# Carbon Black Upsell Helper — Design Document

## Carbon Black Cloud Bundles

One Endpoint bundle and one Workloads bundle may be selected simultaneously. Only one bundle per family (Endpoint or Workloads) can be active at a time.

| Bundle | Included Products |
|--------|------------------|
| Endpoint Foundations | Carbon Black Cloud NGAV (Analytics), Basic Behavioral EDR |
| Endpoint Advanced | Everything in Foundations + Live Query, Vulnerability Management |
| Endpoint Enterprise | Everything in Advanced + Enterprise EDR |

---

## Carbon Black Cloud Workloads Bundles
| Bundle | Included Products |
|--------|------------------|
| Workloads Foundations | vCenter Plug-in, AWS Account onboarding, Lifecycle Management, Asset Inventory, Vulnerability Management, Live Query | Visibilty into operations hygene, prioritized vulnerabilities, and real-time query capability
| Workloads Advanced | Everything in Foundations + NGAV | Adds the ability to block malware
| Workloads Enterprise | Everything in Advanced + Enterprise EDR | Adds continious event capture, threat hunting, threat intelligence and custom detections


## Carbon Black Cloud Individual Products

These can be selected standalone or as add-ons. Some are already included in bundles (noted).

| Product | In Bundle? | Notes |
|---------|-----------|-------|
| Host-Based Firewall | None | Manages Windows firewall |
| Enterprise EDR | Endpoint Enterprise, Workloads Enterprise | Advanced threat hunting, continuous event capture |
| Live Query (Audit & Remediation) | Endpoint Advanced+, Workloads Foundations+ | Real-time query across endpoints |
| Endpoint Network Detection and Response (eNDR/XDR) | None | Add-on requiring Enterprise EDR |

---

## Carbon Black On-Premises Products

These are independent of cloud bundles and can be selected alongside any cloud products.

| Product | Notes |
|---------|-------|
| Carbon Black Response | On-premises EDR |
| App Control | Application Control for fixed fuctions devices, POS, legacy OSs

---

## Customer Profile Inputs

Beyond product selection, capture:
- **Cloud Posture**: Cloud Friendly | Cloud Adverse
- *(Future)* Symantec products (TBD)

---

## Clarifying Questions

After the rep checks the customer's current products, follow-up questions appear dynamically based on what was selected. Each question is only shown when its trigger condition is met. Answers drive the upsell recommendations below.

| # | Question | Trigger (show when…) | If Yes → Suggest | Reason |
|---|----------|----------------------|-----------------|--------|
| 1 | Does the customer need to protect fixed function devices, POS systems, or legacy operating systems? | Cloud Friendly AND any Endpoint OR Workloads bundle selected AND App Control NOT already selected | App Control | App Control is purpose-built for locked-down, or legacy environments where standard EDR cannot be deployed |
| 2 | Does the customer want additional network telemetry such as HTTP/TLS headers, JA3/JA3S fingerprints, Community IDs, protocol identification, and bytes sent/received? | Cloud Friendly AND Enterprise EDR selected (standalone, via Endpoint bundle, or via Workloads Enterprise) AND eNDR NOT already selected | Endpoint Network Detection & Response (eNDR) | eNDR extends EEDR with deep network visibility — session-level telemetry that endpoint-only sensors cannot capture |
| 3 | Is the customer concerned about compliance audits, M&A due diligence, or helpdesk/IT operations visibility? | Cloud Friendly AND Endpoint Foundations selected AND neither Live Query nor Endpoint Advanced/Enterprise selected | Live Query (add-on) or upgrade to Endpoint Advanced | Live Query enables real-time SQL-like queries across all endpoints — essential for point-in-time compliance evidence, inventory sweeps during M&A, and rapid helpdesk investigation |
| 4 | Does the customer want to centrally manage and control the Windows host-based firewall across their endpoints or Windows-based workloads? | Cloud Friendly AND (any Endpoint or Workloads bundle selected OR App Control selected) AND Host-Based Firewall NOT already selected | Host-Based Firewall | Host-Based Firewall lets security teams define and enforce Windows firewall rules fleet-wide from the Carbon Black Cloud console |
| 5 | Does the customer want visibility into vulnerabilities across their endpoints — CVEs, patch status, risk prioritization? | Cloud Friendly AND Endpoint Foundations selected AND neither Endpoint Advanced nor Endpoint Enterprise selected | Endpoint Advanced or Endpoint Enterprise | Vulnerability Management is included in Endpoint Advanced+ — upgrading the bundle is typically more cost-effective than adding a standalone VM tool |
| 6 | Does the customer want greater visibility into endpoint activity, better threat hunting capabilities, and the ability to write custom detections? | Cloud Friendly AND (Endpoint Foundations OR Endpoint Advanced) selected AND Endpoint Enterprise NOT selected AND no Workloads bundle also needing upgrade (Q17 handles that case) | Endpoint Enterprise | Endpoint Enterprise adds Enterprise EDR — continuous event capture, full process tree visibility, threat intelligence feeds, and custom detection rules not available in lower tiers |
| 7 | Does the customer want to detect and prevent malware from executing on their cloud workloads and VMs — not just visibility? | Cloud Friendly AND Workloads Foundations selected AND neither Workloads Advanced nor Workloads Enterprise selected | Workloads Advanced | Workloads Foundations provides hygiene and visibility only — Workloads Advanced adds NGAV to actively block malware on cloud workloads |
| 8 | Does the customer want continuous event capture, threat hunting, threat intelligence feeds, and custom detections on their cloud workloads and VMs? | Cloud Friendly AND (Workloads Foundations OR Workloads Advanced) selected AND Workloads Enterprise NOT selected AND no Endpoint bundle also needing upgrade (Q17 handles that case) | Workloads Enterprise | Workloads Enterprise adds Enterprise EDR to the workloads stack — the same deep visibility and hunting capabilities available for endpoints, applied to cloud workloads |
| 9 | Does the customer want a more robust threat hunting platform with deeper visibility into endpoint activity and attacker behavior? | Cloud Adverse AND Carbon Black App Control selected AND Carbon Black Response NOT already selected | Carbon Black Response (EDR) | App Control excels at prevention but has limited detection depth — Carbon Black Response adds full EDR with process tree visibility, attack chain reconstruction, and threat hunting |
| 10 | Does the customer want more robust blocking and prevention to complement their threat hunting capability? | Cloud Adverse AND Carbon Black Response selected AND Carbon Black App Control NOT already selected | Carbon Black App Control | Carbon Black Response provides excellent detection but relies on behavioral blocking — App Control adds application whitelisting to prevent unauthorized software from executing at all |
| 11 | Is the customer looking to modernize their on-prem EDR to a cloud-delivered solution? | Cloud Friendly AND Carbon Black Response selected | Enterprise EDR (Cloud) | Enterprise EDR delivers the same capabilities cloud-natively with no on-prem infrastructure to manage. Once migrated, all other cloud-friendly questions apply based on the customer's needs |
| 12 | Does the customer use VMware vCenter, or need cloud workload lifecycle management, asset inventory, AWS account onboarding, prioritized vulnerabilities, or real-time query? | Cloud Friendly AND (any Endpoint bundle selected OR App Control selected) AND no Workloads bundle selected | Workloads Foundations | Workloads Foundations includes the vCenter Plugin and cloud workload management capabilities that Endpoint bundles do not provide — if the customer manages VMs or cloud workloads, the Workloads bundle is the right fit |
| 13 | Does the customer want NGAV, Live Query, and Vulnerability Management alongside their Enterprise EDR — bundled at a better price point than purchasing each standalone? | Cloud Friendly AND Enterprise EDR selected as standalone AND Endpoint Enterprise NOT already selected | Endpoint Enterprise | Customers with standalone EEDR are likely paying more for less — Endpoint Enterprise bundles NGAV, Live Query, and Vulnerability Management together with EEDR |
| 14 | Are the customer's workloads primarily VM or cloud-based rather than traditional endpoints? | Cloud Friendly AND Enterprise EDR selected as standalone AND Workloads Enterprise NOT already selected | Workloads Enterprise | Workloads Enterprise packages Enterprise EDR with vCenter integration, lifecycle management, and AWS onboarding — a better fit than standalone EEDR for VM-heavy or cloud-native environments |
| 15 | Does the customer need real-time query capabilities for compliance audits, M&A due diligence, or IT operations visibility? | Cloud Friendly AND App Control selected AND no bundle selected AND Live Query NOT already selected | Live Query (add-on) | Live Query enables real-time SQL-like queries across all endpoints — essential for point-in-time compliance evidence, inventory sweeps during M&A, and rapid helpdesk investigation |
| 16 | Does the customer want cloud-delivered threat hunting, continuous event capture, and visibility into endpoint activity alongside their App Control deployment? | Cloud Friendly AND App Control selected AND Enterprise EDR NOT already selected (standalone or via bundle) | Enterprise EDR | Enterprise EDR complements App Control's prevention-first approach with deep detection capability — continuous event capture, process tree visibility, threat intelligence, and custom detections delivered from the cloud |
| 17 | Does the customer want greater visibility into activity across both their endpoints and cloud workloads, better threat hunting capabilities, and the ability to write custom detections? | Cloud Friendly AND (Endpoint Foundations OR Endpoint Advanced) selected AND Endpoint Enterprise NOT selected AND (Workloads Foundations OR Workloads Advanced) selected AND Workloads Enterprise NOT selected | Endpoint Enterprise + Workloads Enterprise | One question covers both families when both need upgrading — Endpoint Enterprise for endpoints and Workloads Enterprise for cloud workloads, recommended together for consistency |

**Combination rule:** If both Workloads Foundations (Q12) and Enterprise EDR (Q16) are recommended in the same session, consolidate to **Workloads Enterprise** — it covers both requirements in a single bundle.

**Workloads tier-matching rule:** When Workloads Foundations is recommended and the customer already has an Endpoint bundle, upgrade to the matching Workloads tier for consistent protection across endpoints and workloads:
- Endpoint Foundations → minimum Workloads Advanced (adds NGAV for parity)
- Endpoint Advanced → Workloads Advanced
- Endpoint Enterprise → Workloads Enterprise

**Supersede rules** (higher-tier recommendation removes redundant lower-tier ones):
- Endpoint Enterprise → removes: Endpoint Advanced or Endpoint Enterprise, Live Query (add-on or upgrade), Live Query (add-on)
- Endpoint Advanced or Endpoint Enterprise → removes: Live Query (add-on or upgrade), Live Query (add-on)
- Workloads Enterprise → removes: Workloads Advanced, Workloads Foundations, Live Query (add-on), Live Query (add-on or upgrade)
- Workloads Advanced → removes: Workloads Foundations, Live Query (add-on)
- Workloads Foundations → removes: Live Query (add-on) *(Live Query is included in all Workloads tiers)*

> Add more rows here as upsell rules are identified.

---

## Upsell Decision Logic

Rules that fire automatically from product selections alone (no clarifying question needed):

> TODO: Define rules based on rep walkthrough.
>
> Structure: IF [customer has X] AND [customer lacks Y] AND [cloud posture is Z] THEN [suggest W, because reason].
>
> Example rules (placeholders):
> - IF has `Carbon Black Response` (on-prem) AND cloud-friendly → suggest migrating to `Endpoint Advanced`
> - IF has `Endpoint Foundations` AND lacks `Enterprise EDR` → suggest upgrading to `Endpoint Advanced`

---

## UI Flow Notes

1. Rep selects cloud posture (Cloud Friendly / Cloud Adverse)
2. Rep selects customer's current products: choose a bundle OR individual products (mutually exclusive), plus any on-prem products
3. Tool displays upsell opportunities with reasoning
4. Output is a standalone HTML file (no server, no build step)
