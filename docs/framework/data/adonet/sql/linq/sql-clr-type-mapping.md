---
title: Mapování typu SQL CLR
ms.date: 03/30/2017
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: 5437529d9293951ad34abda435b538b4f404c600
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365524"
---
# <a name="sql-clr-type-mapping"></a>Mapování typu SQL CLR
V technologii LINQ to SQL datový model relační databáze mapuje objektový model, který je vyjádřena v programovací jazyk podle vašeho výběru. Při spuštění aplikace, technologie LINQ to SQL překládá dotazy language-integrated ve model objektu do SQL a odešle je do databáze pro provedení. Při databáze vrátí výsledky, znamená, že technologie LINQ to SQL výsledky zpět na objekty, které můžete pracovat v vlastní programovací jazyk.  
  
 Aby bylo možné přeložit dat mezi objektový model a databázi, *mapování typu* musí být definován. Technologie LINQ to SQL používá mapování typu tak, aby každý běžné typu language runtime (CLR) s konkrétní typ systému SQL Server. Můžete definovat mapování typů a další informace o mapování třeba databáze strukturu a tabulka vztahů uvnitř objektový model s mapováním na základě atributů. Alternativně můžete zadat informace o mapování mimo objektový model se souborem externích mapování. Další informace najdete v tématu [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) a [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 Toto téma popisuje následující body:  
  
-   [Výchozí typ mapování](#DefaultTypeMapping)  
  
-   [Typ mapování matice běhového chování](#BehaviorMatrix)  
  
-   [Rozdíly v chování CLR a provedení SQL](#BehaviorDiffs)  
  
-   [Mapování výčtu](#EnumMapping)  
  
-   [Číselné mapování](#NumericMapping)  
  
-   [Text a mapování XML](#TextMapping)  
  
-   [Datum a čas mapování](#DateMapping)  
  
-   [Binární mapování](#BinaryMapping)  
  
-   [Různé mapování](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>   
## <a name="default-type-mapping"></a>Výchozí typ mapování  
 Objektový model nebo externí mapování souboru můžete vytvořit automaticky Návrhář relací objektů (Návrhář relací objektů) nebo nástroj příkazového řádku na SQLMetal. Výchozí typ mapování pro tyto nástroje definovat, jaké typy CLR se rozhodli mapovat na sloupce v databázi systému SQL Server. Další informace o používání těchto nástrojů najdete v tématu [vytváření objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md).  
  
 Můžete také <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metodu pro vytvoření databáze SQL serveru na základě mapování informací ve model objektu nebo externí mapování souboru. Výchozí typ mapování <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metoda definují, jaký typ sloupce jsou vytvořené pro mapování modulu CLR systému SQL Server typy v modelu objektu. Další informace najdete v tématu [postupy: vytvoření dynamicky databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
<a name="BehaviorMatrix"></a>   
## <a name="type-mapping-run-time-behavior-matrix"></a>Typ mapování matice běhového chování  
 Následující diagram znázorňuje očekávané chování běhové konkrétní typ mapování, když data se načítají z nebo uložil do databáze. S výjimkou serializace technologie LINQ to SQL nepodporuje mapování mezi žádná data CLR nebo SQL Server typy, které nejsou v této matici. Další informace o podpoře serializace najdete v tématu [binární serializace](#BinarySerialization).  
  
> [!NOTE]
>  Některé mapování typů může vést k přetečení nebo data ztrátě výjimky při převodu do nebo z databáze.  
  
### <a name="custom-type-mapping"></a>Mapování vlastních typů  
 Pomocí technologie LINQ to SQL, můžete nejsou omezeny na výchozí typ mapování, která používají Návrhář relací objektů na SQLMetal a <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metoda. Můžete vytvořit vlastní typ mapování tak, že je explicitně zadáte v souboru DBML. Pak můžete použít tento soubor DBML k vytvoření souboru kódu a mapování modelu objektu. Další informace najdete v tématu [mapování typu SQL CLR vlastní](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
<a name="BehaviorDiffs"></a>   
## <a name="behavior-differences-between-clr-and-sql-execution"></a>Rozdíly v chování CLR a provedení SQL  
 Z důvodu rozdíly v přesnost a provádění mezi CLR a SQL Server můžete přijímat odlišné výsledky nebo prostředí různé chování v závislosti na tom, kde můžete provést výpočtů. Výpočty provést v technologii LINQ dotazy SQL jsou ve skutečnosti přeložit Transact-SQL a pak spustit na databázi systému SQL Server. Výpočty provést mimo LINQ dotazy SQL jsou spouštěny v kontextu modulu CLR.  
  
 Následující příklady určité rozdíly v chování mezi CLR a SQL Server:  
  
-   Některé typy dat systému SQL Server odlišně, než data ekvivalentní typu řadí v modulu CLR. Například dat systému SQL Server typu `UNIQUEIDENTIFIER` je jinak než data typu CLR seřazené <xref:System.Guid?displayProperty=nameWithType>.  
  
-   SQL Server zpracovává některé operace porovnání řetězců jinak než modulu CLR. V systému SQL Server chování porovnání řetězců závisí na nastavení kolace na serveru. Další informace najdete v tématu [práce s kolací](http://go.microsoft.com/fwlink/?LinkId=115330) v Microsoft SQL Server Books Online.  
  
-   SQL Server může vracet různé hodnoty pro některé funkce namapované než modulu CLR. Například se budou lišit rovnosti funkce, protože systém SQL Server zvažuje dva řetězce, které se rovná se, pokud se liší pouze v prázdné znaky; zatímco modulu CLR je považuje za není rovno.  
  
<a name="EnumMapping"></a>   
## <a name="enum-mapping"></a>Mapování výčtu  
 Technologie LINQ to SQL podporuje mapování modulu CLR <xref:System.Enum?displayProperty=nameWithType> typu na typy systému SQL Server dvěma způsoby:  
  
-   Mapování na SQL číselnými typy (`TINYINT`, `SMALLINT`, `INT`, `BIGINT`)  
  
     Pokud namapujete CLR <xref:System.Enum?displayProperty=nameWithType> typ na číselný typ SQL, namapujete základní celočíselná hodnota CLR <xref:System.Enum?displayProperty=nameWithType> hodnotě sloupce databáze systému SQL Server. Například pokud <xref:System.Enum?displayProperty=nameWithType> s názvem `DaysOfWeek` obsahuje člena s názvem `Tue` s základní celočíselnou hodnotu 3, tento člen mapuje na databázi hodnotu 3.  
  
-   Mapování na typ textu SQL (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`)  
  
     Pokud namapujete CLR <xref:System.Enum?displayProperty=nameWithType> typu SQL typ text, hodnota databáze SQL je namapována na názvy modulu CLR <xref:System.Enum?displayProperty=nameWithType> členy. Například pokud <xref:System.Enum?displayProperty=nameWithType> s názvem `DaysOfWeek` obsahuje člena s názvem `Tue` s základní celočíselnou hodnotu 3, tento člen mapuje na hodnotu databáze `Tue`.  
  
> [!NOTE]
>  Při mapování typů text SQL na CLR <xref:System.Enum?displayProperty=nameWithType>, zahrnout pouze názvy <xref:System.Enum> členy ve sloupci namapované SQL. Jiné hodnoty nejsou podporovány v <xref:System.Enum>-mapovat sloupec SQL.  
  
 Nástroj příkazového řádku Návrhář relací objektů a SQLMetal nelze mapovat automaticky typ SQL CLR <xref:System.Enum> třídy. Toto mapování musí explicitně nakonfigurovat přizpůsobením souboru DBML používat Návrhář relací objektů a na SQLMetal. Další informace o mapování vlastního typu, najdete v části [vlastní mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
 Vzhledem k tomu, že sloupec SQL určený pro výčet bude stejného typu jako ostatní číselné a textové sloupce; Tyto nástroje nebude rozpoznat záměr a výchozí nastavení mapování, jak je popsáno v následujícím [číselné mapování](#NumericMapping) a [Text a mapování XML](#TextMapping) oddíly. Další informace o generování kódu s souboru DBML najdete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda vytvoří sloupec SQL číselného typu mapovat CLR <xref:System.Enum?displayProperty=nameWithType> typu.  
  
<a name="NumericMapping"></a>   
## <a name="numeric-mapping"></a>Číselné mapování  
 Technologie LINQ to SQL umožňuje mapovat číselnými typy mnoho CLR a SQL Server. Následující tabulka uvádí typy CLR, Návrhář relací objektů a SQLMetal vyberte, když vytváříte objektový model, nebo externí mapování souboru na základě vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používané Návrhář relací objektů a SQLMetal|  
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
  
 V další tabulce jsou uvedeny výchozí mapování typu používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodu pro definování typů SQL sloupců, které jsou vytvořené pro mapování na definované v modelu objektu nebo v souboru mapování externí typy CLR.  
  
|Typ CLR|Používá výchozí SQL serveru typ <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
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
  
 Existuje mnoho dalších číselné mapování můžete zvolit, avšak některé může mít za následek přetečení nebo data výjimky ztrátě při překladu do nebo z databáze. Další informace najdete v tématu [typ mapování spustit čas chování matice](#BehaviorMatrix).  
  
### <a name="decimal-and-money-types"></a>Decimal a peníze typy  
 Výchozí přesnost systému SQL Server `DECIMAL` typ (18 desítková číslice vlevo a vpravo od desetinné čárky) je mnohem menší než přesnost modulu CLR <!--zz <xref:System.Decima?displayProperty=nameWithType>l --> `Decimal` typ, který je spárováno se ve výchozím nastavení. To může způsobit ztrátu přesnosti při ukládání dat do databáze. Ale stejně jako opak může dojít v případě systému SQL Server `DECIMAL` typ je konfigurovaný s větší než 29 míst přesnosti. Pokud SQL Server `DECIMAL` nakonfiguroval typ s přesností větší než modulu CLR <xref:System.Decimal?displayProperty=nameWithType>, ztráta přesnosti může dojít při načítání dat z databáze.  
  
 SQL Server `MONEY` a `SMALLMONEY` typů, které jsou také spárovaný s modulu CLR <xref:System.Decimal?displayProperty=nameWithType> zadejte ve výchozím nastavení, máte mnohem menší přesností, což může vést ke ztrátě výjimky přetečení nebo data při ukládání dat do databáze.  
  
<a name="TextMapping"></a>   
## <a name="text-and-xml-mapping"></a>Text a mapování XML  
 Existují také mnoho založený na textu a typy XML, které můžete namapovat s technologie LINQ to SQL. Následující tabulka uvádí typy CLR, Návrhář relací objektů a SQLMetal vyberte, když vytváříte objektový model, nebo externí mapování souboru na základě vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používané Návrhář relací objektů a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 V další tabulce jsou uvedeny výchozí mapování typu používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodu pro definování typů SQL sloupců, které jsou vytvořené pro mapování na definované v modelu objektu nebo v souboru mapování externí typy CLR.  
  
|Typ CLR|Používá výchozí SQL serveru typ <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=nameWithType>[]|`NVARCHAR(4000)`|  
|Implementace vlastního typu `Parse()` a `ToString()`|`NVARCHAR(MAX)`|  
  
 Existuje mnoho dalších založený na textu XML mapování můžete, ale některé může mít za následek přetečení nebo data výjimky ztrátě při překladu do nebo z databáze. Další informace najdete v tématu [typ mapování spustit čas chování matice](#BehaviorMatrix).  
  
### <a name="xml-types"></a>Typy XML  
 SQL Server `XML` datový typ je k dispozici od verze Microsoft SQL Server 2005. Můžete namapovat systému SQL Server `XML` datový typ pro <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>, nebo <xref:System.String>. Pokud sloupec ukládá fragmenty XML, které nelze načíst do <xref:System.Xml.Linq.XElement>, sloupec musí být mapován na <xref:System.String> aby zabránil chybám při běhu. Fragmenty kódu XML, které musí být mapován na <xref:System.String> patří:  
  
-   Pořadí elementů XML  
  
-   Atributy  
  
-   Veřejné identifikátory (PI)  
  
-   Komentáře  
  
 I když můžete namapovat <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XDocument> k systému SQL Server, jak je znázorněno [matice chování čas spuštění mapování typu](#BehaviorMatrix), <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda nemá žádné výchozí mapování typu SQL Server pro tyto typy.  
  
### <a name="custom-types"></a>Vlastní typy  
 Pokud třída implementuje `Parse()` a `ToString()`, objekt můžete namapovat k libovolnému typu text SQL (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`, `TEXT`, `NTEXT`, `XML`). Objekt se uloží v databázi odesláním hodnoty vrácené `ToString()` do sloupce namapované databáze. Objekt je znovu vytvořena vyvoláním `Parse()` na řetězec vrácený databáze.  
  
> [!NOTE]
>  Technologie LINQ to SQL nepodporuje serializaci pomocí <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.  
  
<a name="DateMapping"></a>   
## <a name="date-and-time-mapping"></a>Datum a čas mapování  
 Pomocí technologie LINQ to SQL můžete namapovat mnoho typů systému SQL Server data a času. Následující tabulka uvádí typy CLR, Návrhář relací objektů a SQLMetal vyberte, když vytváříte objektový model, nebo externí mapování souboru na základě vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používané Návrhář relací objektů a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 V další tabulce jsou uvedeny výchozí mapování typu používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodu pro definování typů SQL sloupců, které jsou vytvořené pro mapování na definované v modelu objektu nebo v souboru mapování externí typy CLR.  
  
|Typ CLR|Používá výchozí SQL serveru typ <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 Existuje mnoho dalších datum a čas mapování můžete zvolit, avšak některé může mít za následek přetečení nebo data výjimky ztrátě při překladu do nebo z databáze. Další informace najdete v tématu [typ mapování spustit čas chování matice](#BehaviorMatrix).  
  
> [!NOTE]
>  Typy systému SQL Server `DATETIME2`, `DATETIMEOFFSET`, `DATE`, a `TIME` jsou dostupné od verze Microsoft SQL Server 2008. Technologie LINQ to SQL podporuje mapování na tyto nové typy od verze rozhraní .NET Framework verze 3.5 SP1.  
  
### <a name="systemdatetime"></a>System.Datetime  
 Rozsah a přesnost modulu CLR <xref:System.DateTime?displayProperty=nameWithType> typu je větší než rozsah a přesnost systému SQL Server `DATETIME` typ, který je výchozí typ mapování pro <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda. Abyste se vyhnuli výjimky související s daty mimo rozsah `DATETIME`, použijte `DATETIME2`, která je k dispozici od verze Microsoft SQL Server 2008. `DATETIME2` může odpovídat rozsahu a přesnost modulu CLR <xref:System.DateTime?displayProperty=nameWithType>.  
  
 SQL Server data nemají žádný koncept <xref:System.TimeZone>, funkce, která je v modulu CLR bohatě podporovaná. <xref:System.TimeZone> hodnoty se uloží jako je databáze bez <xref:System.TimeZone> převodu, bez ohledu na původní <xref:System.DateTimeKind> informace. Když <xref:System.DateTime> hodnoty jsou načteny z databáze, jejich hodnota je načtena, protože je do <xref:System.DateTime> s <xref:System.DateTimeKind> z <xref:System.DateTimeKind.Unspecified>. Další informace o podporované <xref:System.DateTime?displayProperty=nameWithType> metody, najdete v části [System.DateTime metody](../../../../../../docs/framework/data/adonet/sql/linq/system-datetime-methods.md).  
  
### <a name="systemtimespan"></a>System.TimeSpan  
 Microsoft SQL Server 2008 a rozhraní .NET Framework 3.5 SP1 umožňují mapování modulu CLR <xref:System.TimeSpan?displayProperty=nameWithType> typ k systému SQL Server `TIME` typu. Existuje však velký rozdíl mezi rozsahu, modulu CLR <xref:System.TimeSpan?displayProperty=nameWithType> podporuje a co systému SQL Server `TIME` zadejte podporuje. Mapování hodnoty menší než 0 nebo větší než 23:59:59.9999999 hodin na SQL `TIME` bude mít za následek přetečení výjimky. Další informace najdete v tématu [System.TimeSpan metody](../../../../../../docs/framework/data/adonet/sql/linq/system-timespan-methods.md).  
  
 V systému Microsoft SQL Server 2000 a SQL Server 2005, nelze mapovat pole databáze k <xref:System.TimeSpan>. Ale operací na <xref:System.TimeSpan> jsou podporována, protože <xref:System.TimeSpan> hodnoty lze vrátit ze <xref:System.DateTime> odčítání nebo zasaženo výraz jako literál nebo vázané proměnnou.  
  
<a name="BinaryMapping"></a>   
## <a name="binary-mapping"></a>Binární mapování  
 Existuje mnoho typů systému SQL Server, které lze mapovat na typ CLR <xref:System.Data.Linq.Binary?displayProperty=nameWithType>. V následující tabulce jsou uvedeny typy systému SQL Server, které způsobit Návrhář relací objektů a SQLMetal k definování CLR <xref:System.Data.Linq.Binary?displayProperty=nameWithType> zadat, když vytváříte objektový model, nebo soubor externí mapování založené na vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používané Návrhář relací objektů a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)` pomocí `FILESTREAM` atribut|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 V další tabulce jsou uvedeny výchozí mapování typu používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodu pro definování typů SQL sloupců, které jsou vytvořené pro mapování na definované v modelu objektu nebo v souboru mapování externí typy CLR.  
  
|Typ CLR|Používá výchozí SQL serveru typ <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 Existuje mnoho dalších binární mapování můžete zvolit, avšak některé může mít za následek přetečení nebo data výjimky ztrátě při překladu do nebo z databáze. Další informace najdete v tématu [typ mapování spustit čas chování matice](#BehaviorMatrix).  
  
### <a name="sql-server-filestream"></a>Systému SQL Server FILESTREAM  
 `FILESTREAM` Atribut pro `VARBINARY(MAX)` sloupce je k dispozici od verze Microsoft SQL Server 2008, můžete namapovat na ni s technologie LINQ to SQL od verze rozhraní .NET Framework verze 3.5 SP1.  
  
 I když můžete namapovat `VARBINARY(MAX)` sloupce s `FILESTREAM` atribut <xref:System.Data.Linq.Binary> objekty, <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda se nepodařilo automaticky vytvořit sloupce s `FILESTREAM` atribut. Další informace o `FILESTREAM`, najdete v části [FILESTREAM přehled](http://go.microsoft.com/fwlink/?LinkId=115291) na Microsoft SQL Server Books Online.  
  
<a name="BinarySerialization"></a>   
### <a name="binary-serialization"></a>Binární serializace  
 Pokud třída implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní, může serializovat objekt pro každé pole binární SQL (`BINARY`, `VARBINARY`, `IMAGE`). Objekt je serializovat a deserializovat podle jak <xref:System.Runtime.Serialization.ISerializable> rozhraní je implementováno. Další informace najdete v tématu [binární serializace](http://go.microsoft.com/fwlink/?LinkId=115581).  
  
<a name="MiscMapping"></a>   
## <a name="miscellaneous-mapping"></a>Různé mapování  
 Následující tabulka uvádí výchozí typ mapování pro některé různé typy, které nebyly ještě zmíněny. Následující tabulka uvádí typy CLR, Návrhář relací objektů a SQLMetal vyberte, když vytváříte objektový model, nebo externí mapování souboru na základě vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používané Návrhář relací objektů a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 V další tabulce jsou uvedeny výchozí mapování typu používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodu pro definování typů SQL sloupců, které jsou vytvořené pro mapování na definované v modelu objektu nebo v souboru mapování externí typy CLR.  
  
|Typ CLR|Používá výchozí SQL serveru typ <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 Technologie LINQ to SQL nepodporuje žádné jiné mapování typů pro tyto různé typy.  Další informace najdete v tématu [typ mapování spustit čas chování matice](#BehaviorMatrix).  
  
## <a name="see-also"></a>Viz také  
 [Mapování na základě atributů](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [Externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [Neshody typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)
