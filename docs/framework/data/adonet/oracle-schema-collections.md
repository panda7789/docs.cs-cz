---
title: Kolekce schémat Oracle
ms.date: 03/30/2017
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
ms.openlocfilehash: cb91a90ae7323283556954caa401646a2063a37e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783293"
---
# <a name="oracle-schema-collections"></a>Kolekce schémat Oracle

Microsoft .NET Framework Zprostředkovatel dat for Oracle podporuje kromě běžných kolekcí schémat následující konkrétní kolekce schémat:

- Sloupce

- Indexy

- IndexColumns

- Procedury

- Sekvence

- Synonyma

- Tabulky

- Uživatelé

- Zobrazení

- Funkce

- Balíčky

- PackageBodies

- Arguments

- UniqueKeys

- PrimaryKeys

- ForeignKeys

- ForeignKeyColumns

- ProcedureParameters

## <a name="columns"></a>Sloupce

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník tabulky, zobrazení nebo clusteru|
|TABLE_NAME|String|Název tabulky, zobrazení nebo clusteru.|
|COLUMN_NAME|String|Název sloupce|
|id|Desetinné číslo|Pořadové číslo sloupce, který se má vytvořit|
|PROGRAMÁTOR|String|Datový typ sloupce|
|ČASOVÝ|Desetinné číslo|Délka sloupce v bajtech|
|ČÍSLIC|Desetinné číslo|Desítková přesnost pro datový typ NUMBER; binární přesnost pro datový typ FLOAT, null pro všechny ostatní datové typy.|
|KAPACITY|Desetinné číslo|Číslice napravo od desetinné čárky v čísle.|
|POVOLENO|String|Určuje, zda sloupec povoluje hodnoty NULL. Hodnota je N, pokud u sloupce existuje omezení NOT NULL, nebo pokud je sloupec částí primárního klíče.|

## <a name="indexes"></a>Indexy

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník indexu|
|INDEX_NAME|String|Název indexu.|
|INDEX_TYPE|String|Typ indexu (normální, RASTRový, normální v závislosti na funkci, RASTRový obrázek založený na funkci nebo doména).|
|TABLE_OWNER|String|Vlastník indexovaného objektu.|
|TABLE_NAME|String|Název indexovaného objektu.|
|TABLE_TYPE|String|Typ indexovaného objektu (například tabulka, CLUSTER).|
|JEDINEČNOST|String|Zda je index jedinečný nebo nejedinečný.|
|KOMPRESE|String|Zda je index povolen nebo zakázán.|
|PREFIX_LENGTH|Desetinné číslo|Počet sloupců v předponě kompresního klíče.|
|TABLESPACE_NAME|String|Název tabulkového prostoru obsahujícího index|
|INI_TRANS|Desetinné číslo|Počáteční počet transakcí|
|MAX_TRANS|Desetinné číslo|Maximální počet transakcí.|
|INITIAL_EXTENT|Desetinné číslo|Velikost počátečního rozsahu.|
|NEXT_EXTENT|Desetinné číslo|Velikost sekundárních rozsahů.|
|MIN_EXTENTS|Desetinné číslo|Minimální počet rozsahů povolených v segmentu.|
|MAX_EXTENTS|Desetinné číslo|V segmentu je povolený maximální počet rozsahů.|
|PCT_INCREASE|Desetinné číslo|Procentuální zvětšení velikosti rozsahu.|
|PCT_THRESHOLD|Desetinné číslo|Prahová hodnota povoleného prostoru blokování na záznam v indexu|
|INCLUDE_COLUMN|Desetinné číslo|ID sloupce posledního sloupce, který má být zahrnut do indexu tabulkově uspořádané tabulky primárního klíče (bez přetečení). Tento sloupec je namapován na sloupec COLUMN_ID v zobrazení * _TAB_COLUMNS data Dictionary.|
|FREELISTS|Desetinné číslo|Počet freelists procesu přidělených tomuto segmentu|
|FREELIST_GROUPS|Desetinné číslo|Počet skupin freelist – přidělených tomuto segmentu|
|PCT_FREE|Desetinné číslo|Minimální procento volného místa v bloku|
|PROTOKOLU|String|Protokolování informací.|
|BLEVEL|Desetinné číslo|B *-úroveň stromu: Hloubka indexu z jeho kořenového bloku k jeho listovým blokům. Hloubka 0 značí, že kořenový blok a blok listu jsou stejné.|
|LEAF_BLOCKS|Desetinné číslo|Počet koncových bloků v indexu|
|DISTINCT_KEYS|Desetinné číslo|Počet jedinečných indexovaných hodnot. U indexů, které vynutily omezení UNIQUE a PRIMARY KEY, je tato hodnota stejná jako počet řádků v tabulce (USER_TABLES. NUM_ROWS).|
|AVG_LEAF_BLOCKS_PER_KEY|Desetinné číslo|Průměrný počet koncových bloků, ve kterých se každá hodnota v indexu zobrazuje Zaokrouhlovaná na nejbližší celé číslo. U indexů, které vynutily omezení JEDINEČNosti a primárního klíče, je tato hodnota vždy 1.|
|AVG_DATA_BLOCKS_PER_KEY|Desetinné číslo|Průměrný počet bloků dat v tabulce, na které odkazují jedinečné hodnoty v indexu, zaokrouhlený na nejbližší celé číslo. Tato statistika je průměrný počet datových bloků obsahujících řádky, které obsahují danou hodnotu pro indexované sloupce.|
|CLUSTERING_FACTOR|Desetinné číslo|Určuje množství pořadí řádků v tabulce založené na hodnotách indexu.|
|STAV|String|Zda je Nerozdělený index platný nebo nepoužitý.|
|NUM_ROWS|Desetinné číslo|Počet řádků v indexu.|
|SAMPLE_SIZE|Desetinné číslo|Velikost vzorku používaného k analýze indexu.|
|LAST_ANALYZED|DateTime|Datum, kdy byl tento index naposledy analyzován.|
|CHÝLENÍ|String|Počet vláken na instanci pro skenování indexu.|
|INSTANCE|String|Počet instancí, ve kterých se mají vyhledávat indexy.|
|DĚLENÉ|String|Určuje, zda je tento index rozdělený na &#124; oddíly (ano ne).|
|POŽADOVANÝCH|String|Určuje, zda je index na dočasné tabulce.|
|DOJDE|String|Určuje, zda je název indexu vygenerován systémem (Y&#124;N).|
|SEKUNDÁRNÍ|String|Určuje, zda je index sekundárním objektem vytvořeným metodou ODCIIndexCreate datové kazety Oracle9i (Y&#124;N).|
|BUFFER_POOL|String|Název výchozího fondu vyrovnávacích pamětí, který se má použít pro bloky indexu|
|USER_STATS|String|Zda byly statistiky zadány přímo uživatelem.|
|ÚKOLU|String|Označuje dobu trvání dočasné tabulky: 1) SYS $ SESSION: řádky se uchovávají po dobu trvání relace, 2) SYS $ TRANSACTION: řádky se odstraní po potvrzení, 3) hodnota null pro trvalou tabulku.|
|PCT_DIRECT_ACCESS|Desetinné číslo|V případě sekundárního indexu v tabulce uspořádané podle indexu je procento řádků s PLATNÝm odhadem.|
|ITYP_OWNER|String|Pro index domény je vlastníkem indextype.|
|ITYP_NAME|String|V případě indexu domény název indextype.|
|UKAZATELŮ|String|Pro index domény parametr řetězec.|
|GLOBAL_STATS|String|U dělených indexů označuje, zda byly statistiky shromážděny analýzou indexu jako celku (Ano) nebo byly odhadnuty od statistik o podkladových oddílech indexu a pododdílech (ne).|
|DOMIDX_STATUS|String|Odráží stav indexu domény. NULL: zadaný index není index domény. PLATNÝ: index je platný index domény. IDXTYP_INVLD: typ indexu tohoto indexu domény je neplatný.|
|DOMIDX_OPSTATUS|String|Odráží stav operace provedené na indexu domény: NULL: zadaný index není index domény. PLATNÉ: operace byla provedena bez chyb. SELHALo: operace selhala s chybou.|
|FUNCIDX_STATUS|String|Určuje stav indexu založeného na funkci: NULL: Toto není index založený na funkci, POVOLENý: index založený na funkci je povolený, ZAKÁZANý: index založený na funkci je zakázaný.|
|JOIN_INDEX|String|Označuje, zda se jedná o index spojení, nebo ne.|

## <a name="indexcolumns"></a>IndexColumns

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|INDEX_OWNER|String|Vlastník indexu|
|INDEX_NAME|String|Název indexu.|
|TABLE_OWNER|String|Vlastník tabulky nebo clusteru|
|TABLE_NAME|String|Název tabulky nebo clusteru|
|COLUMN_NAME|String|Název sloupce nebo atribut sloupce typu objektu|
|COLUMN_POSITION|Desetinné číslo|Pozice sloupce nebo atributu v indexu.|
|COLUMN_LENGTH|Desetinné číslo|Indexovaná délka sloupce|
|CHAR_LENGTH|Desetinné číslo|Maximální délka kódu sloupce.|
|TAHEM|String|Určuje, zda je sloupec seřazen v sestupném pořadí.|

## <a name="procedures"></a>Procedury

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník objektu.|
|OBJECT_NAME|String|Název objektu.|
|SUBOBJECT_NAME|String|Název podobjektu (například partition).|
|OBJECT_ID|Desetinné číslo|Číslo objektu slovníku objektu.|
|DATA_OBJECT_ID|Desetinné číslo|Číslo objektu slovníku segmentu, který obsahuje objekt.|
|LAST_DDL_TIME|DateTime|Časové razítko poslední změny objektu, které vyplývají z příkazu DDL (včetně grantů a odvolaných).|
|TIMESTAMP|String|Časové razítko pro specifikaci objektu (data znaku).|
|STAV|String|Stav objektu (platný, neplatný nebo není k dispozici).|
|POŽADOVANÝCH|String|Zda je objekt dočasný (aktuální relace může zobrazit pouze data, která jsou umístěna v samotném objektu).|
|DOJDE|String|Byl název tohoto objektu systému generovaný? (Y &#124; N).|
|SEKUNDÁRNÍ|String|Určuje, zda se jedná o sekundární objekt vytvořený metodou ODCIIndexCreate datové kazety Oracle9i (Y &#124; N).|
|VYTVÁŘEJÍ|DateTime|Datum, kdy byl objekt vytvořen.|

## <a name="sequences"></a>Sekvence

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|SEQUENCE_OWNER|String|Jméno vlastníka sekvence|
|SEQUENCE_NAME|String|Název sekvence|
|MIN_VALUE|Desetinné číslo|Minimální hodnota sekvence|
|MAX_VALUE|Desetinné číslo|Maximální hodnota sekvence|
|INCREMENT_BY|Desetinné číslo|Hodnota, o kterou se zvýší pořadí|
|CYCLE_FLAG|String|Zalomí sekvenci kolem při dosažení limitu.|
|ORDER_FLAG|String|Jsou čísla posloupnosti vygenerovaná v daném pořadí.|
|CACHE_SIZE|Desetinné číslo|Počet pořadových čísel, která se mají ukládat do mezipaměti|
|LAST_NUMBER|Desetinné číslo|Poslední pořadové číslo zapsané na disk. Pokud sekvence používá ukládání do mezipaměti, je číslo zapsané na disk poslední číslo umístěné v mezipaměti sekvence. Toto číslo může být větší než poslední použité číslo sekvence.|

## <a name="synonyms"></a>Synonyma

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník synonyma|
|SYNONYM_NAME|String|Název synonyma|
|TABLE_OWNER|String|Vlastník objektu, na který odkazuje synonymum|
|TABLE_NAME|String|Název objektu, na který odkazuje synonymum|
|DB_LINK|String|Název odkazovaného odkazu na databázi, pokud existuje.|

## <a name="tables"></a>Tabulky

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník tabulky|
|TABLE_NAME|String|Název tabulky.|
|TEXTOVÝ|String|Typ tabulky|

## <a name="users"></a>Uživatelé

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|NÁZEV|String|Jméno uživatele.|
|id|Desetinné číslo|Číslo ID uživatele|
|CREATEDATE|DateTime|Datum vytvoření uživatele|

## <a name="views"></a>Zobrazení

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník zobrazení|
|VIEW_NAME|String|Název zobrazení|
|TEXT_LENGTH|Desetinné číslo|Délka textu zobrazení|
|TEXT|String|Zobrazit text|
|TYPE_TEXT_LENGTH|Desetinné číslo|Délka klauzule typu zobrazení typu|
|TYP|String|Klauzule Type pro zobrazení typu|
|OID_TEXT_LENGTH|Desetinné číslo|Délka klauzule WITH OID pro zobrazení typu|
|OID_TEXT|String|S klauzulí OID pro zobrazení typu.|
|VIEW_TYPE_OWNER|String|Vlastník typu zobrazení, pokud je zobrazení typu.|
|VIEW_TYPE|String|Typ zobrazení, pokud je zobrazení typu.|
|SUPERVIEW_NAME|String|Název zobrazení|

## <a name="functions"></a>Funkce

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník objektu.|
|OBJECT_NAME|String|Název objektu.|
|SUBOBJECT_NAME|String|Název podobjektu (například partition).|
|OBJECT_ID|Desetinné číslo|Číslo objektu slovníku objektu.|
|DATA_OBJECT_ID|Desetinné číslo|Číslo objektu slovníku segmentu, který obsahuje objekt.|
|OBJECT_TYPE|String|Typ objektu.|
|VYTVÁŘEJÍ|DateTime|Datum, kdy byl objekt vytvořen.|
|LAST_DDL_TIME|DateTime|Časové razítko poslední změny objektu, které vyplývají z příkazu DDL (včetně grantů a odvolaných).|
|TIMESTAMP|String|Časové razítko pro specifikaci objektu (data znaku)|
|STAV|String|Stav objektu (platný, neplatný nebo není k dispozici).|
|POŽADOVANÝCH|String|Zda je objekt dočasný (aktuální relace může zobrazit pouze data, která jsou umístěna v samotném objektu).|
|DOJDE|String|Byl název tohoto objektu systému generovaný? (Y &#124; N).|
|SEKUNDÁRNÍ|String|Určuje, zda se jedná o sekundární objekt vytvořený metodou ODCIIndexCreate datové kazety Oracle9i (Y &#124; N).|

## <a name="packages"></a>Balíčky

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník objektu.|
|OBJECT_NAME|String|Název objektu.|
|SUBOBJECT_NAME|String|Název podobjektu (například partition).|
|OBJECT_ID|Desetinné číslo|Číslo objektu slovníku objektu.|
|DATA_OBJECT_ID|Desetinné číslo|Číslo objektu slovníku segmentu, který obsahuje objekt.|
|LAST_DDL_TIME|DateTime|Časové razítko poslední změny objektu, které vyplývají z příkazu DDL (včetně grantů a odvolaných).|
|TIMESTAMP|String|Časové razítko pro specifikaci objektu (data znaku).|
|STAV|String|Stav objektu (platný, neplatný nebo není k dispozici).|
|POŽADOVANÝCH|String|Zda je objekt dočasný (aktuální relace může zobrazit pouze data, která jsou umístěna v samotném objektu).|
|DOJDE|String|Byl název tohoto objektu systému generovaný? (Y &#124; N).|
|SEKUNDÁRNÍ|String|Určuje, zda se jedná o sekundární objekt vytvořený metodou ODCIIndexCreate datové kazety Oracle9i (Y &#124; N).|
|VYTVÁŘEJÍ|DateTime|Datum, kdy byl objekt vytvořen.|

## <a name="packagebodies"></a>PackageBodies

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník objektu.|
|OBJECT_NAME|String|Název objektu.|
|SUBOBJECT_NAME|String|Název podobjektu (například partition).|
|OBJECT_ID|Desetinné číslo|Číslo objektu slovníku objektu.|
|DATA_OBJECT_ID|Desetinné číslo|Číslo objektu slovníku segmentu, který obsahuje objekt.|
|LAST_DDL_TIME|DateTime|Časové razítko poslední změny objektu, které vyplývají z příkazu DDL (včetně grantů a odvolaných).|
|TIMESTAMP|String|Časové razítko pro specifikaci objektu (data znaku).|
|STAV|String|Stav objektu (platný, neplatný nebo není k dispozici).|
|POŽADOVANÝCH|String|Zda je objekt dočasný (aktuální relace může zobrazit pouze data, která jsou umístěna v samotném objektu).|
|DOJDE|String|Byl název tohoto objektu systému generovaný? (Y &#124; N).|
|SEKUNDÁRNÍ|String|Určuje, zda se jedná o sekundární objekt vytvořený metodou ODCIIndexCreate datové kazety Oracle9i (Y &#124; N).|
|VYTVÁŘEJÍ|DateTime|Datum, kdy byl objekt vytvořen.|

## <a name="arguments"></a>Arguments

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Jméno vlastníka objektu|
|PACKAGE_NAME|String|Název balíčku|
|OBJECT_NAME|String|Název procedury nebo funkce.|
|ARGUMENT_NAME|String|Název argumentu.|
|POZIČNÍ|Desetinné číslo|Pozice v seznamu argumentů nebo hodnota NULL pro návratovou hodnotu funkce.|
|POŘADÍ|Desetinné číslo|Sekvence argumentů včetně všech úrovní vnoření.|
|DEFAULT_VALUE|String|Výchozí hodnota argumentu|
|DEFAULT_LENGTH|Desetinné číslo|Délka výchozí hodnoty pro argument|
|IN_OUT|String|Směr argumentu (v, OUT nebo OUT/OUT).|
|DATA_LENGTH|Desetinné číslo|Délka sloupce v bajtech|
|DATA_PRECISION|Desetinné číslo|Délka v desítkových číslicích (číslo) nebo binárních číslech (FLOAT).|
|DATA_SCALE|Desetinné číslo|Číslice napravo od desetinné čárky v čísle.|
|DATA_TYPE|String|Datový typ argumentu.|

## <a name="uniquekeys"></a>UniqueKeys

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník definice omezení|
|CONSTRAINT_NAME|String|Název definice omezení|
|TABLE_NAME|String|Název přidružený k tabulce (nebo zobrazení) s definicí omezení|
|SEARCH_CONDITION|String|Text podmínky vyhledávání pro omezení check|
|R_OWNER|String|Vlastník tabulky, na kterou odkazuje referenční omezení|
|R_CONSTRAINT_NAME|String|Název jedinečné definice omezení pro odkazovanou tabulku|
|DELETE_RULE|String|Odstraní pravidlo pro referenční omezení (KASKÁDové nebo žádné akce).|
|STAV|String|Stav vynucení omezení (povoleno nebo zakázáno).|
|ODVODITELNÉ|String|Určuje, zda je omezení odloženo.|
|PLATNÝCH|String|Zda všechna data dodržují omezení (OVĚŘENo nebo Neověřeno).|
|DOJDE|String|Určuje, jestli je název omezení vygenerovaný uživatelem nebo systémem.|
|ŠPATNÉ|String|Hodnota Ano značí, že toto omezení určuje nejednoznačný způsob. Aby se předešlo chybám vyplývajícím z této nejednoznačnosti, přepište omezení pomocí funkce TO_DATE se čtyřmi číslicemi.|
|NAMÍSTO|String|Určuje, jestli je povolené omezení vynutilo nebo není vynutilo.|
|LAST_CHANGE|DateTime|Poslední povolení nebo zakázání omezení|
|INDEX_OWNER|String|Jméno uživatele, který je vlastníkem indexu|
|INDEX_NAME|String|Název indexu|

## <a name="primarykeys"></a>PrimaryKeys

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník definice omezení|
|CONSTRAINT_NAME|String|Název definice omezení|
|TABLE_NAME|String|Název přidružený k tabulce (nebo zobrazení) s definicí omezení|
|SEARCH_CONDITION|String|Text podmínky vyhledávání pro omezení check|
|R_OWNER|String|Vlastník tabulky, na kterou odkazuje referenční omezení|
|R_CONSTRAINT_NAME|String|Název jedinečné definice omezení pro odkazovanou tabulku|
|DELETE_RULE|String|Odstraní pravidlo pro referenční omezení (KASKÁDové nebo žádné akce).|
|STAV|String|Stav vynucení omezení (povoleno nebo zakázáno).|
|ODVODITELNÉ|String|Určuje, zda je omezení odloženo.|
|PLATNÝCH|String|Zda všechna data dodržují omezení (OVĚŘENo nebo Neověřeno).|
|DOJDE|String|Určuje, jestli je název omezení vygenerovaný uživatelem nebo systémem.|
|ŠPATNÉ|String|Hodnota Ano značí, že toto omezení určuje nejednoznačný způsob. Aby se předešlo chybám vyplývajícím z této nejednoznačnosti, přepište omezení pomocí funkce TO_DATE se čtyřmi číslicemi.|
|NAMÍSTO|String|Určuje, jestli je povolené omezení vynutilo nebo není vynutilo.|
|LAST_CHANGE|DateTime|Kdy bylo omezení naposledy povoleno nebo zakázáno.|
|INDEX_OWNER|String|Jméno uživatele, jehož index je vlastníkem.|
|INDEX_NAME|String|Název indexu.|

## <a name="foreignkeys"></a>ForeignKeys

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|PRIMARY_KEY_CONSTRAINT_NAME|String|Název definice omezení|
|PRIMARY_KEY_OWNER|String|Vlastník definice omezení|
|PRIMARY_KEY_TABLE_NAME|String|Název přidružený k tabulce (nebo zobrazení) s definicí omezení|
|FOREIGN_KEY_OWNER|String|Vlastník definice omezení|
|FOREIGN_KEY_CONSTRAINT_NAME|String|Název definice omezení|
|FOREIGN_KEY_TABLE_NAME|String|Název přidružený k tabulce (nebo zobrazení) s definicí omezení|
|SEARCH_CONDITION|String|Text podmínky vyhledávání pro omezení check|
|R_OWNER|String|Vlastník tabulky, na kterou odkazuje referenční omezení|
|R_CONSTRAINT_NAME|String|Název jedinečné definice omezení pro odkazovanou tabulku|
|DELETE_RULE|String|Odstraní pravidlo pro referenční omezení (KASKÁDové nebo žádné akce).|
|STAV|String|Stav vynucení omezení (povoleno nebo zakázáno).|
|PLATNÝCH|String|Zda všechna data dodržují omezení (OVĚŘENo nebo Neověřeno).|
|DOJDE|String|Určuje, jestli je název omezení vygenerovaný uživatelem nebo systémem.|
|NAMÍSTO|String|Určuje, jestli je povolené omezení vynutilo nebo není vynutilo.|
|LAST_CHANGE|DateTime|Kdy bylo omezení naposledy povoleno nebo zakázáno.|
|INDEX_OWNER|String|Jméno uživatele, jehož index je vlastníkem.|
|INDEX_NAME|String|Název indexu.|

## <a name="foreignkeycolumns"></a>ForeignKeyColumns

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník definice omezení|
|CONSTRAINT_NAME|String|Název definice omezení|
|TABLE_NAME|String|Název tabulky s definicí omezení|
|COLUMN_NAME|String|Název sloupce nebo atributu sloupce typu objektu zadaného v definici omezení|
|POZIČNÍ|Desetinné číslo|Původní pozice sloupce nebo atributu v definici objektu.|

## <a name="procedureparameters"></a>ProcedureParameters

|ColumnName|DataType|Popis|
|----------------|--------------|-----------------|
|OWNER|String|Vlastník objektu.|
|OBJECT_NAME|String|Název procedury nebo funkce.|
|PACKAGE_NAME|String|Název procedury nebo funkce.|
|OBJECT_ID|Desetinné číslo|Číslo objektu objektu.|
|METODY|String|Jedinečný identifikátor přetížení|
|ARGUMENT_NAME|String|Název argumentu.|
|POZIČNÍ|Desetinné číslo|Pozice v seznamu argumentů nebo hodnota null pro návratovou hodnotu funkce.|
|POŘADÍ|Desetinné číslo|Sekvence argumentů včetně všech úrovní vnoření.|
|DATA_LEVEL|Desetinné číslo|Hloubka vnořeného argumentu pro složené typy.|
|DATA_TYPE|String|Datový typ argumentu.|
|DEFAULT_VALUE|String|Výchozí hodnota argumentu|
|DEFAULT_LENGTH|Desetinné číslo|Délka výchozí hodnoty argumentu|
|IN_OUT|String|Směr argumentu (v, OUT nebo OUT/OUT).|
|DATA_LENGTH|Desetinné číslo|Délka sloupce (v bajtech).|
|DATA_PRECISION|Desetinné číslo|Délka v desítkových číslicích (číslo) nebo binárních číslech (FLOAT).|
|DATA_SCALE|Desetinné číslo|Číslice napravo od desetinné čárky v čísle.|
|RADIX|Desetinné číslo|Základ argumentu pro číslo|
|CHARACTER_SET_NAME|String|Název znakové sady pro argument.|
|TYPE_OWNER|String|Vlastník typu argumentu.|
|TYPE_NAME|String|Název typu argumentu. Pokud je typ místní typ balíčku (to znamená, že je deklarován ve specifikaci balíčku), pak v tomto sloupci se zobrazí název balíčku.|
|TYPE_SUBNAME|String|Relevantní pouze pro místní typy balíčků. Zobrazuje název typu deklarovaného v balíčku identifikovaného ve sloupci TYPE_NAME.|
|TYPE_LINK|String|Platí pouze pro místní typy balíčků, pokud je balíček identifikovaný ve sloupci TYPE_NAME vzdáleným balíčkem. V tomto sloupci se zobrazuje odkaz na databázi, který se používá k odkazování na vzdálený balíček.|
|PLS_TYPE|String|Pro číselné argumenty název typu PL/SQL argumentu. V opačném případě hodnota null.|
|CHAR_LENGTH|Desetinné číslo|Omezení počtu znaků pro řetězcové datové typy.|
|CHAR_USED|String|Označuje, zda je pro řetězec stanovený limit bajtů (B) nebo znak (C).|

## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](ado-net-overview.md)
