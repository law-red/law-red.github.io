---
title: "In Scope. But Also Authorized?"
description: "Why a signed Permission-to-Attack can still leave you without permission"
date: 2026-11-22 00:00:00 +0100
categories: [Security, Penetration Testing]
tags: [pentesting, authorization, scope, cloud, legal, gdpr]
image:
  path: /assets/img/posts/in-scope-but-also-authorized/cover.webp
  alt: "Dallas County Courthouse in Adel, Iowa"
---

## §1 When the Target Isn’t Yours

A tester commences a commissioned attack on a client's web application. The Permission-to-Attack is executed, the target is on the list. Within minutes, it turns out that the application doesn't run on the client's own infrastructure at all. It operates inside a cloud provider's environment, on servers the client does not own, sharing hardware with other tenants. On paper, everything was "in scope." Yet part of what the client authorized was never within the client's authority to authorize.

That is the question a target list does not answer. It states what should be tested and stays silent on who may permit each individual test action.

## §2 Scope ≠ Authority

Authorization for a security assessment is a private contract. It binds only the two signing parties, the client and the testing provider. Criminal law applies whether or not they have agreed. "Authorized" in that document means contractually authorized. Legal authorization is a distinct category. It means the access is actually lawful, because the party consenting had the power to consent, and no law is breached independently of that consent.

For the bare act of access, the rule is simple. If the party entitled to control the system consents, the access is authorized. A target list does not establish this on its own. You still have to check who controls each target.

## §3 The Authority Gap

A permission is only worth as much as the authority of the person granting it. Most scope documents fall apart at exactly this point. An organization cannot authorize access to a system it does not itself control, and modern operations contain far more such systems than the scoping call suggests: cloud infrastructure, SaaS services, outsourced IT arrangements, subsidiary entities, shared platforms.

This is clearest in the cloud context. Where the client controls their data but the provider controls the servers, valid access may require permission from both authorities; consent from one side alone is insufficient. The major cloud providers draw the same line in their testing rules: a customer may test their own resources, but not the provider's infrastructure or other tenants' environments. However generously the client formulates the scope, it cannot extend beyond the edge of what the client actually controls.

Then there is the dynamic problem. Authorization has to hold up for as long as the test runs. While it does, the factual ground shifts: IP addresses change hands, DNS records redirect, a credential works on a system nobody listed. The decisive question at that moment is not "can I reach it?" but "may I?" Being technically capable of reaching that to which one was never authorized is precisely not authorization.

How grave this matter becomes was demonstrated in a widely reported case from Iowa, in which testers engaged to probe courthouse security were arrested in the middle of the night despite holding signed authorization. It remained unclear whether the signatory had the authority to permit entry to buildings owned by individual counties. The case involved physical trespass rather than computer access. The testers later sued the county, which settled in January 2026 for $600,000.[^ars] No court ever ruled on who could authorize what. The case therefore sets no precedent. It does show however, what a signed authorization is worth when the other side does not accept the signer’s authority.

## §4 A Working Checklist

This checklist is a working aid. It makes assumptions and missing permissions visible before testing starts, and it offers no legal guarantee. Each row is there to surface the one box that is still open.

| System/Tenant | Test action | Authorizing party | Evidence & conditions | Data handling | Stop / escalation |
|---|---|---|---|---|---|
| (fictional) Client CRM, hosted at SaaS provider X | Auth bypass, access to customer records | Client and provider X; client alone is insufficient | Written test approval from X on file? no → open | Synthetic/test records only; real customer data off-limits | Upon encountering data outside the client's own tenant: cease immediately, escalate to project lead |

## §5 Three Questions Before Sign-Off

For a security or project lead, three questions must be answerable before sign-off:

1. What evidence does the authorization decision require? Who controls each target, and is it documented?
2. Who resolves missing or unclear authority before testing starts, not after?
3. When does testing pause? What event triggers a stop, and who handles escalation?

Resolving this beforehand saves rework and spares you from discovering mid-engagement that part of the target never had defensible authorization.

## §6 Data Protection

A separate body of law is touched only briefly and deserves its own treatment. At the moment a test encounters personal data, data-protection obligations attach regardless of scope, because they follow the data itself. The Court of Justice of the European Union has confirmed that using personal data for testing purposes constitutes “processing” unless the data has been anonymized or is fictitious, and that the commissioning organization may be answerable as controller for processing carried out by its provider where it occurs within the framework the organization established (CJEU, C-683/21, *Nacionalinis visuomenės sveikatos centras*, 5 December 2023).[^cjeu] That is why the checklist allows synthetic test records only. A scope document cannot extinguish these obligations.

## §7 Close

Authorization, then, is a governance decision, and it belongs to the commissioning organization. The scope document is less a shield than an inventory of what you are answerable for.

Exceeding the agreed scope on the client’s own systems is a less clear-cut criminal question than intuition suggests. In most jurisdictions, these offenses require intent, and a tester who honestly believes a system is covered may lack it. The real risk lies where someone signs a permission they never had the authority to grant.

---

_This article is for informational purposes only and does not constitute legal advice._

[^ars]: <https://arstechnica.com/security/2026/01/county-pays-600000-to-pentesters-it-arrested-for-assessing-courthouse-security/>
[^cjeu]: *(CJEU, Case C-683/21, Nacionalinis visuomenės sveikatos centras, ECLI:EU:C:2023:949, 5 December 2023)*
