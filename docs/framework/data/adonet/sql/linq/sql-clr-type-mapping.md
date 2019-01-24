---
title: SQL-CLR Type Mapping
ms.date: 07/23/2018
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: 5c8c6456d108975ec927e28ac80c8dcca1567b46
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617340"
---
# <a name="sql-clr-type-mapping"></a>SQL-CLR Type Mapping
V technologii LINQ to SQL datový model relační databáze mapuje na objektový model vyjádřený v programovacím jazyce podle vašeho výběru. Při spuštění aplikace, technologie LINQ to SQL integrovaný jazyk dotazů v objektovém modelu převádí na SQL a odesílá je do databáze pro spuštění. Když databázi vrátí výsledky, LINQ to SQL přeloží výsledky zpět na objekty, které můžete pracovat s vlastními programovací jazyk.  
  
 Aby bylo možné přeložit data mezi objektový model a databáze, *mapování typu* musí být definovaný. Technologie LINQ to SQL využívá mapování typu tak, aby odpovídaly každý společný typ language runtime (CLR) s určitým typem systému SQL Server. Můžete definovat mapování typů a dalších informací o mapování jako je například databáze strukturu a tabulka vztahů uvnitř objektový model založený na atributu mapování. Alternativně můžete zadat informace o mapování mimo objektový model se souborem externích mapování. Další informace najdete v tématu [založených na atributech mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) a [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 Toto téma popisuje následující body:  
  
-   [Výchozí typ mapování](#DefaultTypeMapping)  
  
-   [Typ mapování matice chování za běhu](#BehaviorMatrix)  
  
-   [Rozdíly v chování modulu CLR a provedení SQL](#BehaviorDiffs)  
  
-   [Mapování výčtu](#EnumMapping)  
  
-   [Číselné mapování](#NumericMapping)  
  
-   [Text a mapování XML](#TextMapping)  
  
-   [Datum a čas mapování](#DateMapping)  
  
-   [Binární mapování](#BinaryMapping)  
  
-   [Různé mapování](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>   
## <a name="default-type-mapping"></a>Výchozí typ mapování  
 Objektový model nebo externí mapování souboru můžete vytvořit automaticky pomocí Návrháře relací objektů (O/R Designer) nebo nástroj příkazového řádku SQLMetal. Výchozí mapování typů pro tyto nástroje definovat, jaké typy CLR je možné zvolit mapovat na sloupce v databázi serveru SQL Server. Další informace o použití těchto nástrojů najdete v tématu [vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md).  
  
 Můžete také použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metodu pro vytvoření databáze SQL serveru na základě mapování informací v objektovém modelu nebo externí mapování souboru. Výchozí typ mapování <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metoda definování typu SQL Server se sloupce vytvářejí pro mapování na modul CLR typy v objektovém modelu. Další informace najdete v tématu [jak: Dynamické vytvoření databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
<a name="BehaviorMatrix"></a>   
## <a name="type-mapping-run-time-behavior-matrix"></a>Typ mapování matice chování za běhu  
 Následující diagram znázorňuje očekávané chování za běhu mapování určitého typu, když se data načítají z nebo uloží do databáze. Kromě serializaci LINQ to SQL nepodporuje mapování mezi všechna CLR nebo SQL Server data typů, které nejsou uvedeny v této matici. Další informace o podpoře serializace naleznete v tématu [binární serializace](#BinarySerialization).  
 
![SQL Server do tabulky mapování typů dat SQL CLR](media/sql-clr-type-mapping.png)

> [!NOTE]
>  Některé mapování typu může vést ke ztrátě výjimky přetečení nebo dat při překladu do nebo z databáze.  
  
### <a name="custom-type-mapping"></a>Mapování vlastních typů  
 Pomocí LINQ to SQL, nejste omezeni na výchozí mapování typu používané návrhářem relací objektů, SQLMetal a <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metoda. Můžete vytvořit vlastní typ mapování tak, že je explicitně zadáte v souboru DBML. Pak můžete použít tohoto souboru DBML vytvořit objekt modelu kódu a mapování souboru. Další informace najdete v tématu [mapování typů SQL a CLR vlastní](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
<a name="BehaviorDiffs"></a>   
## <a name="behavior-differences-between-clr-and-sql-execution"></a>Rozdíly v chování modulu CLR a provedení SQL  
 Z důvodu rozdílů v přesnosti a provádění mezi CLR a systému SQL Server může přijímat odlišné výsledky nebo vyzkoušet různé chování v závislosti na tom, kde provádět výpočty. Výpočty provádět dotazy SQL v technologii LINQ jsou ve skutečnosti přeložit do jazyka Transact-SQL a pak spustit pro databázi systému SQL Server. Výpočty provést mimo LINQ dotazy SQL jsou spuštěny v rámci modulu CLR.  
  
 Následující příklad, jsou určité rozdíly v chování mezi CLR a systému SQL Server:  
  
-   Některé typy dat systému SQL Server odlišně od datového typu ekvivalentní objednávky v CLR. Například data systému SQL Server typu `UNIQUEIDENTIFIER` jinak než typ dat CLR je seřazen <xref:System.Guid?displayProperty=nameWithType>.  
  
-   SQL Server provede některé operace porovnání řetězců jinak než CLR. V systému SQL Server chování porovnání řetězců závisí na nastavení řazení na serveru. Další informace najdete v tématu [práce s kolací](https://go.microsoft.com/fwlink/?LinkId=115330) v Online knihách systému Microsoft SQL Server.  
  
-   SQL Server může vracet různé hodnoty pro některé z namapované funkce než CLR. Například se bude lišit rovnosti funkce, protože systém SQL Server považuje dva řetězce rovny, pokud se liší pouze v prázdný znak; bude Zatímco CLR je považuje za se nesmí rovnat.  
  
<a name="EnumMapping"></a>   
## <a name="enum-mapping"></a>Mapování výčtu  
 Technologie LINQ to SQL podporuje mapování CLR <xref:System.Enum?displayProperty=nameWithType> typu na typy serveru SQL Server dvěma způsoby:  
  
-   Mapování na číselné typy SQL (`TINYINT`, `SMALLINT`, `INT`, `BIGINT`)  
  
     Při mapování modul CLR <xref:System.Enum?displayProperty=nameWithType> typu na číselný typ SQL, můžete namapovat základní celočíselnou hodnotu CLR <xref:System.Enum?displayProperty=nameWithType> k hodnotě sloupce databáze systému SQL Server. Například pokud <xref:System.Enum?displayProperty=nameWithType> s názvem `DaysOfWeek` obsahuje člen s názvem `Tue` se základní hodnotou celé číslo 3, tento člen mapuje na databázi hodnotu 3.  
  
-   Mapování typů SQL textu (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`)  
  
     Při mapování modul CLR <xref:System.Enum?displayProperty=nameWithType> typu na typ textu SQL, hodnota databáze SQL se mapuje na název modulu CLR <xref:System.Enum?displayProperty=nameWithType> členy. Například pokud <xref:System.Enum?displayProperty=nameWithType> s názvem `DaysOfWeek` obsahuje člen s názvem `Tue` se základní hodnotou celé číslo 3, tento člen mapuje na hodnotu databáze `Tue`.  
  
> [!NOTE]
>  Při mapování typů SQL textu na modul CLR <xref:System.Enum?displayProperty=nameWithType>, obsahovat jenom názvy <xref:System.Enum> členy ve sloupci pro mapovanou SQL. Jiné hodnoty nejsou podporovány v <xref:System.Enum>-mapovat sloupce SQL.  
  
 Nástroj příkazového řádku O/R Designer a SQLMetal nelze mapovat automaticky typu SQL CLR <xref:System.Enum> třídy. Toto mapování je nutné explicitně nakonfigurovat úpravou souboru DBML pro Návrháře relací objektů a SQLMetal. Další informace o mapování vlastního typu, najdete v části [mapování vlastních typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
 Protože sloupec SQL určených pro výčet budou stejného typu jako ostatní číselné a textové sloupce; Tyto nástroje jej nerozpozná záměr a výchozí mapování, jak je popsáno v následujícím [číselné mapování](#NumericMapping) a [Text a mapování XML](#TextMapping) oddíly. Další informace o generování kódu pomocí souboru DBML, v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda vytvoří číselný typ pro mapování modul CLR. sloupec SQL <xref:System.Enum?displayProperty=nameWithType> typu.  
  
<a name="NumericMapping"></a>   
## <a name="numeric-mapping"></a>Číselné mapování  
 Technologie LINQ to SQL umožňuje mapovat mnoho CLR a systému SQL Server číselné typy. Následující tabulka uvádí typy CLR, že O/R Designer a SQLMetal vybrat při vytváření objektový model nebo externí mapování souboru podle vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používané O/R Designer a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`BIT`|<xref:System.Boolean?displayProperty=nameWithType>|  
|`TINYINT`|<xref:System.Int16?displayProperty=nameWithType>|  
|`INT`|<xref:System.Int32?displayProperty=nameWithType>|  
|`BIGINT`|<xref:System.Int64?displayProperty=nameWithType>|  
|`SMALLMONEY`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`MONEY`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`DECIMAL`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`NUMERIC`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`REAL/FLOAT(24)`|<xref:System.Single?displayProperty=nameWithType>|  
|`FLOAT/FLOAT(53)`|<xref:System.Double?displayProperty=nameWithType>|  
  
 V následující tabulce jsou uvedeny výchozí mapování typu používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda k definování typů SQL sloupce, které jsou vytvořeny pro mapování pro typy CLR definovaný v objektovém modelu nebo externí mapování souboru.  
  
|Typ CLR|Výchozí SQL serveru typ používaný <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|`BIT`|  
|<xref:System.Byte?displayProperty=nameWithType>|`TINYINT`|  
|<xref:System.Int16?displayProperty=nameWithType>|`SMALLINT`|  
|<xref:System.Int32?displayProperty=nameWithType>|`INT`|  
|<xref:System.Int64?displayProperty=nameWithType>|`BIGINT`|  
|<xref:System.SByte?displayProperty=nameWithType>|`SMALLINT`|  
|<xref:System.UInt16?displayProperty=nameWithType>|`INT`|  
|<xref:System.UInt32?displayProperty=nameWithType>|`BIGINT`|  
|<xref:System.UInt64?displayProperty=nameWithType>|`DECIMAL(20)`|  
|<xref:System.Decimal?displayProperty=nameWithType>|`DECIMAL(29,4)`|  
|<xref:System.Single?displayProperty=nameWithType>|`REAL`|  
|<xref:System.Double?displayProperty=nameWithType>|`FLOAT`|  
  
 Existuje mnoho dalších číselných mapování, které můžete, ale některé může vést k přetečení nebo data ztráty výjimky při převodu do nebo z databáze. Další informace najdete v tématu [typ mapování spustit čas chování matice](#BehaviorMatrix).  
  
### <a name="decimal-and-money-types"></a>Decimal a typy peníze  
 Výchozí přesnost systému SQL Server `DECIMAL` typ (18 desítkových číslic vlevo a vpravo od desetinné čárky) je mnohem menší než přesnost CLR <xref:System.Decimal?displayProperty=nameWithType> typ, který je spárovaná s ve výchozím nastavení. To může způsobit ztrátu přesnosti při ukládání dat do databáze. Však stačí opak může dojít, pokud SQL Server `DECIMAL` typ je nakonfigurován s víc než 29 platnými číslicemi přesnosti. Pokud SQL Server `DECIMAL` typ byl nakonfigurován s větší přesností než CLR <xref:System.Decimal?displayProperty=nameWithType>, může dojít ke ztrátě přesnosti, při načítání dat z databáze.  
  
 SQL Server `MONEY` a `SMALLMONEY` typy, které jsou také spárovat s modulem CLR <xref:System.Decimal?displayProperty=nameWithType> zadejte ve výchozím nastavení, mají mnohem menší přesností, což může vést ke ztrátě výjimky přetečení nebo dat při ukládání dat do databáze.  
  
<a name="TextMapping"></a>   
## <a name="text-and-xml-mapping"></a>Text a mapování XML  
 Existují také mnoho založený na textu a typy XML, namapované pomocí LINQ to SQL. Následující tabulka uvádí typy CLR, že O/R Designer a SQLMetal vybrat při vytváření objektový model nebo externí mapování souboru podle vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používané O/R Designer a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 V následující tabulce jsou uvedeny výchozí mapování typu používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda k definování typů SQL sloupce, které jsou vytvořeny pro mapování pro typy CLR definovaný v objektovém modelu nebo externí mapování souboru.  
  
|Typ CLR|Výchozí SQL serveru typ používaný <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=nameWithType>[]|`NVARCHAR(4000)`|  
|Implementace vlastního typu `Parse()` a `ToString()`|`NVARCHAR(MAX)`|  
  
 Existuje mnoho dalších založený na textu a mapování XML můžete, ale některé může vést k přetečení nebo data ztráty výjimky při převodu do nebo z databáze. Další informace najdete v tématu [typ mapování spustit čas chování matice](#BehaviorMatrix).  
  
### <a name="xml-types"></a>Typy XML  
 SQL Server `XML` datový typ je k dispozici od verze Microsoft SQL Server 2005. SQL Server můžete namapovat `XML` datový typ, který <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>, nebo <xref:System.String>. Pokud sloupec obsahuje fragmenty XML, které nelze načíst do <xref:System.Xml.Linq.XElement>, sloupec musí být namapována na <xref:System.String> aby nedocházelo k chybám za běhu. Fragmenty XML, které musí být namapována na <xref:System.String> patří následující:  
  
-   Sekvence elementů XML  
  
-   Atributy  
  
-   Veřejné identifikátory (PÍ)  
  
-   Komentáře  
  
 I když můžete namapovat <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XDocument> k systému SQL Server, jak je znázorněno [matice chování čas spuštění mapování typu](#BehaviorMatrix), <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda nemá žádné výchozí mapování typu SQL Server pro tyto typy.  
  
### <a name="custom-types"></a>Vlastní typy  
 Pokud třída implementuje `Parse()` a `ToString()`, objekt můžete namapovat na libovolný typ textu SQL (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`, `TEXT`, `NTEXT`, `XML`). Objekt se uloží v databázi odesláním hodnoty vrácené `ToString()` k sloupci z namapované databáze. Objekt je znovu vytvořena vyvoláním `Parse()` na řetězec vrácený funkcí databáze.  
  
> [!NOTE]
>  Technologie LINQ to SQL nepodporuje serializaci pomocí <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.  
  
<a name="DateMapping"></a>   
## <a name="date-and-time-mapping"></a>Datum a čas mapování  
 Pomocí LINQ to SQL můžete namapovat mnoho typů systému SQL Server data a času. Následující tabulka uvádí typy CLR, že O/R Designer a SQLMetal vybrat při vytváření objektový model nebo externí mapování souboru podle vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používané O/R Designer a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 V následující tabulce jsou uvedeny výchozí mapování typu používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda k definování typů SQL sloupce, které jsou vytvořeny pro mapování pro typy CLR definovaný v objektovém modelu nebo externí mapování souboru.  
  
|Typ CLR|Výchozí SQL serveru typ používaný <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 Existuje mnoho dalších datum a čas mapování, které můžete, ale některé může vést k přetečení nebo data ztráty výjimky při převodu do nebo z databáze. Další informace najdete v tématu [typ mapování spustit čas chování matice](#BehaviorMatrix).  
  
> [!NOTE]
>  Typy serveru SQL Server `DATETIME2`, `DATETIMEOFFSET`, `DATE`, a `TIME` jsou k dispozici od verze Microsoft SQL Server 2008. Technologie LINQ to SQL podporuje mapování na tyto nové typy od verze rozhraní .NET Framework verze 3.5 SP1.  
  
### <a name="systemdatetime"></a>System.Datetime  
 Rozsah a přesnost modulu CLR <xref:System.DateTime?displayProperty=nameWithType> typ je větší než rozsah a přesnost systému SQL Server `DATETIME` typ, který je výchozím typem mapování pro <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody. Chcete-li výjimky související s daty mimo rozsah `DATETIME`, použijte `DATETIME2`, která je k dispozici od verze Microsoft SQL Server 2008. `DATETIME2` rozsah a přesnost modulu CLR odpovídá <xref:System.DateTime?displayProperty=nameWithType>.  
  
 SQL Server data nemají žádný koncept <xref:System.TimeZone>, funkce, která je velmi podporována v modulu CLR. <xref:System.TimeZone> hodnoty jsou uloženy, protože je databáze, aniž byste <xref:System.TimeZone> převod, bez ohledu na původní <xref:System.DateTimeKind> informace. Když <xref:System.DateTime> hodnoty jsou načteny z databáze, jejich hodnoty se načítají podle do <xref:System.DateTime> s <xref:System.DateTimeKind> z <xref:System.DateTimeKind.Unspecified>. Další informace o podporované <xref:System.DateTime?displayProperty=nameWithType> metody, naleznete v tématu [metody System.DateTime](../../../../../../docs/framework/data/adonet/sql/linq/system-datetime-methods.md).  
  
### <a name="systemtimespan"></a>System.TimeSpan  
 Microsoft SQL Server 2008 a rozhraní .NET Framework 3.5 SP1 umožňuje mapovat CLR <xref:System.TimeSpan?displayProperty=nameWithType> typu SQL Server `TIME` typu. Existuje ale velký rozdíl v rozsahu od, který modul CLR <xref:System.TimeSpan?displayProperty=nameWithType> podporuje a co systému SQL Server `TIME` zadejte podporuje. Mapování hodnoty menší než 0 nebo větší než hodiny 23:59:59.9999999 SQL `TIME` výsledkem bude výjimky přetečení. Další informace najdete v tématu [metody System.TimeSpan](../../../../../../docs/framework/data/adonet/sql/linq/system-timespan-methods.md).  
  
 V systému Microsoft SQL Server 2000 a SQL Server 2005, nelze mapovat pole databáze <xref:System.TimeSpan>. Však operace <xref:System.TimeSpan> jsou podporované, protože <xref:System.TimeSpan> hodnoty mohou být vráceny od <xref:System.DateTime> odčítání nebo zařadit do výrazu jako literál nebo vazby proměnné.  
  
<a name="BinaryMapping"></a>   
## <a name="binary-mapping"></a>Binární mapování  
 Existuje mnoho typů systému SQL Server, které lze mapovat na typ CLR <xref:System.Data.Linq.Binary?displayProperty=nameWithType>. V následující tabulce jsou uvedeny typy serveru SQL Server, které způsobují O/R Designer a SQLMetal k definování modul CLR. <xref:System.Data.Linq.Binary?displayProperty=nameWithType> zadejte při vytváření objektový model nebo externí mapování souboru podle vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používané O/R Designer a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)` s `FILESTREAM` atribut|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 V následující tabulce jsou uvedeny výchozí mapování typu používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda k definování typů SQL sloupce, které jsou vytvořeny pro mapování pro typy CLR definovaný v objektovém modelu nebo externí mapování souboru.  
  
|Typ CLR|Výchozí SQL serveru typ používaný <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 Existuje mnoho dalších binární mapování, které můžete, ale některé může vést k přetečení nebo data ztráty výjimky při převodu do nebo z databáze. Další informace najdete v tématu [typ mapování spustit čas chování matice](#BehaviorMatrix).  
  
### <a name="sql-server-filestream"></a>SQL Server FILESTREAM  
 `FILESTREAM` Atributu `VARBINARY(MAX)` sloupce je k dispozici od verze Microsoft SQL Server 2008, můžete namapovat ho pomocí LINQ to SQL, od verze rozhraní .NET Framework verze 3.5 SP1.  
  
 I když můžete namapovat `VARBINARY(MAX)` sloupce s `FILESTREAM` atribut <xref:System.Data.Linq.Binary> objekty, <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda nelze automaticky vytvořit sloupce s `FILESTREAM` atribut. Další informace o `FILESTREAM`, naleznete v tématu [FILESTREAM přehled](https://go.microsoft.com/fwlink/?LinkId=115291) na Microsoft SQL Server Books Online.  
  
<a name="BinarySerialization"></a>   
### <a name="binary-serialization"></a>Binární serializace  
 Pokud třída implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní, může serializovat objekt některého z polí binární SQL (`BINARY`, `VARBINARY`, `IMAGE`). Objekt je serializaci a deserializaci podle jak <xref:System.Runtime.Serialization.ISerializable> rozhraní je implementováno. Další informace najdete v tématu [binární serializace](https://go.microsoft.com/fwlink/?LinkId=115581).  
  
<a name="MiscMapping"></a>   
## <a name="miscellaneous-mapping"></a>Různé mapování  
 V následující tabulce jsou uvedeny výchozí mapování typů pro některé různé typy, které ještě nebyly bylo zmíněno. Následující tabulka uvádí typy CLR, že O/R Designer a SQLMetal vybrat při vytváření objektový model nebo externí mapování souboru podle vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používané O/R Designer a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 V následující tabulce jsou uvedeny výchozí mapování typu používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda k definování typů SQL sloupce, které jsou vytvořeny pro mapování pro typy CLR definovaný v objektovém modelu nebo externí mapování souboru.  
  
|Typ CLR|Výchozí SQL serveru typ používaný <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 Technologie LINQ to SQL nepodporuje žádné jiné mapování typů pro tyto různé typy.  Další informace najdete v tématu [typ mapování spustit čas chování matice](#BehaviorMatrix).  
  
## <a name="see-also"></a>Viz také:
- [Mapování na základě atributů](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [Neshody typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)
