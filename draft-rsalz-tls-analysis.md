---
title: A "permanent" Design Group for TLS
docname: draft-rsalz-tls-analysis-latest
submissiontype: IETF
category: bcp
ipr: trust200902
area: SEC
workgroup: tls
keyword: process
stand_alone: yes
smart_quotes: no
pi: [toc, sortrefs, symrefs]

author:
  -
    ins: R. Salz
    name: Rich Salz
    organization: Akamai Technologies
    email: rsalz@akamai.com

venue:
  repo: https://github.com/richsalz/draft-rsalz-tls-analysis

normative:
  WGPROCS: RFC2418
  IESGNOTE:
    title: "One Design Teams"
    date: December, 2001
    url: https://datatracker.ietf.org/doc/statement-iesg-on-design-teams-20011221/

informative:
  TRON:
    title: "TLS 1.3 Ready or Not"
    target: https://www.ndss-symposium.org/ndss2016/tron-workshop-programme/
    date: February, 2016
  NDSS:
    title: "About the Symposium"
    target: https://www.ndss-symposium.org/about
  TAMARIN:
    title: "Tamarin Prover"
    target: https://tamarin-prover.com
  PROVERIF:
    title: "ProVerif: Cryptographic protocol verifier in the formal model"
    target: https://bblanche.gitlabpages.inria.fr/proverif/
  SSLKEYLOGFILE:
    title: "The SSLKEYLOGFILE Format for TLS"
    target: https://datatracker.ietf.org/doc/draft-ietf-tls-keylogfile/
  IRSG:
    title: "Internet Research Steering Group"
    target: https://www.irtf.org/irsg.html
  UFMRG:
    title: "Usable Formal Methods Research Group"
    target: https://datatracker.ietf.org/rg/ufmrg/about/

--- abstract

This memo defines a permanent design team, as defned in
{{WGPROCS}}, for the TLS Working Group.
The team is, repeatedly, chartered to decide whether or not
a draft that has been adopted by the Working Group needs some
kind of analysis in order to determine if the security guarantees
promised for TLS 1.3 are still being met.

--- middle

# Introduction

This memo defines a permanent design team, as defned in
{{WGPROCS}}, for the TLS Working Group (WG).
The team is, repeatedly, chartered to decide whether or not
a draft that has been adopted by the Working Group needs some
kind of analysis in order to determine if the security guarantees
promised for TLS 1.3 are still being met.

This memo defines procedures for how the TLS Working Group will
operate. As such, final publication as an RFC is not required.
Rather, passage through Working Group Last Call (WGLC) is all that
is required to ensure WG consensus. When circumstances change,
the WG Chairs may determine that another WGLC consensus call is needed.

## Terminology

{::boilerplate bcp14info}

# Background

TLS 1.3 benefited greatly from collaboration with many notable
cryptographers during it's development. Unfortunately, {{?RFC8446}} does
not have an explicit acknowledgements section.
In February of 2016,
the "TLS 1.3 Ready or Not" {{TRON}} (TRON) workshop was held,
co-located with the
Network and Distributed system Security {{NDSS}} Symposium held in
San Diego, California.
The first half of the workshop had several papers analyzing the TLS 1.3
protocol, using formal method tools such as Tamarin ({{TAMARIN}}),
ProVerif (({{PROVERIF}}) and classic paper proofs.

Multiple WG consensus calls over the past 18 months or so, have confirmed
that the working group would like to see more formal analysis
of new drafts, to ensure that they do not weaken the guarantees
that are claimed in {{!RFC8336}} and proven in the TRON presentations
and subsequent other analyses.

Anecdotally, it has been relayed to the WG that some of the cryptographers
who would be most relevant to future analysis do not wish to participate
in the day-to-day operations of the working group.
This has been variously presented as a distraction from their "real work,"
and also that the tenor of the communications has been seen as hostile
and unwelcoming.

# Analysis-Needed Design Group (ANDG)

This document proposes that a Design Team, as defined in
Section 6.5 of {{WGPROCS}} and {{IESGNOTE}}, be created.
Unlike other design groups, which are formed to address issues
of a specific WG document, the ANDG will determine, for each
document presented to it, if some type of formal analysis is needed
to verify that the security properties of TLS 1.3 still apply.

For example, adding new types entries into the SSLKEYLOGFILE
{{SSLKEYLOGFILE}} format would likely affect the operational
security of the application using them, it would have no
effect on the security properties of the TLS 1.3 protocol itself.
On the other hand, since a key part of the existing TLS 1.3
analyses centered around the key derivation state machine, a
document that modified that would likely need analysis to show
that the existing invariants still hold.

## Engagement with ANDG

At various points in the lifecycle of a WG document -- adoption,
development, WGLC -- the ANDG would be engaged.
The actual points in the process are left to the discretion of the WG Chairs,
confirmed by WG rough consensus if necessary.

Once engaged, the ANDG will decide amongst themselves a contact
point for the WG Chairs, membership, and document authors.
Any communication from the contact point MUST represent the consensus,
if not full agreement of all involved ANDG participants.

Note that it is not a requirement that the full ANDG participate in
all document reviews. To avoid confusion, the contact point SHOULD
identify those participating each time a decision is
conveyed to the WG.

## ANDG Membership

The current membership of the ANDG must always be available to the WG
members, as well as any outside observers.
This memo recommends that an "Additional resources" link be created on
the DataTracker TLS "about" page, with a link to the document.
The document should be under change control, either as a new Directorate
maintained by the DataTracker, or a simple text file with names and
affiliations maintained in the TLS WG GitHub repository.

Initial membership in the ANDG will be determined by the WG Chairs.
ANDG members can leave at any time by emailing "tls-chairs@ietf.org",
or its equivalent, and letting the Chairs know.

Anyone may propose new members to the ANDG by submitting their name
to the "tls@ietf.org" mailing list. After the Chairs have determined
there are no strong objections, the person is added.

Every member of the ANDG MUST to have a DataTracker account
and profile. They MAY subscribe to the TLS WG mailing list if they
desire.

## ANDG Impact on the WG

As defined in {{WGPROCS}}, a Design Group has no special authority over
the WG decisions.
If the ANDG says that analysis is needed, and no volunteers can be found,
or if the WG disagrees, the document proceeds through its normal course
of develpment.
When or if mentioned in a Shepherd's write-up, the Document Shepherd MAY
point out that the ANDG suggested analysis.

# Relationship to UFMRG

In general, the IETF Community is also increasingly interested in formal
methods to verify its protocols and data structures.
The Internet Research Steering Group {{IRSG}} (IRSG) recently created
Usable Formal Methods Research Group {{UFMRG}} (UFMRG) to look at how
the IETF can leverage formal methods to improve the documents it
generates.

This document proposes that there SHOULD be a natural collaboration,
albeit not a formal one, between UFMRG and ANDG.

--- back

# Acknowledgements
{:numbered="false"}

This draft would have neither been necessary nor possible without
the initial attempts of the TLS WG Chairs to create a Formal
Analysis Triage Team (FATT) which did not fit well into the IETF
policies and procedures.
