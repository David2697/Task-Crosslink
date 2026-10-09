# Task-Crosslink

`crosslink_accessions.ipynb` : attribue les accessions UniProt (A et B) aux peptides crosslinkés
d'un export XlinkX / Proteome Discoverer, via le service **UniProt Peptide Search**
(correspondance exacte, Leu = Ile, limitée à *Phaeodactylum tricornutum* par défaut).

## Utilisation
1. `pip install pandas requests openpyxl tqdm`
2. Ouvrir le notebook dans Jupyter, régler `INPUT_CSV` (et `TAX_IDS` si un autre organisme).
3. Exécuter toutes les cellules → `Crosslink_with_accessions.csv` et `.xlsx`
   (feuilles *Crosslinks*, *Peptides*, *Non trouvés*).

Colonnes ajoutées pour A et B : `Accession`, `Gene`, `Protein`, `Reviewed`, `Position match`,
`N matches`, `All accessions`, `Peptide start`, plus `Link type` (intra / inter / ambigu) et `Organism`.
