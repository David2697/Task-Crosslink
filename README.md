# Task-Crosslink

`crosslink_accessions.ipynb` : attribue les accessions UniProt (A et B) aux peptides crosslinkés
d'un export XlinkX / Proteome Discoverer, sans connaître l'organisme au départ :

1. l'organisme est déduit des peptides les plus longs, recherchés dans tout UniProtKB
   (**UniProt Peptide Search**), puis son protéome de référence est sélectionné ;
2. tous les peptides sont recherchés dans cet organisme (correspondance exacte, Leu = Ile) ;
3. chaque crosslink reçoit une accession principale (position `Leading Protein Position`,
   puis Swiss-Prot) et la liste complète des correspondances ;
4. dernière section : les 3 crosslinks inter-protéines les plus abondants (XlinkX Score > 40).

## Utilisation
1. `pip install pandas requests openpyxl tqdm`
2. Ouvrir le notebook dans Jupyter et régler `INPUT_CSV`.
3. Exécuter toutes les cellules → `Crosslink_with_accessions.csv` et `.xlsx`
   (feuilles *Crosslinks*, *Peptides*, *Non trouvés*).

Accès réseau requis : `peptidesearch.uniprot.org` et `rest.uniprot.org`.
