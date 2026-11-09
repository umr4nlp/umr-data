# Acknowledgments

The creators of the Czech UMRs wish to express their gratitude to
Federica Gamba, Zdeňka Urešová and the SynSemClass team, and Marie Mikulová and the PDT-C team.

The largest part of the Czech UMRs is an automatic conversion from the Prague Dependency Treebank
– Consolidated ([PDT-C](https://ufal.mff.cuni.cz/pdt-c)), version 2.0 (http://hdl.handle.net/11234/1-5813).
In addition, manual UMR annotation is provided for some of the PDT-C files, and also for other texts
(Parallel Universal Dependencies, PUD).

The conversion covers selected phenomena pertaining to the sentence level annotation (esp. structure
of the graph, nodes and relations labeling, and PropBank-like argument structure for verbs). Further,
coreference relations are identified, both intra- and inter-sentential. More detailed release notes
are on [the project webpage](https://ufal.mff.cuni.cz/uniform-meaning-representation-czech).

The work on the Czech UMR has been supported by the following grants and projects:
UMR, Project No. LUAUS23283 (MŠMT ČR), LUSyD, Project No. GX20-16819X (GAČR),
and LINDAT/CLARIAH-CZ, Project No. LM2023062 (MŠMT ČR).



# Changes from UMR 2.2 to UMR 3.0

For 10 manually annotated non-PUD files, the following updates were made:
- The :wiki attribute was added to specify the Wikidata identifier for each node with an outgoing :name relation (if no such identifier exists, "Wiki-unknown" is used).
- Events that are overtly expressed as deverbal nouns are newly represented using verbal concepts with numbered :ARG roles (Stage 1).
- As a case study for Czech, the annotation of 1 file (etest/ln94211_89.umr) was enriched with temporal relations.



# Changes from UMR 2.0 to UMR 2.2

Added 100 sentences from Czech PUD (part of the Parallel UD dataset from Universal Dependencies).
This is manual Stage 0 annotation.

Added manual annotation for 10 PDT-C files (or their parts). Unlike PUD, annotation of these files
aims at roughly the same annotation aspects as the automatic conversion: predicates use numbered
:ARG roles (Stage 1) but modal annotation stays in sentence-level graphs. Document-level relations
cover coreference only; there are no temporal relations.

The following table shows how many sentences of each file have been annotated manually.

```
| original                      | conv file | man file | # of sentences | manually |
+-------------------------------+-----------+----------+----------------+----------|
| dtest/ln94210_111.umr         |      1544 |     7091 |             14 |       14 |
| dtest/ln95046_093.umr         |      2024 |     7092 |             11 |       11 |
| dtest/pdtsc_093_3.02.umr      |      4145 |     7093 |             50 |     ! 25 |
| dtest/pdtsc_146_2.05.umr      |      4748 |     7094 |             50 |     ! 25 |
| dtest/wsj0013.cz.umr          |      4787 |     7095 |             18 |       18 |
| dtest/wsj0072.cz.umr          |      4846 |     7096 |             19 |     ! 10 |
| etest/ln94205_73.umr          |      0955 |     7097 |             28 |       28 |
| etest/ln94211_89.umr          |      1795 |     7098 |             43 |       43 |
| etest/pdtsc_038_1.00.umr      |      3495 |     7099 |             50 |     ! 25 |
| etest/wsj2350.cz.umr          |      6982 |     7100 |             24 |       24 |
```



# First release in UMR 2.0

The Czech UMRs are automatically converted from the Prague Dependency Treebank – Consolidated
([PDT-C](https://ufal.mff.cuni.cz/pdt-c)), version 2.0 (http://hdl.handle.net/11234/1-5813).

The conversion covers selected phenomena pertaining to the sentence level annotation
(esp. structure of the graph, nodes and relations labeling, and PropBank-like argument structure for verbs).
Further, coreference relations are identified, both intra- and inter-sentential. More detailed
release notes are on [the project webpage](https://ufal.mff.cuni.cz/uniform-meaning-representation-czech).



<pre>
=== Machine-readable metadata (DO NOT REMOVE!) ================================
License: CC BY-NC-SA 4.0
Contributors: Markéta Lopatková, Hana Hledíková, Jan Štěpánek, Daniel Zeman, Eva Fučíková, Michal Novák, Šárka Zikánová, Eva Hajičová, Jiří Havelka, Veronika Kolářová, Lucie Kučová, Marie Mikulová, Jiří Mírovský, Anna Nedoluzhko, Jarmila Panevová, Petr Pajas, Petr Sgall, Magda Ševčíková, Zdeňka Urešová, Zdeněk Žabokrtský, Jan Hajič
Contact: lopatkova@ufal.mff.cuni.cz
===============================================================================
</pre>
