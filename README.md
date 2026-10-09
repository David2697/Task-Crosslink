# Task-Crosslink

`crosslink_accessions.ipynb` : attribue les accessions UniProt (A et B) aux peptides crosslinkés
d'un export XlinkX / Proteome Discoverer, sans connaître l'organisme au départ :

1. l'organisme est déduit des peptides les plus longs, recherchés dans tout UniProtKB
   (**UniProt Peptide Search**), puis son protéome de référence est sélectionné ;
2. tous les peptides sont recherchés dans cet organisme (correspondance exacte, Leu = Ile) ;
3. le protéome de référence est figé dans un FASTA nommé avec sa release UniProt
   (`reference_proteome_<UP>_<release>.fasta`), réutilisable via `PROTEOME_FASTA` ;
4. chaque peptide n'est attribué qu'aux protéines où `début + Crosslinker Position − 1`
   = `Leading Protein Position` ; s'il en reste plusieurs, l'accession est signalée ambiguë ;
5. dernière section : les 3 crosslinks inter-protéines les plus abondants (XlinkX Score > 40).

## Utilisation
1. `pip install pandas requests openpyxl tqdm`
2. Placer `Crosslink Data Anonymized 2.2.csv` à côté du notebook (ou régler `INPUT_CSV`).
3. `Kernel → Restart Kernel and Run All Cells`, puis enregistrer le notebook avec ses sorties → `Crosslink_with_accessions.csv` et `.xlsx`
   (feuilles *Crosslinks*, *Peptides*, *Non trouvés*).

Accès réseau requis : `peptidesearch.uniprot.org` et `rest.uniprot.org`.
