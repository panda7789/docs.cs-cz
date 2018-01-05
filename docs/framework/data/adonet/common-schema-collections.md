---
title: "Společné schéma kolekce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2b3d1a42430a02e4b3dd4a715ef27acd3e46b8ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="common-schema-collections"></a>Společné schéma kolekce
Společné schéma kolekce jsou kolekce schéma, které jsou implementovány každou zprostředkovatelů spravované rozhraní .NET Framework. Můžete zadat dotaz rozhraní .NET Framework spravovaného zprostředkovatele určit seznam podporovaných schématu kolekcí voláním **GetSchema** metoda bez argumentů nebo názvem schématu kolekce "MetaDataCollections". Tato možnost vrátí <xref:System.Data.DataTable> seznam podporovaných schéma kolekce, počet omezení, které každý podporují a počet identifikátor částí, které používají. Tyto kolekce popisují všechny požadované sloupce. Poskytovatelé jsou volně přidat další sloupce, pokud si přejí. Například `SqlClient` a `OracleClient` přidejte název parametru do kolekce omezení.  
  
 Pokud zprostředkovatele se nepodařilo určit hodnotu požadovaný sloupec, vrátí hodnotu null.  
  
 Další informace o používání **GetSchema** metody, najdete v části [GetSchema a kolekcemi schémat](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Tato kolekce schémat zpřístupní informace o všech kolekcí schémat nepodporuje rozhraní .NET Framework spravovaného poskytovatele, který je aktuálně používána pro připojení k databázi.  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|Název_kolekce|odkazy řetězců|Název kolekce, které mají být předány **GetSchema** metoda vrátí kolekci.|  
|NumberOfRestrictions|int|Počet omezení, která může být určen pro kolekci.|  
|NumberOfIdentifierParts|int|Počet částí v názvu objektu složené identifikátor a databáze. Například v systému SQL Server by to byl pro tabulky 3 a 4 pro sloupce. V Oracle je pro tabulky 2 a 3 pro sloupce.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 Tato kolekce schémat zpřístupní informace o zdroji dat, který rozhraní .NET Framework je aktuálně spravovaného zprostředkovatele připojení k.  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|odkazy řetězců|Regulární výraz tak, aby odpovídaly složené oddělovače v složené identifikátor. Například "\\." (pro SQL Server) nebo "@&#124; \\." (pro Oracle).<br /><br /> Složené identifikátor je obvykle co se používá pro název databázového objektu, například: pubs.dbo.authors nebo pubs@dbo.authors.<br /><br /> Pro systém SQL Server, použijte regulární výraz "\\.". Pro OracleClient, použijte "@&#124; \\.".<br /><br /> Pro použití rozhraní ODBC Catalog_name_seperator.<br /><br /> Pro OLE DB pomocí DBLITERAL_CATALOG_SEPARATOR nebo DBLITERAL_SCHEMA_SEPARATOR.|  
|DataSourceProductName|odkazy řetězců|Název produktu přístup poskytovatele, jako je například "Oracle" nebo "SQLServer".|  
|DataSourceProductVersion|odkazy řetězců|Určuje verzi produktu přístup poskytovatele, v nativním formátu zdroje dat a není ve formátu Microsoft.<br /><br /> V některých případech DataSourceProductVersion a DataSourceProductVersionNormalized se stejnou hodnotu. V případě technologie OLE DB a rozhraní ODBC tyto bude vždy stejná jsou namapované na stejný volání funkce v základní nativní rozhraní API.|  
|DataSourceProductVersionNormalized|odkazy řetězců|Normalizované verze pro data zdrojové, tak, aby ji můžete porovnat s `String.Compare()`. Formát tohoto objektu je konzistentní pro všechny verze zprostředkovatele, který má zabránit verze 10 řazení mezi verze 1 a verze 2.<br /><br /> Zprostředkovatel Oracle například používá formát "nn.nn.nn.nn.nn" pro jeho normalizované verze, což způsobí, že zdroj dat Oracle 8i vrátit "08.01.07.04.01". Typický formát "nn.nn.nnnn" Microsoft používá systém SQL Server.<br /><br /> V některých případech DataSourceProductVersion a DataSourceProductVersionNormalized se stejnou hodnotu. V případě technologie OLE DB a rozhraní ODBC to bude vždy stejná jsou namapované na stejný volání funkce v základní nativní rozhraní API.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|Určuje vztah mezi sloupce v klauzuli GROUP BY a -agregovat sloupců v seznamu select.|  
|IdentifierPattern|odkazy řetězců|Regulární výraz, který odpovídá identifikátor a má hodnotu shody identifikátoru. Například "[A-Za-z0-9_ #$]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Určuje, zda není v uvozovkách identifikátory jsou považovány jako malá a velká písmena, nebo ne.|  
|OrderByColumnsInSelect|bool|Určuje, zda sloupce v klauzuli ORDER BY musí být v seznamu select. Hodnota true označuje, že jsou nemusí být v seznamu select hodnota false určuje, že nemusí být v seznamu select.|  
|ParameterMarkerFormat|odkazy řetězců|Řetězec formátu, který představuje způsob formátování parametr.<br /><br /> Pokud pojmenované parametry jsou podporovány ve zdroji dat, musí být první zástupný symbol v tomto řetězci kde musí být formátována název parametru.<br /><br /> Například, pokud zdroj dat očekává parametry s názvem a předponu ':' bude ": {0}". Pokud to formátování s názvem parametru "p1" výsledná řetězec je ": p1".<br /><br /> Pokud zdroj dat očekává parametry, které mu předcházet text ' @', ale názvy již zahrnují {0}' to může být a výsledek formátování parametr s názvem "@p1"by být jednoduše"@p1".<br /><br /> Zdroje dat, které nemají očekávat pojmenované parametry a očekávat použití '?' znak, řetězec formátu lze zadat jako jednoduše '?', který by ignorovat název parametru. Pro OLE DB vrátíme '?'.|  
|ParameterMarkerPattern|odkazy řetězců|Regulární výraz, který odpovídá parametru značku. Bude mít hodnotu shody názvu parametru, pokud existuje.<br /><br /> Například, pokud jsou podporovány pojmenované parametry ' @' úvodní znak, který bude obsažen v názvu parametru by to byl: "(@[A-Za-z0-9_$ #] *)".<br /><br /> Ale pokud pojmenované parametry jsou podporovány ':' jako úvodní znak a není součástí názvu parametru, bude: ": ([A-Za-z0-9_$ #]\*)".<br /><br /> Samozřejmě pokud zdroj dat nepodporuje pojmenované parametry, jednoduše bude "?".|  
|ParameterNameMaxLength|int|Maximální délka názvu parametru ve znacích. Visual Studio očekává, že pokud jsou podporovány názvy parametrů, minimální hodnota maximální délky se 30 znaků.<br /><br /> Pokud zdroj dat nepodporuje pojmenované parametry, vrátí tato vlastnost hodnotu 0.|  
|ParameterNamePattern|odkazy řetězců|Regulární výraz, který odpovídá názvy platný parametr. Různé datové zdroje mají různá pravidla týkající se znaky, které mohou být použity pro názvy parametrů.<br /><br /> Visual Studio očekává, že pokud jsou podporovány názvy parametrů, jsou znaky "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" minimální podporované sadu znaků, které jsou platné pro názvy parametrů.|  
|QuotedIdentifierPattern|odkazy řetězců|Regulární výraz, který odpovídá identifikátor uvozovkách a má hodnotu shody identifikátoru samotné bez uvozovek. Například pokud zdroj dat použije uvozovky k identifikaci identifikátory v uvozovkách, bude: "(([^\\"] &#124;\\" \\")*)".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Určuje, zda jsou nebo nejsou považovány jako malá a velká písmena identifikátory v uvozovkách.|  
|StatementSeparatorPattern|odkazy řetězců|Regulární výraz, který odpovídá příkaz oddělovače.|  
|StringLiteralPattern|odkazy řetězců|Regulární výraz, který odpovídá řetězcový literál a má hodnotu shodu literál sám sebe. Například pokud zdroj dat použije k identifikaci řetězce jedním uvozovky, bude: "(" ([^'] &#124; ") *')"'|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Určuje, jaké typy příkazů SQL spojení jsou podporovány datovým zdrojem.|  
  
## <a name="datatypes"></a>Datové typy  
 Toto schéma kolekce zpřístupňuje informace o datové typy, které jsou podporovány v databázi, rozhraní .NET Framework spravovaná zprostředkovatele je aktuálně připojen k.  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|TypeName|odkazy řetězců|Název typu dat specifický pro zprostředkovatele.|  
|ProviderDbType|int|Hodnota typu specifický pro zprostředkovatele, který se má použít při zadávání parametr typu. Například SqlDbType.Money nebo OracleType.Blob.|  
|ColumnSize|long|Délka jiné než číselné sloupec nebo parametr odkazuje na maximální nebo délka definované pro tento typ poskytovatele.<br /><br /> Znaková data je maximální nebo definované délka v jednotkách, které jsou definované ve zdroji dat. Oracle obsahuje koncepci zadání délkou a potom zadáte velikost skutečné úložiště pro některé znakové datové typy. To definuje pouze v jednotkách pro databázi Oracle.<br /><br /> Pro data a času datové typy to je délka řetězcová reprezentace (za předpokladu, že maximální povolené přesnost komponentu zlomků sekund).<br /><br /> Pokud je číselný datový typ, je to horní mez na maximální přesnost datového typu.|  
|CreateFormat|odkazy řetězců|Řetězec formátu, který představuje jak přidat tento sloupec prohlášení definice dat, jako je například CREATE TABLE. Každý prvek v poli pomocí metody CreateParameter by měl být zobrazen "značku parametr" v řetězci formátu.<br /><br /> Například SQL datový typ DESETINNÉ potřebuje přesností a měřítkem. V takovém případě bude řetězec formátu "DECIMAL({0},{1})".|  
|CreateParameters|odkazy řetězců|Vytvoření parametry, které se musí zadat při vytváření sloupec datového typu. Každý parametr vytvoření je uvedena v řetězci, oddělený čárkou v pořadí, ve kterém se mají zadat.<br /><br /> Například SQL datový typ DESETINNÉ potřebuje přesností a měřítkem. Vytvoření parametry v takovém případě by mělo obsahovat řetězec "přesnost, měřítko".<br /><br /> V textovém příkazu k vytvoření DECIMAL sloupce s přesností 10 a měřítkem 2, může být hodnota sloupce CreateFormat DECIMAL({0},{1}) "a specifikace dokončení typu by DECIMAL(10,2).|  
|Datový typ|odkazy řetězců|Název typu rozhraní .NET Framework datového typu.|  
|IsAutoincrementable|bool|true – hodnoty tohoto typu dat může být automaticky rostoucí.<br /><br /> false – hodnoty tohoto typu dat nemusí být automaticky rostoucí.<br /><br /> Všimněte si, že to jenom Určuje, zda sloupec datového typu může být automaticky roste, ne to, jestli všechny sloupce tohoto typu jsou automaticky rostoucí.|  
|IsBestMatch|bool|true – datový typ je nejlepší shodu mezi všech typů dat v úložišti dat a datový typ rozhraní .NET Framework uvedené hodnotou ve sloupci datového typu.<br /><br /> false – datový typ není nejlepší shodu.<br /><br /> Pro každou sadu řádků, ve kterých je hodnota sloupce datového typu stejné IsBestMatch sloupec je nastavený na hodnotu true pouze v jednom řádku.|  
|IsCaseSensitive|bool|true – datový typ je typ znak a je malá a velká písmena.<br /><br /> false – datový typ není typu znak nebo není malá a velká písmena.|  
|IsFixedLength|bool|true – sloupce tento datový typ vytvořené jazyk definice dat (DDL) budou mít pevnou délkou.<br /><br /> false – sloupce tento typ dat, které vytvoří DDL bude s proměnnou délkou.<br /><br /> DBNull.Value—It není označuje, zda zprostředkovatel namapujete toto pole s pevnou délkou nebo proměnnou délkou sloupec.|  
|IsFixedPrecisionScale|bool|true – datový typ má pevnou přesnost a měřítko.<br /><br /> false – datový typ nemá pevnou přesnost a měřítko.|  
|IsLong|bool|true – datový typ obsahuje velmi dlouhé data; Definice velmi dlouhé dat je specifický pro zprostředkovatele.<br /><br /> false – datový typ neobsahuje data velmi náročná.|  
|Vlastnost isNullable|bool|true – je datový typ s možnou hodnotou Null.<br /><br /> false – datový typ není null.<br /><br /> DBNull.Value—It není označuje, zda je datový typ s možnou hodnotou Null.|  
|IsSearchable|bool|true – datový typ lze použít v klauzuli WHERE se žádné operátor s výjimkou predikátu LIKE.<br /><br /> false – datový typ nelze použít v klauzuli WHERE s žádné operátor s výjimkou predikátu LIKE.|  
|IsSearchableWithLike|bool|true – datový typ lze použít s LIKE predikátu.<br /><br /> false – datový typ nelze použít s predikátu LIKE.|  
|IsUnsigned|bool|true – datový typ není podepsán.<br /><br /> false – datový typ je podepsaný.<br /><br /> Použít na datový typ DBNull.Value—Not.|  
|MaximumScale|short|Pokud typ je číselného typu, jedná se maximální povolený počet číslic vpravo od desetinné čárky. Jinak je to DBNull.Value.|  
|MinimumScale|short|Pokud typ je číselného typu, to je minimální počet číslic vpravo od desetinné čárky. Jinak je to DBNull.Value.|  
|IsConcurrencyType|bool|true – datový typ se aktualizuje databázi pokaždé, když se změní na řádku a hodnota sloupce se liší od všechny předchozí hodnoty<br /><br /> false – datový typ je poznámka aktualizovat databázi pokaždé, když se změní na řádek<br /><br /> DBNull.Value – databáze nepodporuje tento typ datového typu|  
|IsLiteralSupported|bool|true – datový typ může být vyjádřený jako literál<br /><br /> false – datový typ nemůže být vyjádřena jako literál|  
|LiteralPrefix|odkazy řetězců|Předpona u daného literál.|  
|LiteralSuffix|odkazy řetězců|Přípona u daného literál.|  
|NativeDataType|String|NativeDataType je konkrétní sloupec technologie OLE DB pro vystavení typ OLE DB datového typu.|  
  
## <a name="restrictions"></a>Omezení  
 Tato kolekce schémat zveřejněné informace o omezení, které jsou podporovány pomocí spravovaného poskytovatele rozhraní .NET Framework, který je aktuálně používána pro připojení k databázi.  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|Název_kolekce|odkazy řetězců|Název kolekce, která se týkají těchto omezení.|  
|RestrictionName|odkazy řetězců|Název omezení v kolekci.|  
|RestrictionDefault|odkazy řetězců|Ignorovat.|  
|RestrictionNumber|int|Skutečné umístění v omezení kolekce, která spadá toto konkrétní omezení.|  
  
## <a name="reservedwords"></a>ReservedWords  
 Tato kolekce schémat zpřístupní informace o slova, která jsou vyhrazené databázi, která zprostředkovatele, který je aktuálně připojen k spravované rozhraní .NET Framework.  
  
|columnName|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|ReservedWord|odkazy řetězců|Specifické pro poskytovatele vyhrazené slovo.|  
  
## <a name="see-also"></a>Viz také  
 [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [Příkaz GetSchema a kolekce schémat](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
