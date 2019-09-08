---
title: Společné kolekce schémat
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: 0b23164b56c6fefc6c258f313e9e17b156605518
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786796"
---
# <a name="common-schema-collections"></a>Společné kolekce schémat
Společné kolekce schémat jsou kolekce schémat, které jsou implementované všemi .NET Framework spravovanými zprostředkovateli. Můžete zadat dotaz na .NET Framework spravovaného poskytovatele a určit seznam podporovaných kolekcí schémat voláním metody **GetSchema** bez argumentů nebo s názvem kolekce schématu "MetaDataCollections". Tato akce vrátí <xref:System.Data.DataTable> seznam podporovaných kolekcí schémat, počet omezení, která jednotlivé požadavky podporují, a počet částí identifikátorů, které používají. Tyto kolekce popisují všechny požadované sloupce. Poskytovatelé jsou volní, pokud chtějí přidat další sloupce. Například `SqlClient` a`OracleClient` přidejte ParameterName do kolekce omezení.  
  
 Pokud zprostředkovatel nemůže určit hodnotu požadovaného sloupce, vrátí hodnotu null.  
  
 Další informace o použití metod **GetSchema** naleznete v tématu [GetSchema a Schema Collections](getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Tato kolekce schémat zpřístupňuje informace o všech kolekcích schémat podporovaných zprostředkovatelem .NET Framework spravovaném poskytovatelem, který se aktuálně používá pro připojení k databázi.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|collectionName|odkazy řetězců|Název kolekce, která má být předána metodě **GetSchema** pro vrácení kolekce.|  
|NumberOfRestrictions|int|Počet omezení, která lze pro kolekci zadat.|  
|NumberOfIdentifierParts|int|Počet částí v složeném identifikátoru nebo názvu databázového objektu. Například v SQL Server by to bylo 3 pro tabulky a 4 pro sloupce. V Oracle by to bylo 2 pro tabulky a 3 pro sloupce.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 Tato kolekce schémat zpřístupňuje informace o zdroji dat, ke kterému je aktuálně připojen .NET Framework spravovaného zprostředkovatele.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|odkazy řetězců|Regulární výraz, který bude odpovídat složeným oddělovačům ve složeném identifikátoru. Například "\\." (pro SQL Server) nebo "\@&#124;\\." (pro Oracle).<br /><br /> Složený identifikátor obvykle používá pro název databázového objektu, například: pubs. dbo. Authors nebo pubs\@dbo. Authors.<br /><br /> Pro SQL Server použijte regulární výraz "\\.". Pro OracleClient použijte "\@&#124;\\.".<br /><br /> Pro rozhraní ODBC použijte Catalog_name_seperator.<br /><br /> Pro OLE DB použít DBLITERAL_CATALOG_SEPARATOR nebo DBLITERAL_SCHEMA_SEPARATOR.|  
|DataSourceProductName|odkazy řetězců|Název produktu, ke kterému přistupoval poskytovatel, například "Oracle" nebo "SQLServer".|  
|DataSourceProductVersion|odkazy řetězců|Určuje verzi produktu, ke kterému přistupoval poskytovatel, v nativním formátu zdrojů dat, nikoli ve formátu Microsoft.<br /><br /> V některých případech bude DataSourceProductVersion a DataSourceProductVersionNormalized stejnou hodnotou. V případě OLE DB a rozhraní ODBC budou tyto vždy stejné, jako jsou namapovány na stejné volání funkce v nadřazeném nativním rozhraní API.|  
|DataSourceProductVersionNormalized|odkazy řetězců|Normalizovaná verze pro zdroj dat, která může být porovnána s `String.Compare()`. Formát je konzistentní pro všechny verze zprostředkovatele, aby nedocházelo k řazení verze 10 mezi verze 1 a verze 2.<br /><br /> Poskytovatel Oracle například používá formát "NN. NN. NN. NN. NN" pro svou normalizovanou verzi, což způsobí, že zdroj dat Oracle 8i vrátí "08.01.07.04.01". SQL Server používá typický formát Microsoft "NN. NN. nnnn".<br /><br /> V některých případech bude DataSourceProductVersion a DataSourceProductVersionNormalized stejnou hodnotou. V případě OLE DB a rozhraní ODBC budou vždy stejná jako namapováno na stejné volání funkce v nadřazeném nativním rozhraní API.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|Určuje vztah mezi sloupci v klauzuli GROUP BY a neagregovanými sloupci v seznamu pro výběr.|  
|IdentifierPattern|odkazy řetězců|Regulární výraz, který odpovídá identifikátoru a má hodnotu shody identifikátoru. Například "[A-za-z0-9_ # $]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Označuje, zda jsou jiné identifikátory než v uvozovkách považovány za rozlišovat velká a malá písmena.|  
|OrderByColumnsInSelect|bool|Určuje, zda sloupce v klauzuli ORDER BY musí být v seznamu SELECT. Hodnota true značí, že musí být v seznamu SELECT, hodnota false znamená, že v seznamu Select nejsou vyžadovány.|  
|ParameterMarkerFormat|odkazy řetězců|Formátovací řetězec, který představuje způsob formátování parametru.<br /><br /> Pokud jsou pojmenované parametry podporovány zdrojem dat, první zástupný symbol v tomto řetězci by měl mít formát názvu parametru.<br /><br /> Například pokud zdroj dat očekává parametry s názvem a předponou ': ', bude ":{0}". Při formátování s názvem parametru "P1" je výsledný řetězec ":p 1".<br /><br /> Pokud zdroj\@dat očekává parametry s předponou ' ', ale názvy je již zahrnuly, může to{0}být ' ' a výsledek formátování parametru s názvem "\@P1" by jednoduše představoval "\@P1".<br /><br /> Pro zdroje dat, které neočekávají pojmenované parametry a očekávají použití? znak, formátovací řetězec může být zadán jako jednoduchý znak "?", který by ignoroval název parametru. Pro OLE DB vrátíme "?".|  
|ParameterMarkerPattern|odkazy řetězců|Regulární výraz, který odpovídá značce parametru. Bude mít hodnotu shody názvu parametru, pokud existuje.<br /><br /> Například pokud jsou pojmenované parametry podporovány se\@znakem "", který bude zahrnut do názvu parametru, bude: "(\@[A-za-z0-9_ $ #] *)".<br /><br /> Pokud se ale u pojmenovaných parametrů podporuje znak ":" jako úvodní znak a není součástí názvu parametru, může to být: ":([A-za-z0-9_ $ #]\*)".<br /><br /> Pokud zdroj dat samozřejmě nepodporuje pojmenované parametry, bude to jednoduše "?".|  
|ParameterNameMaxLength|int|Maximální délka názvu parametru ve znacích. Visual Studio očekává, že pokud jsou podporovány názvy parametrů, minimální hodnota maximální délky je 30 znaků.<br /><br /> Pokud zdroj dat nepodporuje pojmenované parametry, vrátí tato vlastnost hodnotu nula.|  
|ParameterNamePattern|odkazy řetězců|Regulární výraz, který odpovídá platným názvům parametrů. Různé zdroje dat mají různá pravidla týkající se znaků, které se dají použít pro názvy parametrů.<br /><br /> Sada Visual Studio očekává, že pokud jsou podporovány názvy parametrů, jsou znaky "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" minimální podporovanou sadou znaků, které jsou platné pro názvy parametrů.|  
|QuotedIdentifierPattern|odkazy řetězců|Regulární výraz, který odpovídá identifikátoru v uvozovkách a má hodnotu shody samotného identifikátoru bez uvozovek. Například pokud zdroj dat použil dvojité uvozovky k identifikaci v apostrofech, bude to\\: "(([^"]&#124;\\"\\") *) ".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Označuje, zda jsou v uvozovkách považovány za rozlišovat velká a malá písmena.|  
|StatementSeparatorPattern|odkazy řetězců|Regulární výraz, který odpovídá oddělovači příkazů.|  
|StringLiteralPattern|odkazy řetězců|Regulární výraz, který odpovídá literálu řetězce a má hodnotu shody samotného literálu. Například pokud zdroj dat použil jednotlivé uvozovky k identifikaci řetězců, bude: "([^ ']&#124;' ') * ')" '|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Určuje, jaké typy příkazů JOIN SQL jsou podporovány zdrojem dat.|  
  
## <a name="datatypes"></a>Datové typy  
 Tato kolekce schémat zpřístupňuje informace o datových typech podporovaných databází, ke kterým je aktuálně připojen .NET Framework spravovaného zprostředkovatele.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|TypeName|odkazy řetězců|Název datového typu specifický pro poskytovatele.|  
|ProviderDbType|int|Hodnota typu specifická pro poskytovatele, která se má použít při určení typu parametru. Například SqlDbType. Money nebo OracleType. blob.|  
|ColumnSize|long|Délka nečíselného sloupce nebo parametru odkazuje buď na maximum, nebo na délku definovanou pro tento typ zprostředkovatelem.<br /><br /> U znakových dat je to maximální nebo definovaná délka v jednotkách definovaných zdrojem dat. Oracle má koncepci zadání délky a pak specifikuje skutečnou velikost úložiště pro některé znakové datové typy. Tato definice definuje pouze délku v jednotkách pro Oracle.<br /><br /> V případě datových typů data a času se jedná o délku řetězcového vyjádření (za předpokladu, že je maximální povolená přesnost součásti zlomků sekund).<br /><br /> Pokud je datový typ numerický, jedná se o horní mez nad maximální přesnost datového typu.|  
|CreateFormat|odkazy řetězců|Řetězec formátu, který představuje způsob přidání tohoto sloupce do příkazu definice dat, například CREATE TABLE. Každý prvek v poli CreateParameter by měl být reprezentován "značkami parametru" v řetězci formátu.<br /><br /> Například datový typ desetinné číslo SQL vyžaduje přesnost a měřítko. V tomto případě bude řetězec formátu "DECIMAL ({0},{1})".|  
|CreateParameters|odkazy řetězců|Parametry vytváření, které je třeba zadat při vytváření sloupce tohoto datového typu. Každý parametr vytvoření je uveden v řetězci, oddělený čárkou v pořadí, ve kterém mají být dodány.<br /><br /> Například datový typ desetinné číslo SQL vyžaduje přesnost a měřítko. V takovém případě by parametry vytváření měly obsahovat řetězec "Precision, Scale".<br /><br /> V textovém příkazu pro vytvoření desetinného sloupce s přesností 10 a měřítka 2 může být hodnota sloupce CreateFormat desítková ({0},{1}) a kompletní specifikace typu by byla desítková (10, 2).|  
|DataType|odkazy řetězců|Název .NET Frameworkho typu datového typu.|  
|IsAutoincrementable|bool|true – hodnoty tohoto datového typu se můžou automaticky zvyšovat.<br /><br /> false – hodnoty tohoto datového typu nemusí být automaticky zvyšovány.<br /><br /> Všimněte si, že tato možnost je pouze indikována tím, zda sloupec tohoto datového typu může být automaticky zvyšován, nikoli zda jsou všechny sloupce tohoto typu automaticky zvyšovány.|  
|IsBestMatch|bool|true – datový typ je nejlepší shody mezi všemi datovými typy v úložišti dat a datovým typem .NET Framework, který je označen hodnotou ve sloupci DataType.<br /><br /> false – datový typ není nejlepší shody.<br /><br /> Pro každou sadu řádků, ve které je hodnota sloupce DataType shodná, je sloupec IsBestMatch nastaven na hodnotu true pouze v jednom řádku.|  
|IsCaseSensitive|bool|true – datový typ je typ znaku a rozlišuje velká a malá písmena.<br /><br /> false – datový typ není typ znaku nebo nerozlišuje velká a malá písmena.|  
|IsFixedLength|bool|true – sloupce tohoto datového typu, které jsou vytvořené jazykem DDL (Data Definition Language), budou mít pevnou délku.<br /><br /> false – sloupce tohoto datového typu, které jsou vytvořené pomocí DDL, budou mít proměnlivou délku.<br /><br /> DBNull. Value – není známo, zda poskytovatel mapuje toto pole se sloupcem s pevnou délkou nebo s proměnlivou délkou.|  
|IsFixedPrecisionScale|bool|true – datový typ má pevnou přesnost a škálování.<br /><br /> false – datový typ nemá pevnou přesnost a škálování.|  
|Long|bool|true – datový typ obsahuje velmi dlouhá data; definice velmi dlouhých dat je specifická pro konkrétního poskytovatele.<br /><br /> false – datový typ neobsahuje velmi dlouhá data.|  
|IsNullable|bool|true – datový typ může mít hodnotu null.<br /><br /> false – datový typ nemůže mít hodnotu null.<br /><br /> DBNull. Value – není známo, zda datový typ může mít hodnotu null.|  
|Prohledávatelné|bool|true – datový typ lze použít v klauzuli WHERE s libovolným operátorem s výjimkou predikátu LIKE.<br /><br /> false – datový typ nelze použít v klauzuli WHERE s libovolným operátorem s výjimkou predikátu LIKE.|  
|IsSearchableWithLike|bool|true – datový typ se dá použít s predikátem LIKE.<br /><br /> false – datový typ nelze použít s predikátem LIKE.|  
|Bez znaménka|bool|true – datový typ je bez znaménka.<br /><br /> false – datový typ je podepsán.<br /><br /> DBNull. Value – nelze použít pro datový typ.|  
|MaximumScale|short|Pokud je indikátorem typu číselný typ, jedná se o maximální počet číslic, které jsou povoleny napravo od desetinné čárky. V opačném případě se jedná o DBNull. Value.|  
|MinimumScale|short|Pokud je indikátorem typu číselný typ, jedná se o minimální počet číslic, které jsou povoleny napravo od desetinné čárky. V opačném případě se jedná o DBNull. Value.|  
|IsConcurrencyType|bool|true – datový typ se aktualizuje v databázi pokaždé, když se změní řádek a hodnota sloupce se liší od všech předchozích hodnot.<br /><br /> false – datový typ je při každé změně řádku aktualizován databází<br /><br /> DBNull. Value – databáze nepodporuje tento typ datového typu.|  
|IsLiteralSupported|bool|true – datový typ může být vyjádřený jako literál.<br /><br /> false – datový typ nemůže být vyjádřen jako literál.|  
|LiteralPrefix|odkazy řetězců|Předpona použitá pro daný literál.|  
|LiteralSuffix|odkazy řetězců|Přípona použitá pro daný literál.|  
|NativeDataType|String|NativeDataType je konkrétní sloupec OLE DB pro vystavení OLE DBho typu datového typu.|  
  
## <a name="restrictions"></a>Omezení  
 Tato kolekce schémat vystavila informace o omezeních podporovaných zprostředkovatelem .NET Framework spravovaném poskytovatelem, který se aktuálně používá pro připojení k databázi.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|collectionName|odkazy řetězců|Název kolekce, pro kterou platí tato omezení|  
|Omezení|odkazy řetězců|Název omezení v kolekci|  
|RestrictionDefault|odkazy řetězců|Přeskočen.|  
|RestrictionNumber|int|Skutečné umístění v kolekcích omezuje tato konkrétní omezení.|  
  
## <a name="reservedwords"></a>ReservedWords  
 Tato kolekce schémat zpřístupňuje informace o slovech, která jsou vyhrazena databázím, ke kterému .NET Framework spravovaný zprostředkovatel aktuálně připojen.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|ReservedWord|odkazy řetězců|Vyhrazené slovo specifické pro poskytovatele|  
  
## <a name="see-also"></a>Viz také:

- [Načítání informací o databázovém schématu](retrieving-database-schema-information.md)
- [Příkaz GetSchema a kolekce schémat](getschema-and-schema-collections.md)
- [Přehled ADO.NET](ado-net-overview.md)
