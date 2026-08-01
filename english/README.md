# Changes from UMR 2.0 to UMR 3.0

The following additional conversions were applied for the 3.0 release:

| Original 2.0 Structure | UMR 3.0 Structure | Change Type | Number of Occurrences |
|---|---|---|:---:|
| amr-unknown | umr-unknown | deterministic | 839 |
| amr-choice | umr-choice | deterministic | 130 |
| (questions missing `:mode`) | `:mode interrogative` added | deterministic | 1,615 |
| possible-01 | `:modal-strength neutral-affirmative` | deterministic | — |
| recommend-01 | `:modal-strength neutral-affirmative` | deterministic | — |
| permit-01 | `:modal-strength neutral-affirmative` | deterministic | — |
| likely-01 | `:modal-strength partial-affirmative` | deterministic | — |
| obligate-01 | `:modal-strength partial-affirmative` | deterministic | 1,477 total |
| `:domain` | have-configuration-91 | manual | 238 |
| `:domain` | have-role-91 | manual | 195 |
| `:domain` | identity-91 | manual | 280 |
| AMR pronoun concepts (i, you, he, she, it, we, they) | `person` + `:refer-person 1st/2nd/3rd` | deterministic | 8,758 |
| AMR indefinite pronouns (somebody, anyone, nothing, etc.) | UMR person/thing equivalents + `:refer-person`/`:refer-number` | deterministic | — |
| Ambiguous pronoun referents | `person` + `:refer-person` (LLM-assisted disambiguation) | LLM-assisted | 3,226 of 3,295 decisions |

**Pronoun conversion detail:**

| Attribute | Occurrences |
|-----------|------------:|
| `:refer-person 1st` | 2,512 |
| `:refer-person 2nd` | 3,827 |
| `:refer-person 3rd` | 2,301 |
| `:refer-number plural` | 3,756 |
| `:refer-number singular` | 7,377 |

# Acknowledgments

The creators of the English UMRs wish to express their gratitude to Matt Buchholz, Skatje Myers, Alexis Palmer, Martha Palmer, Jin Zhao, Claire Bonial, Tim O’Gorman, Kristin Wright-Bettner, Benét Post, Alvin Chen, Marie MacGregor, Ahmed Elsayed, Carlos Gomez, Loden Havenmeier, and Ath Kilgore for their assistance.


<pre>
=== Machine-readable metadata (DO NOT REMOVE!) ================================
License: CC BY-SA 4.0
Contributors: Julia Bonn, Jens E. Van Gysel, Meagan Vigus
Contact: julia.bonn@colorado.edu
===============================================================================
</pre>