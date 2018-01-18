---
title: "Kolekce schématu Oracle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4f199a0fc0939bd5fae4fefb7440c46bd471e4b6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-schema-collections"></a>Kolekce schématu Oracle
Zprostředkovatel dat Microsoft .NET Framework pro Oracle podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:  
  
-   Sloupce  
  
-   Indexy  
  
-   IndexColumns  
  
-   Procedury  
  
-   Sekvence  
  
-   Synonyma.  
  
-   Tabulky  
  
-   Uživatelé  
  
-   zobrazení  
  
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
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastníka tabulky, zobrazení nebo clusteru.|  
|TABLE_NAME|String|Tabulka, zobrazení nebo název clusteru.|  
|COLUMN_NAME|String|Název sloupce.|  
|ID|Desetinné číslo|Při vytváření, pořadové číslo sloupce.|  
|DATOVÝ TYP|String|Datový typ sloupce.|  
|DÉLKA|Desetinné číslo|Délka sloupce v bajtech.|  
|PŘESNOST|Desetinné číslo|Počet desetinných míst pro datový typ Číslo; binární přesnost pro typ FLOAT dat, hodnotu null pro všechny ostatní datové typy.|  
|ŠKÁLOVÁNÍ|Desetinné číslo|Číslic vpravo od desetinné čárky v číslo.|  
|S MOŽNOU HODNOTOU NULL|String|Určuje, zda sloupec povoluje hodnoty Null. Hodnota je N pokud existuje omezení NOT NULL ve sloupci nebo pokud je sloupec součástí primární klíč.|  
  
## <a name="indexes"></a>Indexy  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník indexu|  
|INDEX_NAME|String|Název indexu.|  
|INDEX_TYPE|String|Typ indexu (normální, rastrový OBRÁZEK, na základě funkce normální, na základě funkce rastrového OBRÁZKU nebo domény).|  
|TABLE_OWNER|String|Vlastníka indexovaného objektu.|  
|TABLE_NAME|String|Název objektu indexované.|  
|TABLE_TYPE|String|Typ objektu indexované (například tabulky, clusteru).|  
|JEDINEČNOST|String|Index, jestli je JEDINEČNÝ nebo NONUNIQUE.|  
|KOMPRESE|String|Index, zda je povoleno nebo zakázáno.|  
|PREFIX_LENGTH|Desetinné číslo|Počet sloupců v předponu klíče komprese.|  
|TABLESPACE_NAME|String|Název tabulkového prostoru, který obsahuje index.|  
|INI_TRANS|Desetinné číslo|Počáteční počet transakcí.|  
|MAX_TRANS|Desetinné číslo|Maximální počet transakcí.|  
|INITIAL_EXTENT|Desetinné číslo|Velikost počáteční rozsah.|  
|NEXT_EXTENT|Desetinné číslo|Velikost sekundární rozsahy.|  
|MIN_EXTENTS|Desetinné číslo|Minimální počet povolený v segmentu.|  
|MAX_EXTENTS|Desetinné číslo|Maximální počet povolený v segmentu.|  
|PCT_INCREASE|Desetinné číslo|Procento zvýšení rozsahu velikosti.|  
|PCT_THRESHOLD|Desetinné číslo|Procentuální prahová hodnota povolený pro každý záznam index bloku prostor.|  
|INCLUDE_COLUMN|Desetinné číslo|ID sloupce posledního sloupce mají být zahrnuty v tabulce uspořádané podle indexu index primary key (bez přetečení). V tomto sloupci se mapuje na sloupec COLUMN_ID * zobrazení slovník dat _TAB_COLUMNS.|  
|VOLNÝCH PROSTŘEDKŮ|Desetinné číslo|Počet volných prostředků proces přidělené pro tento segment.|  
|FREELIST_GROUPS|Desetinné číslo|Počet skupin freelist přidělené pro tento segment.|  
|PCT_FREE|Desetinné číslo|Minimální procento volného místa v bloku.|  
|PROTOKOLOVÁNÍ|String|Informace o protokolování.|  
|BLEVEL|Desetinné číslo|B *-strom úroveň: hloubka indexu z jeho kořenový bloku na jeho typu list bloky. Hloubka 0 označuje, že kořenový bloku a listu bloku jsou stejné.|  
|LEAF_BLOCKS|Desetinné číslo|Počet bloků s listu v indexu|  
|DISTINCT_KEYS|Desetinné číslo|Počet jedinečných indexované hodnot. Pro indexy, které vynutit omezení JEDINEČNÝ a primární klíč tato hodnota je stejný jako počet řádků v tabulce (USER_TABLES. NUM_ROWS).|  
|AVG_LEAF_BLOCKS_PER_KEY|Desetinné číslo|Průměrný počet bloků listu, ve kterých se vyskytuje každý odlišné hodnota v indexu se zaokrouhlí na nejbližší celé číslo. Pro indexy, které vynutit omezení JEDINEČNÝ a primární klíč tato hodnota je vždy 1.|  
|AVG_DATA_BLOCKS_PER_KEY|Desetinné číslo|Průměrný počet datových bloků v tabulce, která jsou propojená tímto odlišné hodnoty v indexu zaokrouhlí na nejbližší celé číslo. Tato statistika je průměrný počet datových bloků, které obsahují řádky, které obsahují danou hodnotu indexovaného sloupce.|  
|CLUSTERING_FACTOR|Desetinné číslo|Určuje množství pořadí řádků v tabulce na základě hodnot indexu.|  
|STAV|String|Jestli nedělený index je platné nebo UNUSABLE.|  
|NUM_ROWS|Desetinné číslo|Počet řádků v indexu.|  
|SAMPLE_SIZE|Desetinné číslo|Velikost vzorku použít k analýze index.|  
|LAST_ANALYZED|DateTime|Datum naposledy analyzovali tento index.|  
|STUPEŇ|String|Počet vláken na instanci pro skenování indexu.|  
|INSTANCE|String|Počet instancí, přes který indexy ke skenování.|  
|ROZDĚLENA NA ODDÍLY|String|Jestli je tento index rozdělena na oddíly (Ano &#124; NE).|  
|DOČASNÉ|String|Index, jestli je na dočasné tabulky.|  
|GENERUJE|String|Zda je název indexu systém vygeneruje (Y &#124; N).|  
|SEKUNDÁRNÍ|String|Jestli index je sekundární objekt vytvořený metodě ODCIIndexCreate zásobník Oracle9i dat (Y &#124; N).|  
|BUFFER_POOL|String|Název výchozí fond vyrovnávací paměti má být použit pro index bloky.|  
|USER_STATS|String|Jestli statistiku byla zadána přímo uživatelem.|  
|DOBA TRVÁNÍ|String|Určuje dobu trvání dočasné tabulky: 1) SYS$ relace: řádky zachovány po dobu trvání relace, 2) SYS$ transakce: řádky jsou odstraněny po potvrzení, Null 3) pro trvalé tabulku.|  
|PCT_DIRECT_ACCESS|Desetinné číslo|Pro sekundární index v tabulce uspořádané podle indexu snadno uhodnout podíl řádků s platnými|  
|ITYP_OWNER|String|Pro index domény vlastníkem indextype.|  
|ITYP_NAME|String|Pro index domény, název indextype.|  
|PARAMETRY|String|Pro index domény řetězec parametrů.|  
|GLOBAL_STATS|String|Pro oddílů indexy Určuje, zda statistiky byly shromážděny analýza indexu jako celek (Ano), nebo byly odhadované z statistické údaje o základní oddílů indexu a subpartitions (ne).|  
|DOMIDX_STATUS|String|Odráží stav indexu domény. Hodnota NULL: zadaného indexu není indexem domény. PLATNÉ: index je index platná doména. IDXTYP_INVLD: typ indexu indexu této domény je neplatný.|  
|DOMIDX_OPSTATUS|String|Odráží stav operace, která byla provedena v indexu domény: NULL: Zadaný index není indexem domény. PLATNÉ: operaci provést bez chyb. Se nezdařilo: operace se nezdařila s chybou.|  
|FUNCIDX_STATUS|String|Označuje stav indexu na základě funkce: hodnotu NULL: Nejedná se funkce založené na index, povoleno: index na základě funkce zapnutá, zakázáno: index na základě funkce je zakázán.|  
|JOIN_INDEX|String|Určuje, jestli je připojení k indexu či nikoli.|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|INDEX_OWNER|String|Vlastník indexu.|  
|INDEX_NAME|String|Název indexu.|  
|TABLE_OWNER|String|Vlastníka tabulky nebo clusteru.|  
|TABLE_NAME|String|Název tabulky nebo clusteru.|  
|COLUMN_NAME|String|Název sloupce nebo atribut sloupce typu objektu.|  
|COLUMN_POSITION|Desetinné číslo|Pozice sloupce nebo atributu v indexu.|  
|COLUMN_LENGTH|Desetinné číslo|Indexované délka sloupce.|  
|CHAR_LENGTH|Desetinné číslo|Codepoint maximální délka sloupce.|  
|SESTUP|String|Jestli je sloupec seřazené v sestupném pořadí.|  
  
## <a name="procedures"></a>Procedury  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník objektu.|  
|OBJECT_NAME|String|Název objektu.|  
|SUBOBJECT_NAME|String|Název určitých podřízených objektů (například oddíl).|  
|OBJECT_ID|Desetinné číslo|Číslo objekt slovníku objektu.|  
|DATA_OBJECT_ID|Desetinné číslo|Slovník objekt počet segment, který obsahuje objekt.|  
|LAST_DDL_TIME|DateTime|Časové razítko pro poslední změny objektu vyplývající z příkazu DDL (včetně uděluje a zruší).|  
|ČASOVÉ RAZÍTKO|String|Časové razítko pro specifikaci objektu (textová data).|  
|STAV|String|Stav objektu (platné, neplatné nebo není k dispozici).|  
|DOČASNÉ|String|Jestli je dočasný objekt (aktuální relaci vidí pouze data, která je umístit tento objekt sám sebe).|  
|GENERUJE|String|Název vygenerované systémem tento objekt byl? (Y &#124; N).|  
|SEKUNDÁRNÍ|String|Jestli se jedná o sekundární objekt vytvořený metodě ODCIIndexCreate zásobník Oracle9i dat (Y &#124; N).|  
|VYTVOŘIT|DateTime|Datum vytvoření objektu.|  
  
## <a name="sequences"></a>Sekvence  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|SEQUENCE_OWNER|String|Název majitele pořadí.|  
|SEQUENCE_NAME|String|Název pořadí.|  
|MIN_VALUE|Desetinné číslo|Minimální hodnota pořadí.|  
|MAX_VALUE|Desetinné číslo|Maximální hodnota pořadí.|  
|INCREMENT_BY|Desetinné číslo|Hodnota, podle kterého se zvýší pořadí.|  
|CYCLE_FLAG|String|Pořadí wrap kolem v dosažení limitu.|  
|ORDER_FLAG|String|Generují pořadová čísla v pořadí.|  
|CACHE_SIZE|Desetinné číslo|Počet pořadová čísla do mezipaměti.|  
|LAST_NUMBER|Desetinné číslo|Poslední pořadové číslo zapsaný na disk. Pokud sekvenci používá ukládání do mezipaměti, číslo zapsána do disku je číslo poslední umístěny v mezipaměti pořadí. Toto číslo je pravděpodobně být větší než poslední pořadové číslo, která byla použita.|  
  
## <a name="synonyms"></a>Synonyma.  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník synonymum.|  
|SYNONYM_NAME|String|Název synonymum.|  
|TABLE_OWNER|String|Vlastníkem objektu, který odkazuje synonymum.|  
|TABLE_NAME|String|Název objektu odkazuje synonymum.|  
|DB_LINK|String|Název připojení databáze, který je odkazováno, pokud existuje.|  
  
## <a name="tables"></a>Tabulky  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastníka tabulky.|  
|TABLE_NAME|String|Název tabulky.|  
|TYP|String|Typ tabulky.|  
  
## <a name="users"></a>Uživatelé  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|NÁZEV|String|Jméno uživatele.|  
|ID|Desetinné číslo|Identifikační číslo uživatele.|  
|CREATEDATE FORMÁT|DateTime|Datum vytvoření uživatele.|  
  
## <a name="views"></a>zobrazení  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník zobrazení.|  
|VIEW_NAME|String|Název zobrazení.|  
|TEXT_LENGTH|Desetinné číslo|Délka textu zobrazení.|  
|TEXT|String|Text ze zobrazení.|  
|TYPE_TEXT_LENGTH|Desetinné číslo|Délka klauzuli typ typu zobrazení.|  
|TYPE_TEXT|String|Typ klauzule typu zobrazení.|  
|OID_TEXT_LENGTH|Desetinné číslo|Délka klauzuli OID s typem zobrazení.|  
|OID_TEXT|String|S klauzulí OID typu zobrazení.|  
|VIEW_TYPE_OWNER|String|Vlastník na typu zobrazení, pokud je zobrazení aktuálního zobrazení.|  
|VIEW_TYPE|String|Typ zobrazení, pokud je zobrazení aktuálního zobrazení.|  
|SUPERVIEW_NAME|String|Název superview.|  
  
## <a name="functions"></a>Funkce  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník objektu.|  
|OBJECT_NAME|String|Název objektu.|  
|SUBOBJECT_NAME|String|Název určitých podřízených objektů (například oddíl).|  
|OBJECT_ID|Desetinné číslo|Číslo objekt slovníku objektu.|  
|DATA_OBJECT_ID|Desetinné číslo|Slovník objekt počet segment, který obsahuje objekt.|  
|OBJECT_TYPE|String|Typ objektu.|  
|VYTVOŘIT|DateTime|Datum vytvoření objektu.|  
|LAST_DDL_TIME|DateTime|Časové razítko pro poslední změny objektu vyplývající z příkazu DDL (včetně uděluje a zruší).|  
|ČASOVÉ RAZÍTKO|String|Časové razítko pro specifikaci objektu (textová data)|  
|STAV|String|Stav objektu (platné, neplatné nebo není k dispozici).|  
|DOČASNÉ|String|Jestli je dočasný objekt (aktuální relaci vidí pouze data, která je umístit tento objekt sám sebe).|  
|GENERUJE|String|Název vygenerované systémem tento objekt byl? (Y &#124; N).|  
|SEKUNDÁRNÍ|String|Jestli se jedná o sekundární objekt vytvořený metodě ODCIIndexCreate zásobník Oracle9i dat (Y &#124; N).|  
  
## <a name="packages"></a>Balíčky  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník objektu.|  
|OBJECT_NAME|String|Název objektu.|  
|SUBOBJECT_NAME|String|Název určitých podřízených objektů (například oddíl).|  
|OBJECT_ID|Desetinné číslo|Číslo objekt slovníku objektu.|  
|DATA_OBJECT_ID|Desetinné číslo|Slovník objekt počet segment, který obsahuje objekt.|  
|LAST_DDL_TIME|DateTime|Časové razítko pro poslední změny objektu vyplývající z příkazu DDL (včetně uděluje a zruší).|  
|ČASOVÉ RAZÍTKO|String|Časové razítko pro specifikaci objektu (textová data).|  
|STAV|String|Stav objektu (platné, neplatné nebo není k dispozici).|  
|DOČASNÉ|String|Jestli je dočasný objekt (aktuální relaci vidí pouze data, která je umístit tento objekt sám sebe).|  
|GENERUJE|String|Název vygenerované systémem tento objekt byl? (Y &#124; N).|  
|SEKUNDÁRNÍ|String|Jestli se jedná o sekundární objekt vytvořený metodě ODCIIndexCreate zásobník Oracle9i dat (Y &#124; N).|  
|VYTVOŘIT|DateTime|Datum vytvoření objektu.|  
  
## <a name="packagebodies"></a>PackageBodies  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník objektu.|  
|OBJECT_NAME|String|Název objektu.|  
|SUBOBJECT_NAME|String|Název určitých podřízených objektů (například oddíl).|  
|OBJECT_ID|Desetinné číslo|Číslo objekt slovníku objektu.|  
|DATA_OBJECT_ID|Desetinné číslo|Slovník objekt počet segment, který obsahuje objekt.|  
|LAST_DDL_TIME|DateTime|Časové razítko pro poslední změny objektu vyplývající z příkazu DDL (včetně uděluje a zruší).|  
|ČASOVÉ RAZÍTKO|String|Časové razítko pro specifikaci objektu (textová data).|  
|STAV|String|Stav objektu (platné, neplatné nebo není k dispozici).|  
|DOČASNÉ|String|Jestli je dočasný objekt (aktuální relaci vidí pouze data, která je umístit tento objekt sám sebe).|  
|GENERUJE|String|Název vygenerované systémem tento objekt byl? (Y &#124; N).|  
|SEKUNDÁRNÍ|String|Jestli se jedná o sekundární objekt vytvořený metodě ODCIIndexCreate zásobník Oracle9i dat (Y &#124; N).|  
|VYTVOŘIT|DateTime|Datum vytvoření objektu.|  
  
## <a name="arguments"></a>Arguments  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Jméno vlastníka objektu.|  
|NÁZEV_BALÍČKU|String|Název balíčku.|  
|OBJECT_NAME|String|Název procedury nebo funkce.|  
|ARGUMENT_NAME|String|Název argumentu.|  
|POZICE|Desetinné číslo|Pozice v seznamu argument, nebo hodnota NULL pro funkce návratovou hodnotu.|  
|POŘADÍ|Desetinné číslo|Pořadí argumentů, včetně všech vnořených úrovní.|  
|DEFAULT_VALUE|String|Výchozí hodnota pro argument.|  
|DEFAULT_LENGTH|Desetinné číslo|Délka výchozí hodnota pro argument.|  
|IN_OUT|String|Argument směr (IN, OUT nebo v nebo na více systémů).|  
|DATA_LENGTH|Desetinné číslo|Délka sloupce v bajtech.|  
|DATA_PRECISION|Desetinné číslo|Délka v číslice desítkové soustavy (NUMBER) nebo binární číslic (FLOAT).|  
|DATA_SCALE|Desetinné číslo|Číslic vpravo od desetinné čárky v číslo.|  
|DATA_TYPE|String|Datový typ argumentu.|  
  
## <a name="uniquekeys"></a>UniqueKeys  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník definice omezení.|  
|CONSTRAINT_NAME|String|Název definice omezení.|  
|TABLE_NAME|String|Název přidružené tabulky (nebo zobrazení) s definicí omezení.|  
|SEARCH_CONDITION|String|Text podmínek vyhledávání pro omezení check.|  
|R_OWNER|String|Vlastníka tabulky uvedené v referenčním omezení.|  
|R_CONSTRAINT_NAME|String|Název definice jedinečné omezení pro odkazovanou tabulku.|  
|DELETE_RULE|String|Odstraňte pravidlo pro referenční omezení (CASCADE nebo NO ACTION).|  
|STAV|String|Stav vynucení omezení (povoleno nebo zakázáno).|  
|DEFERRABLE|String|Zda je deferrable omezení.|  
|OVĚŘIT|String|Jestli všechna data dodržuje omezení (ověřit nebo nebyl OVĚŘEN.).|  
|GENERUJE|String|Jestli název omezení je uživatel nebo vygenerované systémem.|  
|BAD|String|Hodnota Ano značí, že toto omezení určuje století nejednoznačný způsobem. Abyste se vyhnuli chybám, které jsou výsledkem této nejednoznačnosti, přepište omezení pomocí funkce TO_DATE čtyřmístný rok.|  
|VYUŽÍVAJÍ|String|Toho, jestli povolené omezení vynucené nebo nevynucené.|  
|LAST_CHANGE|DateTime|Pokud bylo povoleno nebo zakázáno omezení poslední|  
|INDEX_OWNER|String|Jméno uživatele, který je vlastníkem index|  
|INDEX_NAME|String|Název indexu|  
  
## <a name="primarykeys"></a>PrimaryKeys  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník definice omezení.|  
|CONSTRAINT_NAME|String|Název definice omezení.|  
|TABLE_NAME|String|Název přidružené tabulky (nebo zobrazení) s definicí omezení.|  
|SEARCH_CONDITION|String|Text podmínek vyhledávání pro omezení check.|  
|R_OWNER|String|Vlastníka tabulky uvedené v referenčním omezení.|  
|R_CONSTRAINT_NAME|String|Název definice jedinečné omezení pro odkazovanou tabulku.|  
|DELETE_RULE|String|Odstraňte pravidlo pro referenční omezení (CASCADE nebo NO ACTION).|  
|STAV|String|Stav vynucení omezení (povoleno nebo zakázáno).|  
|DEFERRABLE|String|Zda je deferrable omezení.|  
|OVĚŘIT|String|Jestli všechna data dodržuje omezení (ověřit nebo nebyl OVĚŘEN.).|  
|GENERUJE|String|Jestli název omezení je uživatel nebo vygenerované systémem.|  
|BAD|String|Hodnota Ano značí, že toto omezení určuje století nejednoznačný způsobem. Abyste se vyhnuli chybám, které jsou výsledkem této nejednoznačnosti, přepište omezení pomocí funkce TO_DATE čtyřmístný rok.|  
|VYUŽÍVAJÍ|String|Toho, jestli povolené omezení vynucené nebo nevynucené.|  
|LAST_CHANGE|DateTime|Pokud bylo omezení poslední povoleno nebo zakázáno.|  
|INDEX_OWNER|String|Jméno uživatele, který vlastní index.|  
|INDEX_NAME|String|Název indexu.|  
  
## <a name="foreignkeys"></a>ForeignKeys  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|PRIMARY_KEY_CONSTRAINT_NAME|String|Název definice omezení.|  
|PRIMARY_KEY_OWNER|String|Vlastník definice omezení.|  
|PRIMARY_KEY_TABLE_NAME|String|Název přidružené tabulky (nebo zobrazení) s definicí omezení|  
|FOREIGN_KEY_OWNER|String|Vlastník definice omezení.|  
|FOREIGN_KEY_CONSTRIANT_NAME|String|Název definice omezení.|  
|FOREIGN_KEY_TABLE_NAME|String|Název přidružené tabulky (nebo zobrazení) s definicí omezení.|  
|SEARCH_CONDITION|String|Text podmínek vyhledávání pro omezení check|  
|R_OWNER|String|Vlastníka tabulky uvedené v referenčním omezení.|  
|R_CONSTRAINT_NAME|String|Název definice jedinečné omezení pro odkazovanou tabulku.|  
|DELETE_RULE|String|Odstraňte pravidlo pro referenční omezení (CASCADE nebo NO ACTION).|  
|STAV|String|Stav vynucení omezení (povoleno nebo zakázáno).|  
|OVĚŘIT|String|Jestli všechna data dodržuje omezení (ověřit nebo nebyl OVĚŘEN.).|  
|GENERUJE|String|Jestli název omezení je uživatel nebo vygenerované systémem.|  
|VYUŽÍVAJÍ|String|Toho, jestli povolené omezení vynucené nebo nevynucené.|  
|LAST_CHANGE|DateTime|Pokud bylo omezení poslední povoleno nebo zakázáno.|  
|INDEX_OWNER|String|Jméno uživatele, který vlastní index.|  
|INDEX_NAME|String|Název indexu.|  
  
## <a name="foreignkeycolumns"></a>ForeignKeyColumns  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník definice omezení.|  
|CONSTRAINT_NAME|String|Název definice omezení.|  
|TABLE_NAME|String|Název tabulky s definicí omezení.|  
|COLUMN_NAME|String|Název sloupce nebo atribut sloupce typu objektu, který je zadaný v definici omezení.|  
|POZICE|Desetinné číslo|Původní pozice sloupce nebo atributu v definici objektu.|  
  
## <a name="procedureparameters"></a>ProcedureParameters  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|VLASTNÍK|String|Vlastník objektu.|  
|OBJECT_NAME|String|Název procedury nebo funkce.|  
|NÁZEV_BALÍČKU|String|Název procedury nebo funkce.|  
|OBJECT_ID|Desetinné číslo|Počet objektu na objekt.|  
|PŘETÍŽENÍ|String|Přetížení jedinečný identifikátor.|  
|ARGUMENT_NAME|String|Název argumentu.|  
|POZICE|Desetinné číslo|Pozice v seznamu argument, nebo hodnota null pro funkce návratovou hodnotu.|  
|POŘADÍ|Desetinné číslo|Pořadí argumentů, včetně všech vnořených úrovní.|  
|DATA_LEVEL|Desetinné číslo|Vnoření hloubku argument pro složené typy.|  
|DATA_TYPE|String|Datový typ argumentu.|  
|DEFAULT_VALUE|String|Výchozí hodnota pro argument.|  
|DEFAULT_LENGTH|Desetinné číslo|Délka výchozí hodnota pro argument.|  
|IN_OUT|String|Argument směr (IN, OUT nebo v nebo na více systémů).|  
|DATA_LENGTH|Desetinné číslo|Délka sloupce (v bajtech).|  
|DATA_PRECISION|Desetinné číslo|Délka v číslice desítkové soustavy (NUMBER) nebo binární číslic (FLOAT).|  
|DATA_SCALE|Desetinné číslo|Číslic vpravo od desetinné čárky v číslo.|  
|RADIX|Desetinné číslo|Základ – argument pro číslo.|  
|CHARACTER_SET_NAME|String|Znaková sada název pro argument.|  
|TYPE_OWNER|String|Vlastník typ argumentu.|  
|TYPE_NAME|String|Název typu argumentu. Pokud je typ místního typu balíčku (to znamená, že je deklarovaná ve specifikaci balíčku), pak v tomto sloupci se zobrazuje název balíčku.|  
|TYPE_SUBNAME|String|Platí pouze pro místní typy balíčků. Zobrazí název typu deklarován v balíčku v sloupci TYPE_NAME identifikovat.|  
|TYPE_LINK|String|Platí pouze pro místní typy balíčků, pokud je balíček identifikovat ve sloupci TYPE_NAME vzdálených balíčků. V tomto sloupci se zobrazuje připojení databáze používá k odkazování na vzdálených balíčků.|  
|PLS_TYPE|String|Pro číselné argumenty, název typu PL/SQL argumentu. V opačném případě hodnota null.|  
|CHAR_LENGTH|Desetinné číslo|Limit pro počet znaků pro datové typy řetězec.|  
|CHAR_USED|String|Určuje, zda je oficiální řetězce limit bajtů (B) nebo limit char (C).|  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
