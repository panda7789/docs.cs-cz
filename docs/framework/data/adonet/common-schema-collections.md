---
title: Společné kolekce schémat
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: b6c2c89101f3304a0cab014de2def22195541471
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249471"
---
# <a name="common-schema-collections"></a>Společné kolekce schémat
Společné kolekce schématu jsou kolekce schématu, které jsou implementovány jednotlivými zprostředkovateli spravovaného rozhraní .NET Framework. Můžete dotaz zprostředkovatele spravovaného rozhraní .NET Framework určit seznam podporovaných kolekcí schématu voláním **GetSchema** metoda bez argumentů nebo s názvem kolekce schématu "MetaDataCollections". Tím se <xref:System.Data.DataTable> vrátí seznam podporovaných kolekcí schématu, počet omezení, které podporují, a počet částí identifikátoru, které používají. Tyto kolekce popisují všechny požadované sloupce. Poskytovatelé mohou přidat další sloupce, pokud si to přejí. Například `SqlClient` a `OracleClient` přidejte ParameterName do kolekce omezení.  
  
 Pokud zprostředkovatel není schopen určit hodnotu požadovaného sloupce, vrátí hodnotu null.  
  
 Další informace o použití **metody GetSchema** naleznete v tématu [GetSchema a kolekce schématu](getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Tato kolekce schématu zveřejňuje informace o všech kolekcí schématu podporovaných spravovaným zprostředkovatelem rozhraní .NET Framework, který se aktuálně používá k připojení k databázi.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|CollectionName|řetězec|Název kolekce předat **GetSchema** metoda vrátit kolekce.|  
|Početomezení|int|Počet omezení, které mohou být určeny pro kolekci.|  
|NumberOfIdentifierParts|int|Počet částí v názvu objektu složený identifikátor/databáze. Například v SQL Server by to bylo 3 pro tabulky a 4 pro sloupce. V Oracle by to bylo 2 pro tabulky a 3 pro sloupce.|  
  
## <a name="datasourceinformation"></a>Informace o zdroji dat  
 Tato kolekce schématu zveřejňuje informace o zdroji dat, ke kterému se aktuálně připojuje zprostředkovatel správy rozhraní .NET Framework.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|Vzor oddělovače složených identifikátorů|řetězec|Regulární výraz tak, aby odpovídal složeným oddělovačům ve složeném identifikátoru. Například "\\" " " . (pro SQL Server)\@ \\nebo "&#124;". (pro společnost Oracle).<br /><br /> Složený identifikátor se obvykle používá pro název databázového objektu, například: pubs.dbo.authors nebo pubs\@dbo.authors.<br /><br /> Pro SQL Server použijte regulární výraz ".".\\ Pro řešení OracleClient\@ \\použijte "&#124;".<br /><br /> Pro rozhraní ODBC použijte Catalog_name_seperator.<br /><br /> Pro TECHNOLOGIE OLE DB použijte DBLITERAL_CATALOG_SEPARATOR nebo DBLITERAL_SCHEMA_SEPARATOR.|  
|Název_produktu DataSourceProductName|řetězec|Název produktu, ke který má poskytovatel přístup, například "Oracle" nebo "SQLServer".|  
|Verze ProductSourceProductVersion|řetězec|Označuje verzi produktu, ke které má poskytovatel přístup, v nativním formátu zdrojů dat, nikoli ve formátu společnosti Microsoft.<br /><br /> V některých případech DataSourceProductVersion a DataSourceProductVersionNormalized bude stejná hodnota. V případě OLE DB a ODBC budou vždy stejné jako na stejné volání funkce v podkladovém nativním rozhraní API.|  
|DataSourceProductVersionNormalized|řetězec|Normalizovaná verze pro zdroj dat tak, aby `String.Compare()`jej lze porovnat s . Formát tohoto je konzistentní pro všechny verze zprostředkovatele zabránit verzi 10 z řazení mezi verzí 1 a verze 2.<br /><br /> Například poskytovatel Oracle používá formát "nn.nn.nn.nn", pro jeho normalizovanou verzi, která způsobí, že zdroj dat Oracle 8i vrátí "08.01.07.04.01". SQL Server používá typický formát Microsoft "nn.nn.nnnn".<br /><br /> V některých případech DataSourceProductVersion a DataSourceProductVersionNormalized bude stejná hodnota. V případě OLE DB a ODBC budou vždy stejné jako na stejné volání funkce v podkladovém nativním rozhraní API.|  
|Sesazeníchování|<xref:System.Data.Common.GroupByBehavior>|Určuje vztah mezi sloupci v klauzuli GROUP BY a neagregovanými sloupci v seznamu výběru.|  
|IdentifikátorPattern|řetězec|Regulární výraz, který odpovídá identifikátoru a má hodnotu shody identifikátoru. Například "[A-Za-z0-9_#$]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Označuje, zda jsou identifikátory, které nejsou uvozovkami, považovány za rozlišující malá a velká písmena či nikoli.|  
|OrderbyColumnsinSelect|bool|Určuje, zda sloupce v klauzuli ORDER BY musí být v seznamu výběru. Hodnota true označuje, že musí být v seznamu select, hodnota false označuje, že nemusí být v seznamu výběru.|  
|ParametrMarkerFormat|řetězec|Formátovací řetězec, který představuje způsob formátování parametru.<br /><br /> Pokud jsou pojmenované parametry podporovány zdrojem dat, první zástupný symbol v tomto řetězci by měl být tam, kde by měl být formátován název parametru.<br /><br /> Například pokud zdroj dat očekává, že parametry budou pojmenovány a předponou{0}s ':' by to bylo ": ". Při formátování s názvem parametru "p1" je výsledný řetězec ":p1".<br /><br /> Pokud zdroj dat očekává, že parametry budou\@předponové s " ', ale{0}názvy je již obsahují, bude\@to " ',\@a výsledek formátování parametru s názvem " p1 " by jednoduše byl " p1 ".<br /><br /> Pro zdroje dat, které neočekávají pojmenované parametry a očekávají použití znaku ?' formát ovací řetězec lze zadat jako jednoduše '?', který by ignorovat název parametru. Pro OLE DB vrátíme '?'.|  
|ParametrMarkerPattern|řetězec|Regulární výraz, který odpovídá značce parametru. Bude mít hodnotu shody názvu parametru, pokud existuje.<br /><br /> Pokud jsou například pojmenované parametry\@podporovány znakem " úvodního zákazníka, který bude zahrnut\@do názvu parametru, bude to: "( [A-Za-z0-9_$#]*".<br /><br /> Pokud jsou však pojmenované parametry podporovány znakem ':' jako znakem úvodního a není součástí názvu parametru, bude to: ":([A-Za-z0-9_$#]\*)".<br /><br /> Samozřejmě, pokud zdroj dat nepodporuje pojmenované parametry, bude to jednoduše "?".|  
|ParametrNameMaxLength|int|Maximální délka názvu parametru ve znacích. Visual Studio očekává, že pokud jsou podporovány názvy parametrů, minimální hodnota pro maximální délku je 30 znaků.<br /><br /> Pokud zdroj dat nepodporuje pojmenované parametry, tato vlastnost vrátí nulu.|  
|ParametrNamePattern|řetězec|Regulární výraz, který odpovídá názvům platných parametrů. Různé zdroje dat mají různá pravidla týkající se znaků, které mohou být použity pro názvy parametrů.<br /><br /> Visual Studio očekává, že pokud jsou podporovány názvy parametrů, znaky "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" jsou minimální podporovanou sadou znaků, které jsou platné pro názvy parametrů.|  
|QuotedIdentifierPattern|řetězec|Regulární výraz, který odpovídá identifikátoru v uvozovkách a má hodnotu shody samotného identifikátoru bez uvozovek. Pokud například zdroj dat použil dvojité uvozovky k identifikaci identifikátorů v\\uvozovkách, bude to: "(([^"]&#124;\\"\\")*)".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Označuje, zda jsou identifikátory v uvozovkách považovány za rozlišující malá a velká písmena či nikoli.|  
|Oddělovač příkazuVzor|řetězec|Regulární výraz, který odpovídá oddělovači prohlášení.|  
|StringLiteralPattern|řetězec|Regulární výraz, který odpovídá literálu řetězce a má hodnotu shody samotného literálu. Pokud například zdroj dat použil k identifikaci řetězců jednoduché uvozovky, bude to: "('([^']&#124;')*'""|  
|PodporovanéJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Určuje, jaké typy příkazů spojení SQL jsou zdrojem dat podporovány.|  
  
## <a name="datatypes"></a>Datové typy  
 Tato kolekce schématu zveřejňuje informace o datových typech, které jsou podporovány databází, ke které je aktuálně připojen zprostředkovatel spravovaný rozhraní .NET Framework.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|TypeName|řetězec|Název datového typu specifické pro zprostředkovatele.|  
|Typ poskytovateleDbType|int|Hodnota typu specifické pro zprostředkovatele, která by měla být použita při zadávání typu parametru. Například SqlDbType.Money nebo OracleType.Blob.|  
|Columnsize|long|Délka nečíselného sloupce nebo parametru odkazuje buď na maximální nebo délku definovanou pro tento typ zprostředkovatelem.<br /><br /> Pro znaková data se jedná o maximální nebo definovanou délku v jednotkách definovanou zdrojem dat. Oracle má koncept určení délky a potom určení skutečné velikosti úložiště pro některé typy dat znaků. To definuje pouze délku v jednotkách pro Oracle.<br /><br /> Pro datové typy data-čas se jedná o délku reprezentace řetězce (za předpokladu maximální povolené přesnosti komponenty vteřin ve zlomcích).<br /><br /> Pokud je datový typ číselný, jedná se o horní mez maximální přesnosti datového typu.|  
|Vytvořitformát|řetězec|Formátovací řetězec, který představuje, jak přidat tento sloupec do příkazu definice dat, například VYTVOŘIT TABULKU. Každý prvek v poli CreateParameter by měl být reprezentován "značkou parametru" ve formátovacím řetězci.<br /><br /> Například datový typ SQL DECIMAL potřebuje přesnost a měřítko. V tomto případě by formátovací řetězec byl{0}{1}"DECIMAL( , .".|  
|CreateParameters|řetězec|Parametry vytvoření, které musí být zadány při vytváření sloupce tohoto datového typu. Každý parametr vytvoření je uveden v řetězci, oddělené čárkou v pořadí, ve které mají být dodány.<br /><br /> Například datový typ SQL DECIMAL potřebuje přesnost a měřítko. V tomto případě by parametry vytvoření měly obsahovat řetězec "přesnost, měřítko".<br /><br /> V příkazu text vytvořit decimal sloupec s přesností 10 a měřítko 2, hodnota CreateFormat sloupec{0}{1}může být DECIMAL( , )" a kompletní specifikace typu by DECIMAL(10,2).|  
|DataType|řetězec|Název typu rozhraní .NET Framework datového typu.|  
|Jeautoincrementable|bool|true – Hodnoty tohoto datového typu mohou být automatické přírůstky.<br /><br /> false – Hodnoty tohoto datového typu nemusí být automatické zvýšení.<br /><br /> Všimněte si, že to pouze označuje, zda sloupec tohoto datového typu může být automatické zvýšení, ne že všechny sloupce tohoto typu jsou automatické zvýšení.|  
|IsBestMatch|bool|true – Datový typ se nejlépe shoduje se všemi datovými typy v úložišti dat a datovým typem rozhraní .NET Framework označeným hodnotou ve sloupci DataType.<br /><br /> false – datový typ není nejvhodnější.<br /><br /> Pro každou sadu řádků, ve kterých je hodnota sloupce DataType stejná, je sloupec IsBestMatch nastaven na hodnotu true pouze v jednom řádku.|  
|Iscasesensitive|bool|true – datový typ je typ znaku a rozlišuje malá a velká písmena.<br /><br /> false – datový typ není typ znaku nebo není rozlišována malá a velká písmena.|  
|IsFixedLength|bool|true – Sloupce tohoto datového typu vytvořené jazykem definice dat (DDL) budou mít pevnou délku.<br /><br /> false – Sloupce tohoto datového typu vytvořené DDL budou mít proměnnou délku.<br /><br /> DBNull.Value – Není známo, zda zprostředkovatel bude mapovat toto pole se sloupcem s pevnou délkou nebo proměnnou délkou.|  
|IsFixedPrecisionScale|bool|true – Datový typ má pevnou přesnost a měřítko.<br /><br /> false – datový typ nemá pevnou přesnost a měřítko.|  
|Islong (IsLong)|bool|true – datový typ obsahuje velmi dlouhá data; definice velmi dlouhých údajů je specifická pro poskytovatele.<br /><br /> false – datový typ neobsahuje příliš dlouhá data.|  
|Isnullable|bool|true – datový typ lze zrušit.<br /><br /> false – datový typ nelze utajit.<br /><br /> DBNull.Value – Není známo, zda datový typ je nullable.|  
|Jevyhledatelný|bool|true – datový typ lze použít v klauzuli WHERE s libovolným operátorem s výjimkou predikátu LIKE.<br /><br /> false – datový typ nelze použít v klauzuli WHERE s žádným operátorem s výjimkou predikátu LIKE.|  
|IsSearchableWithLike|bool|true – Datový typ lze použít s predikátem LIKE<br /><br /> false – datový typ nelze použít s predikátem LIKE.|  
|IsUnsigned|bool|true – Datový typ je nepodepsaný.<br /><br /> false – datový typ je podepsán.<br /><br /> DBNull.Value – nevztahuje se na datový typ.|  
|Maximální měřítko|short|Pokud je typový indikátor číselný typ, jedná se o maximální počet číslic povolených vpravo od desetinné čárky. V opačném případě je dbnull.Value.|  
|MinimumScale|short|Pokud je typový indikátor číselný typ, jedná se o minimální počet číslic povolených vpravo od desetinné čárky. V opačném případě je dbnull.Value.|  
|IsConcurrencyType|bool|true – datový typ je aktualizován databází při každé změně řádku a hodnota sloupce se liší od všech předchozích hodnot<br /><br /> false – datový typ je aktualizován databází při každé změně řádku<br /><br /> DBNull.Value – databáze nepodporuje tento typ datového typu|  
|IsLiteralPodporované|bool|true – datový typ lze vyjádřit jako doslovný<br /><br /> false – datový typ nelze vyjádřit jako literál|  
|LiteralPrefix|řetězec|Předpona aplikovaná na daný literál.|  
|LiteralSuffix|řetězec|Přípona aplikovaná na daný literál.|  
|NativeDataType|Řetězec|NativeDataType je sloupec specifický pro prostředí OLE DB pro vystavení typu OLE DB datového typu .|  
  
## <a name="restrictions"></a>Omezení  
 Tato kolekce schématu odhalila informace o omezeních podporovaných spravovaným zprostředkovatelem rozhraní .NET Framework, který se aktuálně používá k připojení k databázi.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|CollectionName|řetězec|Název kolekce, která se vztahuje na tato omezení.|  
|Název_omezení|řetězec|Název omezení v kolekci.|  
|OmezeníVýchozí|řetězec|Ignorovány.|  
|Číslo omezení|int|Skutečné umístění v kolekcích omezení, které toto konkrétní omezení spadá do.|  
  
## <a name="reservedwords"></a>Vyhrazená Slova  
 Tato kolekce schématu zveřejňuje informace o slova, která jsou vyhrazena v databázi, která rozhraní .NET Framework spravovaného zprostředkovatele, který je aktuálně připojen k.  
  
|ColumnName|DataType|Popis|  
|----------------|--------------|-----------------|  
|ReservedWord|řetězec|Vyhrazené slovo specifické pro zprostředkovatele.|  
  
## <a name="see-also"></a>Viz také

- [Načítání informací o databázovém schématu](retrieving-database-schema-information.md)
- [Příkaz GetSchema a kolekce schémat](getschema-and-schema-collections.md)
- [Přehled ADO.NET](ado-net-overview.md)
