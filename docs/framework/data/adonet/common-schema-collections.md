---
title: Společné kolekce schémat
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: 29ccd2af4268a86ae4c2047ad2523f68b0f6489e
ms.sourcegitcommit: a474397fd4de822f0d878d86d907e49763872b0b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "37072121"
---
# <a name="common-schema-collections"></a>Společné kolekce schémat
Společné kolekce schémat jsou kolekce schémat, které jsou implementovány ve všech zprostředkovatelů spravovaným rozhraním .NET Framework. Můžete dát dotaz na zprostředkovatele rozhraní .NET Framework spravované určit seznam kolekcí nepodporuje schéma voláním **GetSchema** metody bez argumentů nebo názvem kolekce schématu "MetaDataCollections". Vrátí <xref:System.Data.DataTable> seznam kolekcí nepodporuje schéma, počet omezení, které každá podporují a počet identifikátor částí, které používají. Tyto kolekce popisují všechny požadované sloupce. Poskytovatelé jsou zdarma Pokud chtějí přidat i další sloupce. Například `SqlClient` a `OracleClient` přidejte název parametru kolekce omezení.  
  
 Pokud zprostředkovatele nemůže určit hodnotu požadovaný sloupec, vrátí hodnotu null.  
  
 Další informace o používání **GetSchema** metody, naleznete v tématu [GetSchema a kolekce schémat](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Tato kolekce schémat zveřejňuje informace o všech kolekce schémat podporován spravovaného zprostředkovatele .NET Framework, který se aktuálně používá pro připojení k databázi.  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|collectionName|odkazy řetězců|Název kolekce, kterou chcete předat **GetSchema** metoda vrátí kolekci.|  
|NumberOfRestrictions|int|Počet omezení, která může být zadáno pro kolekci.|  
|NumberOfIdentifierParts|int|Počet částí v názvu objektu složené identifikátor/databáze. Například v systému SQL Server, jde 3 pro tabulky a 4 pro sloupce. V databázi Oracle bylo by pro tabulky 2 a 3 pro sloupce.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 Tato kolekce schémat zveřejňuje informace o zdroji dat, který rozhraní .NET Framework spravovaného poskytovatele je aktuálně připojení k.  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|odkazy řetězců|Regulární výraz tak, aby odpovídaly složené oddělovače ve složených identifikátor. Například "\\." (pro SQL Server) nebo "\@&#124;\\." (pro Oracle).<br /><br /> Složený identifikátor má zpravidla co se používá pro název databázového objektu, například: pubs.dbo.authors nebo pubs\@dbo.authors.<br /><br /> SQL Server, použijte regulární výraz "\\.". OracleClient, použijte "\@&#124;\\.".<br /><br /> Pro ODBC použijte Catalog_name_seperator.<br /><br /> Pro OLE DB pomocí DBLITERAL_CATALOG_SEPARATOR nebo DBLITERAL_SCHEMA_SEPARATOR.|  
|DataSourceProductName|odkazy řetězců|Název produktu přístup poskytovateli, jako je například "Oracle" nebo "Systému SQL Server".|  
|DataSourceProductVersion|odkazy řetězců|Určuje verzi produktu přístup poskytovateli, v nativním formátu zdroje dat a není ve formátu Microsoft.<br /><br /> V některých případech bude DataSourceProductVersion a DataSourceProductVersionNormalized stejnou hodnotu. V případě technologie OLE DB a rozhraní ODBC vždy budou stejné jako jsou namapovány na stejný volání funkce v základní nativní rozhraní API.|  
|DataSourceProductVersionNormalized|odkazy řetězců|Normalizovaná verzi pro data zdroje, tak, že se má porovnat s `String.Compare()`. Formát tohoto objektu je konzistentní pro všechny verze poskytovatel, kterého chcete zabránit verze 10 řazení mezi verze 1 a 2.<br /><br /> Například poskytovatele dat Oracle používá formát "nn.nn.nn.nn.nn" pro jeho normalizovaná verzi, která způsobí, že zdroj dat Oracle 8i vrátit "08.01.07.04.01". Typický formát "nn.nn.nnnn" Microsoft používá systém SQL Server.<br /><br /> V některých případech bude DataSourceProductVersion a DataSourceProductVersionNormalized stejnou hodnotu. V případě technologie OLE DB a ODBC to vždy budou stejné jako jsou namapovány na stejný volání funkce v základní nativní rozhraní API.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|Určuje vztah mezi sloupce v klauzuli Group by a neagregované sloupce v seznamu select.|  
|IdentifierPattern|odkazy řetězců|Regulární výraz, který odpovídá identifikátoru a má hodnotu shody identifikátoru. Například "[A-Za-z0-9_ #$]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Určuje, zda jsou považovány identifikátory v uvozovkách bez jako malá a velká písmena nebo ne.|  
|OrderByColumnsInSelect|bool|Určuje, zda sloupců v klauzuli ORDER BY musí být v seznamu select. Hodnota true označuje, že se musí být v seznamu select, hodnota false označuje, že nemusí být ve výběrovém seznamu.|  
|ParameterMarkerFormat|odkazy řetězců|Řetězec formátu, který představuje způsob formátování parametru.<br /><br /> Pokud pojmenované parametry jsou podporovány ve zdroji dat, by měla být první zástupný symbol v tomto řetězci, kde by se měly naformátovat název parametru.<br /><br /> Například, pokud zdroj dat očekává, že parametry s názvem a s předponou ":" to může být ":{0}". Když toto formátování s názvem parametru "p1" výsledný řetězec je ": p1".<br /><br /> Pokud zdroj dat očekává, že parametry s předponou "\@", ale název je již obsahuje, to může být "{0}" a výsledkem formátování parametr s názvem "\@p1" by být jednoduše "\@p1".<br /><br /> Pro zdroje dat, které nemají očekávat pojmenované parametry a očekávané použití "?" znak, řetězec formátu se dá nastavit jako "?", která bude ignorovat název parametru. Pro OLE DB vrátíme "?".|  
|ParameterMarkerPattern|odkazy řetězců|Regulární výraz, který odpovídá parametru značky. Bude mít hodnotu shody názvu parametru, pokud existuje.<br /><br /> Například, pokud pojmenované parametry jsou podporovány pomocí "\@" úvodní znak, který bude obsažen v názvu parametru by to byl: "(\@[A-Za-z0-9_$ #] *)".<br /><br /> Ale pokud pojmenované parametry jsou podporovány ":" jako úvodní znak a není součástí název parametru, to může být: ": ([A-Za-z0-9_$ #]\*)".<br /><br /> Samozřejmě pokud zdroj dat nepodporuje pojmenované parametry, jednoduše by to "?".|  
|ParameterNameMaxLength|int|Maximální délka názvu parametru ve znacích. Visual Studio očekává, že pokud názvy parametrů jsou podporovány, minimální hodnota pro maximální počet znaků je 30 znaků.<br /><br /> Pokud zdroj dat nepodporuje pojmenované parametry, tato vlastnost vrátí hodnotu 0.|  
|ParameterNamePattern|odkazy řetězců|Regulární výraz, který se shoduje s názvy platná hodnota parametru. Různé datové zdroje mají různá pravidla týkající se znaky, které mohou být použity pro názvy parametrů.<br /><br /> Visual Studio očekává, že pokud názvy parametrů jsou podporovány, jsou znaky "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" minimální podporované množinu znaků, které jsou platné pro názvy parametrů.|  
|QuotedIdentifierPattern|odkazy řetězců|Regulární výraz, který odpovídá identifikátoru v uvozovkách a má hodnotu shody identifikátoru samotného bez uvozovek. Například pokud zdroj dat používá k identifikaci identifikátory v uvozovkách dvojité uvozovky, jde: "(([^\\"]&#124;\\"\\") *) ".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Určuje, zda jsou považovány identifikátory v uvozovkách jako malá a velká písmena nebo ne.|  
|StatementSeparatorPattern|odkazy řetězců|Regulární výraz, který odpovídá oddělovač.|  
|StringLiteralPattern|odkazy řetězců|Regulární výraz, který odpovídá řetězcový literál a má hodnotu shody literálu samotný. Například pokud zdroj dat používá k identifikaci řetězců nabídek jedním, jde: "('([^']&#124;'') *") ".|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Určuje, jaké typy příkazů SQL spojení jsou podporovány ve zdroji dat.|  
  
## <a name="datatypes"></a>Datové typy  
 Tato kolekce zveřejňuje informace o schématu o datových typech, které jsou podporovány v databázi, že rozhraní .NET Framework spravovaný zprostředkovatel je aktuálně připojena k.  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|TypeName|odkazy řetězců|Název typu dat specifickým pro zprostředkovatele.|  
|ProviderDbType|int|Hodnota typu specifickým pro zprostředkovatele, který se má použít při zadávání parametr typu. Například SqlDbType.Money nebo OracleType.Blob.|  
|ColumnSize|long|Délka nečíselným sloupcem nebo parametr odkazuje na maximální nebo délka definované pro tento typ zprostředkovatele.<br /><br /> Znaková data je maximální počet nebo délka definované v jednotkách, definovaný ve zdroji dat. Oracle nemá koncept určující délku a potom zadáte velikost skutečné úložiště pro některé znakové datové typy. Definuje pouze délky v jednotkách pro Oracle.<br /><br /> Pro datum a čas datové typy Toto je délka řetězcové vyjádření (za předpokladu, že maximální povolenou přesnost součást zlomků sekund).<br /><br /> Pokud je číselný datový typ, je to horní mez na maximální přesnost datového typu.|  
|CreateFormat|odkazy řetězců|Formátovací řetězec, který představuje, jak přidat příkaz pro definici dat, jako je například vytvoření tabulky v tomto sloupci. Každý prvek v poli pomocí metody CreateParameter by měla být reprezentovaná "značky parametr" v řetězci formátu.<br /><br /> Například SQL datový typ DECIMAL musí přesnost a měřítko. V takovém případě by být formátovací řetězec "DECIMAL ({0},{1})".|  
|CreateParameters|odkazy řetězců|Vytvoření parametry, které se musí zadat při vytváření sloupce datového typu. Každý parametr vytváření je uveden v řetězci, oddělte čárkami v pořadí, ve kterém se nemusí zadávat.<br /><br /> Například SQL datový typ DECIMAL musí přesnost a měřítko. Parametry vytvoření v tomto případě by měl obsahovat řetězec "přesnost, měřítko".<br /><br /> V textovém příkazu k vytvoření DESÍTKOVÉ sloupce s přesností na 10 a škálování 2, může být hodnota sloupce CreateFormat desetinné číslo ({0},{1}) "a specifikaci úplný typ by DECIMAL(10,2).|  
|Datový typ|odkazy řetězců|Název typu rozhraní .NET Framework datového typu.|  
|IsAutoincrementable|bool|true – hodnoty tohoto typu dat mohou být automatické zvyšování.<br /><br /> false – automatické zvyšování nemusí být hodnoty datového typu.<br /><br /> Všimněte si, že to pouze znamená, zda může být sloupec datového typu auto-zvyšování hodnoty, ne to, jestli jsou všechny sloupce tohoto typu zvyšování hodnoty automaticky.|  
|IsBestMatch|bool|true – datový typ je nejlepší shodu mezi všech typů dat v úložišti dat a datový typ rozhraní .NET Framework určeno hodnotou ve sloupci datového typu.<br /><br /> false – datový typ není nejlepší shodu.<br /><br /> Pro každou sadu řádků, ve kterých je hodnota datového typu sloupce stejný sloupec IsBestMatch je nastaven na hodnotu true pouze v jednom řádku.|  
|IsCaseSensitive|bool|true – datový typ je typ znak a je velká a malá písmena.<br /><br /> false – datový typ není typem znaku nebo není malá a velká písmena.|  
|Isfixedlength atributu Sqlfacetattribute|bool|true – sloupce tento typ dat, které jsou vytvořené pomocí jazyka pro definici dat (DDL) bude mít pevnou délku.<br /><br /> NEPRAVDA – tento typ dat vytvořené jazyka DDL sloupců bude s proměnnou délkou.<br /><br /> DBNull.Value—It není znám, zda zprostředkovatel bude mapovat tato pole s pevnou délkou nebo proměnné délky sloupce.|  
|IsFixedPrecisionScale|bool|true – datový typ má pevnou hodnot precision a scale.<br /><br /> false – datový typ, nemá pevnou hodnot precision a scale.|  
|IsLong|bool|true – datový typ obsahuje velmi dlouhá data. Definice velmi dlouhý dat závisí na konkrétním zprostředkovateli.<br /><br /> false – datový typ neobsahuje velmi dlouhá data.|  
|IsNullable|bool|true – datový typ může mít hodnotu Null.<br /><br /> false – datový typ není s možnou hodnotou Null.<br /><br /> DBNull.Value—It není znám, zda je datový typ s možnou hodnotou Null.|  
|IsSearchable|bool|true – datový typ je možné v klauzuli WHERE jakékoli operátor s výjimkou predikátu LIKE.<br /><br /> false – datový typ nelze použít v klauzuli WHERE jakékoli operátor s výjimkou predikátu LIKE.|  
|IsSearchableWithLike|bool|true – datový typ jde použít s predikátu LIKE<br /><br /> false – datový typ nelze použít s predikátu LIKE.|  
|IsUnsigned|bool|true – datový typ není podepsaný.<br /><br /> false – datový typ je podepsán.<br /><br /> Lze použít na datový typ DBNull.Value—Not.|  
|MaximumScale|short|Pokud indikátor typu číselného typu, toto je maximální počet číslic vpravo od desetinné čárky. V opačném případě je to DBNull.Value.|  
|MinimumScale|short|Pokud indikátor typu číselného typu, toto je minimální počet číslic vpravo od desetinné čárky. V opačném případě je to DBNull.Value.|  
|IsConcurrencyType|bool|true – datový typ aktualizována v databázi pokaždé, když se změní na řádku a hodnota sloupce se liší od všechny předchozí hodnoty<br /><br /> false – datový typ je poznámka aktualizována v databázi vždy, když se změní na řádku<br /><br /> DBNull.Value – databáze nepodporuje tento typ datového typu|  
|IsLiteralSupported|bool|true – datový typ může být vyjádřený jako literál<br /><br /> false – datový typ nemůže být vyjádřený jako literál|  
|LiteralPrefix|odkazy řetězců|Předpona u daného literál.|  
|LiteralSuffix|odkazy řetězců|Přípona u daného literál.|  
|NativeDataType|String|NativeDataType je konkrétní sloupec technologie OLE DB pro vystavení typ OLE DB datového typu.|  
  
## <a name="restrictions"></a>Omezení  
 Tato kolekce schémat zpřístupnit informace o omezení, které jsou podporovány spravovaného zprostředkovatele .NET Framework, který se aktuálně používá pro připojení k databázi.  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|collectionName|odkazy řetězců|Název kolekce, která tato omezení platí pro.|  
|RestrictionName|odkazy řetězců|Název omezení v kolekci.|  
|RestrictionDefault|odkazy řetězců|Ignorovat.|  
|RestrictionNumber|int|Skutečné umístění v omezení kolekce, která spadá toto konkrétní omezení.|  
  
## <a name="reservedwords"></a>ReservedWords  
 Tato kolekce schémat zveřejňuje informace o slova, která jsou vyhrazené databázi, kterou rozhraní .NET Framework spravovaný zprostředkovatel, který je aktuálně připojený k.  
  
|Názevsloupce|Datový typ|Popis|  
|----------------|--------------|-----------------|  
|ReservedWord|odkazy řetězců|Specifické pro zprostředkovatele vyhrazené slovo.|  
  
## <a name="see-also"></a>Viz také  
 [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [Příkaz GetSchema a kolekce schémat](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](http://go.microsoft.com/fwlink/?LinkId=217917)
