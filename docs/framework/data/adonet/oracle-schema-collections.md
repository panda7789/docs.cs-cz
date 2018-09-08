---
title: Kolekce schémat Oracle
ms.date: 03/30/2017
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
ms.openlocfilehash: 342c4cbe994eb983713be0f258e3a029df6739f8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217344"
---
# <a name="oracle-schema-collections"></a>Kolekce schémat Oracle
Microsoft .NET Framework Data Provider pro Oracle podporuje následující kolekce určité schéma kromě společné kolekce schémat:  
  
-   Sloupce  
  
-   Indexy  
  
-   IndexColumns  
  
-   Procedury  
  
-   Sekvence  
  
-   Synonyma  
  
-   Tabulky  
  
-   Uživatelé  
  
-   Zobrazení  
  
-   Funkce  
  
-   Balíčky  
  
-   PackageBodies  
  
-   Arguments  
  
-   UniqueKeys  
  
-   PrimaryKeys  
  
-   ForeignKeys  
  
-   ForeignKeyColumns  
  
-   ProcedureParameters  
  
## <a name="columns"></a>Sloupce  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastníka tabulky, zobrazení nebo clusteru.|  
|TABLE_NAME|String|Tabulka, zobrazení nebo název clusteru.|  
|COLUMN_NAME|String|Název sloupce.|  
|ID|Desetinné číslo|Při vytváření, pořadové číslo sloupce.|  
|DATOVÝ TYP|String|Datový typ sloupce.|  
|DÉLKA|Desetinné číslo|Délka sloupce v bajtech.|  
|PŘESNOST|Desetinné číslo|Počet desetinných míst pro ČÍSELNOU datový typ; binární přesnost datového typu FLOAT, hodnotu null pro všechny další datové typy.|  
|ŠKÁLOVÁNÍ|Desetinné číslo|Číslice vpravo od desetinné čárky v řadě.|  
|S POVOLENOU HODNOTOU NULL|String|Určuje, zda sloupec povoluje hodnoty Null. Je hodnota N pokud existuje omezení NOT NULL ve sloupci nebo pokud sloupec je součástí PRIMÁRNÍHO klíče.|  
  
## <a name="indexes"></a>Indexy  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník indexu|  
|INDEX_NAME|String|Název indexu.|  
|INDEX_TYPE|String|Typ indexu (normální, rastrový OBRÁZEK, používají funkce normální, používají funkce rastrový OBRÁZEK nebo domény).|  
|TABLE_OWNER|String|Vlastníka indexovaného objektu.|  
|TABLE_NAME|String|Název objektu indexované.|  
|TABLE_TYPE|String|Typ objektu indexované (například tabulky, CLUSTER).|  
|JEDINEČNOST|String|Určuje, zda je index UNIQUE nebo NONUNIQUE.|  
|KOMPRESE|String|Index určuje, zda je povoleno nebo zakázáno.|  
|PREFIX_LENGTH|Desetinné číslo|Počet sloupců v předponě klíč komprese.|  
|TABLESPACE_NAME|String|Název tabulkového prostoru, který obsahuje index.|  
|INI_TRANS|Desetinné číslo|Počáteční počet transakcí.|  
|MAX_TRANS|Desetinné číslo|Maximální počet transakcí.|  
|INITIAL_EXTENT|Desetinné číslo|Velikost tohoto počátečního rozsahu.|  
|NEXT_EXTENT|Desetinné číslo|Velikost sekundární oblasti.|  
|MIN_EXTENTS|Desetinné číslo|Minimální počet povolený v segmentu.|  
|MAX_EXTENTS|Desetinné číslo|Maximální počet povolený v segmentu.|  
|PCT_INCREASE|Desetinné číslo|Procento zvětšení velikosti rozsahu.|  
|PCT_THRESHOLD|Desetinné číslo|Procentuální prahová hodnota místa bloku každou položku v indexu povolen.|  
|INCLUDE_COLUMN|Desetinné číslo|Sloupec ID z posledního sloupce mají být zahrnuty v indexu tabulky indexů uspořádané primárního klíče (bez přetečení). V tomto sloupci se mapuje na sloupec COLUMN_ID * _TAB_COLUMNS data slovníku zobrazení.|  
|VOLNÝCH PROSTŘEDKŮ|Desetinné číslo|Počet volných prostředků procesů přidělených pro tento segment.|  
|FREELIST_GROUPS|Desetinné číslo|Počet skupin freelist přidělené pro tento segment.|  
|PCT_FREE|Desetinné číslo|Minimální procento volného místa v bloku.|  
|PROTOKOLOVÁNÍ|String|Informace o protokolování.|  
|BLEVEL|Desetinné číslo|B *-úroveň stromu: hloubka indexu z jeho kořenový blok na jeho typu list bloky. Hloubka 0 označuje, že kořenový blok a blok listu jsou stejné.|  
|LEAF_BLOCKS|Desetinné číslo|Počet bloků listu v indexu|  
|DISTINCT_KEYS|Desetinné číslo|Počet jedinečných hodnot indexované. Pro indexy, které vynutit omezení UNIQUE a PRIMARY KEY tato hodnota je stejný jako počet řádků v tabulce (USER_TABLES. NUM_ROWS).|  
|AVG_LEAF_BLOCKS_PER_KEY|Desetinné číslo|Průměrný počet bloků typu list, ve kterých se zobrazí každou jednoznačnou hodnotu v indexu se zaokrouhlí na nejbližší celé číslo. Pro indexy, které vynutit omezení UNIQUE a PRIMARY KEY tato hodnota je vždy 1.|  
|AVG_DATA_BLOCKS_PER_KEY|Desetinné číslo|Průměrný počet datových bloků v tabulce, které jsou odkazované odlišné hodnoty v indexu zaokrouhlí na nejbližší celé číslo. Tato statistiky je průměrný počet datových bloků, které obsahují řádky, které obsahují dané hodnoty pro sloupce s fulltextovými indexy.|  
|CLUSTERING_FACTOR|Desetinné číslo|Označuje množství pořadí řádků v tabulce na základě hodnot indexu.|  
|STAV|String|Index nedělený na oddíly, jestli je platné nebo UNUSABLE.|  
|NUM_ROWS|Desetinné číslo|Počet řádků v indexu.|  
|SAMPLE_SIZE|Desetinné číslo|Velikost vzorku slouží k analýze index.|  
|LAST_ANALYZED|DateTime|Datum poslední analyzovat tento index.|  
|MÍRY|String|Počet vláken na instanci ke skenování indexu.|  
|INSTANCE|String|Počet instancí, ve kterém indexy ke kontrole.|  
|ROZDĚLIT NA ODDÍLY|String|Určuje, zda je tento index rozdělit na oddíly (Ano &#124; ne).|  
|DOČASNÉ|String|Index určuje, zda je na dočasnou tabulku.|  
|VYGENERUJE|String|Určuje, zda název indexu je generována (Y&#124;N).|  
|SEKUNDÁRNÍ|String|Určuje, zda index je sekundární objekt vytvořený metodou ODCIIndexCreate Oracle9i Datová páska (Y&#124;N).|  
|BUFFER_POOL|String|Název fondu vyrovnávací paměti výchozí se použije pro index bloky.|  
|USER_STATS|String|Určuje, zda byly zadány Statistika přímo uživatelem.|  
|DOBA TRVÁNÍ|String|Určuje dobu trvání dočasnou tabulku: 1) SYS$ relace: řádky jsou zachovány po dobu trvání relace (2) SYS$ transakce: řádky budou odstraněny po potvrzení, 3) hodnotu Null pro trvalou tabulku.|  
|PCT_DIRECT_ACCESS|Desetinné číslo|Pro sekundární index v tabulce indexu uspořádané, procentuální podíl řádků s platnou odhad|  
|ITYP_OWNER|String|Pro doménu index vlastníka indextype.|  
|ITYP_NAME|String|Pro index doménu, název indextype.|  
|PARAMETRY|String|Pro doménu index parametru řetězce.|  
|GLOBAL_STATS|String|Pro dělené indexy označuje, zda statistiky byly shromážděny analýzou indexu jako celek (Ano) nebo byly odhadované ze statistik indexu oddíly a subpartitions (ne).|  
|DOMIDX_STATUS|String|Odráží stav index domény. Hodnota NULL: Zadaný index není index založený na doméně. PLATNÉ: index je index platnou doménu. IDXTYP_INVLD: typ indexu indexu této domény je neplatný.|  
|DOMIDX_OPSTATUS|String|Odráží stav operace, která byla provedena s indexem domény: NULL: Zadaný index není index založený na doméně. PLATNÉ: operaci provést bez chyb. Nezdařilo se: operace se nezdařila s chybou.|  
|FUNCIDX_STATUS|String|Označuje stav index založený na funkce: NULL: Nejedná se používají funkce indexování povoleno: index založený na funkce zapnutá, zakázané: index založený na funkce je zakázaná.|  
|JOIN_INDEX|String|Určuje, zda toto připojení k indexu či nikoli.|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|INDEX_OWNER|String|Vlastník indexu.|  
|INDEX_NAME|String|Název indexu.|  
|TABLE_OWNER|String|Vlastníka tabulky nebo clusteru.|  
|TABLE_NAME|String|Název tabulky nebo clusteru.|  
|COLUMN_NAME|String|Název sloupce nebo atribut sloupec typu objektu.|  
|COLUMN_POSITION|Desetinné číslo|Pozice sloupce nebo atribut v indexu.|  
|COLUMN_LENGTH|Desetinné číslo|Indexované délka sloupce.|  
|CHAR_LENGTH|Desetinné číslo|Bod kódu maximální délka sloupce.|  
|SESTUP|String|Určuje, zda sloupec je seřazen v sestupném pořadí.|  
  
## <a name="procedures"></a>Procedury  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník objektu.|  
|OBJECT_NAME|String|Název objektu.|  
|SUBOBJECT_NAME|String|Název na podřízený (například oddíl).|  
|OBJECT_ID|Desetinné číslo|Číslo objektu slovník objektu.|  
|DATA_OBJECT_ID|Desetinné číslo|Číslo objekt slovníku segment, který obsahuje objekt.|  
|LAST_DDL_TIME|DateTime|Časové razítko poslední změny objektu vyplývající z příkazu DDL (včetně podpory a zruší).|  
|ČASOVÉ RAZÍTKO|String|Časové razítko pro specifikaci objektu (znak data).|  
|STAV|String|Stav objektu (platné, neplatný nebo není k dispozici).|  
|DOČASNÉ|String|Určuje, zda je dočasný objekt (aktuální relace můžete zobrazit pouze data, která je umístěn v tomto objektu samotného).|  
|VYGENERUJE|String|Název vygenerované systémem tento objekt byl? (Y &AMP;#124; N).|  
|SEKUNDÁRNÍ|String|Zda se jedná o sekundární objekt vytvořený metodou ODCIIndexCreate Oracle9i Datová páska (Y &#124; N).|  
|VYTVOŘENÍ|DateTime|Datum vytvoření objektu.|  
  
## <a name="sequences"></a>Sekvence  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|SEQUENCE_OWNER|String|Jméno vlastníka pořadí.|  
|SEQUENCE_NAME|String|Název pořadí.|  
|MIN_VALUE|Desetinné číslo|Minimální hodnota pořadí.|  
|MAX_VALUE|Desetinné číslo|Maximální hodnota pořadí.|  
|INCREMENT_BY|Desetinné číslo|Hodnota, podle kterého se zvýší pořadí.|  
|CYCLE_FLAG|String|Pořadí zalomit na dosažení limitu.|  
|ORDER_FLAG|String|Vygenerují pořadová čísla v pořadí.|  
|CACHE_SIZE|Desetinné číslo|Počet pořadová čísla do mezipaměti.|  
|LAST_NUMBER|Desetinné číslo|Poslední pořadové číslo zapsané na disk. Pokud sekvenci používá ukládání do mezipaměti, počet zapsaných na disk je poslední číslo, které jsou umístěny v mezipaměti pořadí. Toto číslo je pravděpodobně být větší než poslední pořadové číslo, která byla použita.|  
  
## <a name="synonyms"></a>Synonyma  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník synonymum.|  
|SYNONYM_NAME|String|Název synonymum.|  
|TABLE_OWNER|String|Vlastníkem objektu, který odkazuje synonymum.|  
|TABLE_NAME|String|Název objektu, který odkazuje synonymum.|  
|DB_LINK|String|Název odkazu na databázi odkazuje, pokud existuje.|  
  
## <a name="tables"></a>Tabulky  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastníka tabulky.|  
|TABLE_NAME|String|Název tabulky.|  
|TYP|String|Typ tabulky.|  
  
## <a name="users"></a>Uživatelé  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|NÁZEV|String|Jméno uživatele.|  
|ID|Desetinné číslo|Identifikační číslo uživatele.|  
|CREATEDATE FORMÁT|DateTime|Datum vytvoření uživatele.|  
  
## <a name="views"></a>Zobrazení  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník zobrazení.|  
|VIEW_NAME|String|Název zobrazení.|  
|TEXT_LENGTH|Desetinné číslo|Délka textu zobrazení.|  
|TEXT|String|Zobrazit text.|  
|TYPE_TEXT_LENGTH|Desetinné číslo|Délka klauzuli typ zobrazení typu.|  
|TYP|String|Zadejte klauzule aktuálního zobrazení.|  
|OID_TEXT_LENGTH|Desetinné číslo|Délka identifikátoru objektu pomocí klauzule aktuálního zobrazení.|  
|OID_TEXT|String|S klauzulí OID z aktuálního zobrazení.|  
|VIEW_TYPE_OWNER|String|Vlastník typu zobrazení, pokud je zobrazení aktuálního zobrazení.|  
|VIEW_TYPE|String|Typ zobrazení. Pokud je zobrazení aktuálního zobrazení.|  
|SUPERVIEW_NAME|String|Název superview.|  
  
## <a name="functions"></a>Funkce  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník objektu.|  
|OBJECT_NAME|String|Název objektu.|  
|SUBOBJECT_NAME|String|Název na podřízený (například oddíl).|  
|OBJECT_ID|Desetinné číslo|Číslo objektu slovník objektu.|  
|DATA_OBJECT_ID|Desetinné číslo|Číslo objekt slovníku segment, který obsahuje objekt.|  
|OBJECT_TYPE|String|Typ objektu.|  
|VYTVOŘENÍ|DateTime|Datum vytvoření objektu.|  
|LAST_DDL_TIME|DateTime|Časové razítko poslední změny objektu vyplývající z příkazu DDL (včetně podpory a zruší).|  
|ČASOVÉ RAZÍTKO|String|Časové razítko pro specifikaci objektu (znak data)|  
|STAV|String|Stav objektu (platné, neplatný nebo není k dispozici).|  
|DOČASNÉ|String|Určuje, zda je dočasný objekt (aktuální relace můžete zobrazit pouze data, která je umístěn v tomto objektu samotného).|  
|VYGENERUJE|String|Název vygenerované systémem tento objekt byl? (Y &AMP;#124; N).|  
|SEKUNDÁRNÍ|String|Zda se jedná o sekundární objekt vytvořený metodou ODCIIndexCreate Oracle9i Datová páska (Y &#124; N).|  
  
## <a name="packages"></a>Balíčky  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník objektu.|  
|OBJECT_NAME|String|Název objektu.|  
|SUBOBJECT_NAME|String|Název na podřízený (například oddíl).|  
|OBJECT_ID|Desetinné číslo|Číslo objektu slovník objektu.|  
|DATA_OBJECT_ID|Desetinné číslo|Číslo objekt slovníku segment, který obsahuje objekt.|  
|LAST_DDL_TIME|DateTime|Časové razítko poslední změny objektu vyplývající z příkazu DDL (včetně podpory a zruší).|  
|ČASOVÉ RAZÍTKO|String|Časové razítko pro specifikaci objektu (znak data).|  
|STAV|String|Stav objektu (platné, neplatný nebo není k dispozici).|  
|DOČASNÉ|String|Určuje, zda je dočasný objekt (aktuální relace můžete zobrazit pouze data, která je umístěn v tomto objektu samotného).|  
|VYGENERUJE|String|Název vygenerované systémem tento objekt byl? (Y &AMP;#124; N).|  
|SEKUNDÁRNÍ|String|Zda se jedná o sekundární objekt vytvořený metodou ODCIIndexCreate Oracle9i Datová páska (Y &#124; N).|  
|VYTVOŘENÍ|DateTime|Datum vytvoření objektu.|  
  
## <a name="packagebodies"></a>PackageBodies  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník objektu.|  
|OBJECT_NAME|String|Název objektu.|  
|SUBOBJECT_NAME|String|Název na podřízený (například oddíl).|  
|OBJECT_ID|Desetinné číslo|Číslo objektu slovník objektu.|  
|DATA_OBJECT_ID|Desetinné číslo|Číslo objekt slovníku segment, který obsahuje objekt.|  
|LAST_DDL_TIME|DateTime|Časové razítko poslední změny objektu vyplývající z příkazu DDL (včetně podpory a zruší).|  
|ČASOVÉ RAZÍTKO|String|Časové razítko pro specifikaci objektu (znak data).|  
|STAV|String|Stav objektu (platné, neplatný nebo není k dispozici).|  
|DOČASNÉ|String|Určuje, zda je dočasný objekt (aktuální relace můžete zobrazit pouze data, která je umístěn v tomto objektu samotného).|  
|VYGENERUJE|String|Název vygenerované systémem tento objekt byl? (Y &AMP;#124; N).|  
|SEKUNDÁRNÍ|String|Zda se jedná o sekundární objekt vytvořený metodou ODCIIndexCreate Oracle9i Datová páska (Y &#124; N).|  
|VYTVOŘENÍ|DateTime|Datum vytvoření objektu.|  
  
## <a name="arguments"></a>Arguments  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Jméno vlastníka objektu.|  
|NÁZEV_BALÍČKU|String|Název balíčku.|  
|OBJECT_NAME|String|Název procedury nebo funkce.|  
|ARGUMENT_NAME|String|Název argumentu.|  
|POZICE|Desetinné číslo|Pozice v seznamu argumentů, nebo hodnota NULL pro návratovou hodnotu funkce.|  
|POŘADÍ|Desetinné číslo|Pořadí argumentů, včetně všech úrovní vnoření.|  
|DEFAULT_VALUE|String|Výchozí hodnota pro argument.|  
|DEFAULT_LENGTH|Desetinné číslo|Délka výchozí hodnoty pro argument.|  
|IN_OUT|String|Směrování argumentu (IN, OUT nebo IN/OUT).|  
|DATA_LENGTH|Desetinné číslo|Délka sloupce v bajtech.|  
|DATA_PRECISION|Desetinné číslo|Délka v desítkové číslice (číslo) nebo binární číslice (FLOAT).|  
|DATA_SCALE|Desetinné číslo|Číslice vpravo od desetinné čárky v řadě.|  
|DATA_TYPE|String|Datový typ argumentu.|  
  
## <a name="uniquekeys"></a>UniqueKeys  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník omezení definice.|  
|CONSTRAINT_NAME|String|Název definice omezení.|  
|TABLE_NAME|String|Název přidružený k tabulce (nebo zobrazení) s definicí omezení.|  
|SEARCH_CONDITION|String|Text podmínek vyhledávání pro omezení check.|  
|R_OWNER|String|Vlastníka tabulky uvedené v referenčním omezení.|  
|R_CONSTRAINT_NAME|String|Název definice omezení jedinečnosti pro odkazovanou tabulku.|  
|DELETE_RULE|String|Odstraňte pravidlo pro referenční omezení (sebe nebo NO ACTION).|  
|STAV|String|Stav vynucení omezení (povoleno nebo zakázáno).|  
|NEBYLA|String|Určuje, zda je nebyla omezení.|  
|OVĚŘENÍ|String|Určuje, zda všechna data dodržuje omezení (ověřuje nebo ne).|  
|VYGENERUJE|String|Určuje, zda je název omezení uživatele nebo vygenerované systémem.|  
|ŠPATNÉ|String|Hodnota Ano značí, že toto omezení určuje století nejednoznačný způsobem. Aby nedocházelo k chybám vyplývající z této nejednoznačnosti, přepište omezení pomocí funkce TO_DATE čtyřmístný rok.|  
|SPOLEHNĚTE SE|String|Určuje, zda povolená omezení je vynucené nebo nevynucené.|  
|LAST_CHANGE|DateTime|Pokud bylo povoleno nebo zakázáno omezení poslední|  
|INDEX_OWNER|String|Jméno uživatele, vlastnící index|  
|INDEX_NAME|String|Název indexu|  
  
## <a name="primarykeys"></a>PrimaryKeys  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník omezení definice.|  
|CONSTRAINT_NAME|String|Název definice omezení.|  
|TABLE_NAME|String|Název přidružený k tabulce (nebo zobrazení) s definicí omezení.|  
|SEARCH_CONDITION|String|Text podmínek vyhledávání pro omezení check.|  
|R_OWNER|String|Vlastníka tabulky uvedené v referenčním omezení.|  
|R_CONSTRAINT_NAME|String|Název definice omezení jedinečnosti pro odkazovanou tabulku.|  
|DELETE_RULE|String|Odstraňte pravidlo pro referenční omezení (sebe nebo NO ACTION).|  
|STAV|String|Stav vynucení omezení (povoleno nebo zakázáno).|  
|NEBYLA|String|Určuje, zda je nebyla omezení.|  
|OVĚŘENÍ|String|Určuje, zda všechna data dodržuje omezení (ověřuje nebo ne).|  
|VYGENERUJE|String|Určuje, zda je název omezení uživatele nebo vygenerované systémem.|  
|ŠPATNÉ|String|Hodnota Ano značí, že toto omezení určuje století nejednoznačný způsobem. Aby nedocházelo k chybám vyplývající z této nejednoznačnosti, přepište omezení pomocí funkce TO_DATE čtyřmístný rok.|  
|SPOLEHNĚTE SE|String|Určuje, zda povolená omezení je vynucené nebo nevynucené.|  
|LAST_CHANGE|DateTime|Omezení při posledního povoleno nebo zakázáno.|  
|INDEX_OWNER|String|Jméno uživatele, vlastnící index.|  
|INDEX_NAME|String|Název indexu.|  
  
## <a name="foreignkeys"></a>ForeignKeys  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|PRIMARY_KEY_CONSTRAINT_NAME|String|Název definice omezení.|  
|PRIMARY_KEY_OWNER|String|Vlastník omezení definice.|  
|PRIMARY_KEY_TABLE_NAME|String|Název přidružený k s definicí omezení tabulky (nebo zobrazení)|  
|FOREIGN_KEY_OWNER|String|Vlastník omezení definice.|  
|FOREIGN_KEY_CONSTRIANT_NAME|String|Název definice omezení.|  
|FOREIGN_KEY_TABLE_NAME|String|Název přidružený k tabulce (nebo zobrazení) s definicí omezení.|  
|SEARCH_CONDITION|String|Text podmínek vyhledávání pro omezení check|  
|R_OWNER|String|Vlastníka tabulky uvedené v referenčním omezení.|  
|R_CONSTRAINT_NAME|String|Název definice omezení jedinečnosti pro odkazovanou tabulku.|  
|DELETE_RULE|String|Odstraňte pravidlo pro referenční omezení (sebe nebo NO ACTION).|  
|STAV|String|Stav vynucení omezení (povoleno nebo zakázáno).|  
|OVĚŘENÍ|String|Určuje, zda všechna data dodržuje omezení (ověřuje nebo ne).|  
|VYGENERUJE|String|Určuje, zda je název omezení uživatele nebo vygenerované systémem.|  
|SPOLEHNĚTE SE|String|Určuje, zda povolená omezení je vynucené nebo nevynucené.|  
|LAST_CHANGE|DateTime|Omezení při posledního povoleno nebo zakázáno.|  
|INDEX_OWNER|String|Jméno uživatele, vlastnící index.|  
|INDEX_NAME|String|Název indexu.|  
  
## <a name="foreignkeycolumns"></a>ForeignKeyColumns  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník omezení definice.|  
|CONSTRAINT_NAME|String|Název definice omezení.|  
|TABLE_NAME|String|Název tabulky s definicí omezení.|  
|COLUMN_NAME|String|Název sloupce nebo atribut zadaný v definici omezení sloupce typu objektu.|  
|POZICE|Desetinné číslo|Původní pozici sloupce nebo atributu v definici objektu.|  
  
## <a name="procedureparameters"></a>ProcedureParameters  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník objektu.|  
|OBJECT_NAME|String|Název procedury nebo funkce.|  
|NÁZEV_BALÍČKU|String|Název procedury nebo funkce.|  
|OBJECT_ID|Desetinné číslo|Číslo objektu objektu.|  
|PŘETÍŽENÍ|String|Jedinečný identifikátor přetížení.|  
|ARGUMENT_NAME|String|Název argumentu.|  
|POZICE|Desetinné číslo|Pozice v seznamu argumentů, nebo hodnota null pro návratovou hodnotu funkce.|  
|POŘADÍ|Desetinné číslo|Pořadí argumentů, včetně všech úrovní vnoření.|  
|DATA_LEVEL|Desetinné číslo|Vnoření hloubky argumentu pro složené typy.|  
|DATA_TYPE|String|Datový typ argumentu.|  
|DEFAULT_VALUE|String|Výchozí hodnota pro argument.|  
|DEFAULT_LENGTH|Desetinné číslo|Délka výchozí hodnoty pro argument.|  
|IN_OUT|String|Směrování argumentu (IN, OUT nebo IN/OUT).|  
|DATA_LENGTH|Desetinné číslo|Délka sloupce (v bajtech).|  
|DATA_PRECISION|Desetinné číslo|Délka v desítkové číslice (číslo) nebo binární číslice (FLOAT).|  
|DATA_SCALE|Desetinné číslo|Číslic vpravo od desetinné čárky v řadě.|  
|RADIX|Desetinné číslo|Argument základ pro číslo.|  
|CHARACTER_SET_NAME|String|Znaková sada název argumentu.|  
|TYPE_OWNER|String|Vlastník typu argumentu.|  
|TYPE_NAME|String|Název typu argumentu. Pokud je typ balíčku místního typu (to znamená, že je deklarována v specifikace balíčku), pak tento sloupec zobrazuje název balíčku.|  
|TYPE_SUBNAME|String|Platí pouze pro místní typy balíčků. Zobrazí název typu deklarován v balíčku označené ve sloupci TYPE_NAME.|  
|TYPE_LINK|String|Platí pouze pro místní typy balíčků, pokud je balíček označené ve sloupci TYPE_NAME vzdálených balíčků. Tento sloupec zobrazuje odkaz databáze používá k odkazování na vzdálených balíčků.|  
|PLS_TYPE|String|U argumentů, název typu PL/SQL argumentu. V opačném případě hodnota null.|  
|CHAR_LENGTH|Desetinné číslo|Omezení počtu znaků pro řetězcovými datovými typy.|  
|CHAR_USED|String|Označuje, zda je oficiální řetězce limit bajtů (B) nebo limit char (C).|  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
