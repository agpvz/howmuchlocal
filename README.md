# howmuchlocal

Local anaesthetic toxicity calculator for the bedside.

**Live**: [howmuchlocal.amnestic.co.za](https://howmuchlocal.amnestic.co.za)

A single-file HTML/CSS/JS tool that answers the high-acuity question: *given what's already gone into the patient, how much local anaesthetic is left across all amide agents?*

## What it does

- Tap a weight chip (or enter custom kg).
- Log each LA dose already given as drug + concentration + volume.
- Read off, for each amide agent, how many milligrams of headroom remain — and what that translates to in mL at the most clinically relevant concentrations.
- A cumulative load meter shows where the patient sits relative to the 80% safety cap.
- A persistent LAST rescue button opens the ASRA 2020 lipid emulsion checklist with bolus and infusion volumes pre-calculated for the entered weight.

State persists in `localStorage` — close the tab, reopen, the case is still there.

## Method

Additive fractional toxicity model: ∑(dose ÷ max dose) ≤ 1.

Conservative adult mg/kg maxima (plain solutions, lean body weight):

| Agent | mg/kg |
| --- | --- |
| Lignocaine | 4.5 |
| Bupivacaine | 2.0 |
| Ropivacaine | 3.0 |
| Levobupivacaine | 2.0 |

Safety cap defaults to 80% of theoretical maximum — this is a conscious tightening relative to package-insert maxima to absorb the multifactorial reductions Rosenberg et al describe (elderly, hepatic/cardiac dysfunction, acidosis, fascial-plane block kinetics, repeated dosing, concomitant IV lignocaine).

## References

- Rosenberg PH, Veering BT, Urmey WF. Maximum recommended doses of local anesthetics: a multifactorial concept. *Reg Anesth Pain Med* 2004;29(6):564–75. [PMID 15635516](https://pubmed.ncbi.nlm.nih.gov/15635516/)
- Neal JM, Neal EJ, Weinberg GL. ASRA Local Anesthetic Systemic Toxicity checklist: 2020 version. *Reg Anesth Pain Med* 2021;46(1):81–82. [PMID 33148630](https://pubmed.ncbi.nlm.nih.gov/33148630/)
- Neal JM, Barrington MJ, Fettiplace MR, et al. Third ASRA Practice Advisory on LAST: Executive Summary 2017. *Reg Anesth Pain Med* 2018;43(2):113–23. [PMID 29356773](https://pubmed.ncbi.nlm.nih.gov/29356773/)
- Association of Anaesthetists. [Management of Severe Local Anaesthetic Toxicity, 2023 update (QRH 3-10)](https://anaesthetists.org/Home/Resources-publications/Guidelines/Management-of-severe-local-anaesthetic-toxicity-2023).
- El-Boghdadly K, Pawa A, Chin KJ. Local anesthetic systemic toxicity: current perspectives. *Local Reg Anesth* 2018;11:35–44.

## Disclaimer

This is a bedside aid for trained anaesthetists. It is not a substitute for clinical judgement. The maxima used are conservative consensus values; many factors (age, frailty, hepatic/cardiac disease, pregnancy, acidosis, hypoalbuminaemia, fascial plane blocks, repeated blocks, concomitant IV lignocaine infusion, vascular injection sites) warrant further dose reduction. Always have 20% lipid emulsion and the ASRA LAST checklist immediately accessible when administering local anaesthetic.

## Deploy

Single file, no build step.

```bash
npx wrangler pages deploy . --project-name=howmuchlocal
```

## Author

**Dr AGP van Zyl** — Specialist Anaesthesiologist.

## Licence

MIT. See [LICENSE](LICENSE).
