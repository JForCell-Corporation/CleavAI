# Lab

## MEROPS database

> Neil D Rawlings, Alan J Barrett, Paul D Thomas, Xiaosong Huang, Alex Bateman, Robert D Finn, The MEROPS database of proteolytic enzymes, their substrates and inhibitors in 2017 and a comparison with peptidases in the PANTHER database, Nucleic Acids Research, Volume 46, Issue D1, 4 January 2018, Pages D624–D632, https://doi.org/10.1093/nar/gkx1134

Provided files:

-   MEROPS database release 12.4: all SQL statements including cleavage and substrate.

### Tables

#### `cleavage`
|Field|Type|Null|Key|Default|Extra|
|-----|----|----|---|-------|-----|
|code|varchar(45)|NO|PRI| | |
|uniprot_acc|varchar(45)|NO|PRI| | |
|p1|int|NO|PRI|0| |
|cleavage_evidence|enum('experimental','theoretical')|NO| |experimental| |
|cleavage_type|enum('physiological','non-physiological','pathological','synthetic')|NO| |physiological| |
|cleavage_notes|text|YES| |NULL| |
|cleavage_ontology|varchar(4)|YES| |NULL| |
|cleavage_location|varchar(3)|YES| |NULL| |
|residue_range|varchar(45)|YES| |NULL| |
|cutdb|varchar(45)|YES| |NULL| |
|Ref|varchar(55)|YES| |NULL| |
|peptide_identification|varchar(2)|YES| |NULL| |
|peptidase_identification|varchar(2)|YES| |NULL| |
|mernum|varchar(10)|YES| |NULL| |

#### `substrate`

|Field|Type|Null|Key|Default|Extra|
|-----|----|----|---|-------|-----|
|uniprot_acc|varchar(45)|NO|PRI|0| |
|sequence|mediumtext|NO| |NULL| |
|checksum|varchar(45)|NO| | | |
|uniprot_desc|text|YES| |NULL| |
|taxonomy_id|int unsigned|YES| |NULL| |
|md5|varchar(45)|YES| |NULL| |

### Furin MEROPS ID(mernum)

Using:
```sql
WHERE s.uniprot_desc LIKE '%furin%';
```

Found:
```plaintext
MER0000375
MER0000381
MER0000377
MER0000383
MER0002984
MER0002578
MER0000964
MER0004695
```

