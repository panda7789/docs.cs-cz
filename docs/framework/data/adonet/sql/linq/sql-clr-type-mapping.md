---
title: Mapování typů SQL a CLR
ms.date: 07/23/2018
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: 0ac2c62388e554dad31beb54966fa2a4d5ffea2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945018"
---
# <a name="sql-clr-type-mapping"></a>Mapování typů SQL a CLR
V LINQ to SQL datový model relační databáze mapuje na objektový model, který je vyjádřen v programovacím jazyce podle vašeho výběru. Když se aplikace spustí, LINQ to SQL přeloží dotazy integrované v jazyce v objektovém modelu do SQL a pošle je do databáze ke spuštění. Když databáze vrátí výsledky, LINQ to SQL přeloží výsledky zpět na objekty, se kterými můžete pracovat ve vlastním programovacím jazyce.  
  
 Aby bylo možné přeložit data mezi objektovým modelem a databází, musí být definováno *mapování typů* . LINQ to SQL používá mapování typů ke spárování každého typu modulu CLR (Common Language Runtime) s konkrétním typem SQL Server. V objektovém modelu s mapováním založeném na atributech můžete definovat mapování typů a další informace o mapování, jako je struktura databáze a vztahy mezi tabulkami. Alternativně můžete zadat informace o mapování mimo objektový model s externím mapovacím souborem. Další informace najdete v tématu [mapování na základě atributů](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) a [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 Toto téma popisuje následující body:  
  
- [Výchozí mapování typů](#DefaultTypeMapping)  
  
- [Matice chování mapování typů za běhu](#BehaviorMatrix)  
  
- [Rozdíly v chování při provádění CLR a SQL](#BehaviorDiffs)  
  
- [Mapování výčtu](#EnumMapping)  
  
- [Číselné mapování](#NumericMapping)  
  
- [Mapování textu a XML](#TextMapping)  
  
- [Mapování data a času](#DateMapping)  
  
- [Mapování binárních souborů](#BinaryMapping)  
  
- [Různá mapování](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>   
## <a name="default-type-mapping"></a>Výchozí mapování typů  
 Pomocí Návrhář relací objektů (O/R Designer) nebo nástroje příkazového řádku SQLMetal můžete automaticky vytvořit objektový model nebo externí mapování souboru. Výchozí mapování typů pro tyto nástroje definují, které typy CLR jsou zvoleny k mapování sloupců v rámci databáze SQL Server. Další informace o použití těchto nástrojů naleznete v tématu [Creating a Object Model](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md).  
  
 Můžete také použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metodu k vytvoření databáze SQL Server na základě informací o mapování v objektovém modelu nebo v externím souboru mapování. Výchozí mapování typů pro <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metodu definují, který typ SQL Server sloupců je vytvořen pro mapování na typy CLR v objektovém modelu. Další informace najdete v tématu [jak: Dynamicky vytvořit databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
<a name="BehaviorMatrix"></a>   
## <a name="type-mapping-run-time-behavior-matrix"></a>Matice chování mapování typů za běhu  
 Následující diagram znázorňuje očekávané chování konkrétního mapování typů v době, kdy jsou data načtena nebo ukládána do databáze. S výjimkou serializace nepodporuje LINQ to SQL mapování mezi žádnými datovými typy CLR nebo SQL Server, které nejsou uvedeny v této matici. Další informace o podpoře serializace naleznete v tématu [binární serializace](#BinarySerialization).  
 
![SQL Server k tabulce mapování datových typů SQL CLR](media/sql-clr-type-mapping.png)

> [!NOTE]
> Některé mapování typů může způsobit přetečení nebo výjimky ztráty dat při převodu do nebo z databáze.  
  
### <a name="custom-type-mapping"></a>Mapování vlastního typu  
 U LINQ to SQL nebudete omezeni na výchozí mapování typu používaného návrhářem s/R, SQLMetal a <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metodou. Můžete vytvořit mapování vlastního typu explicitním zadáním v souboru DBML. Pak můžete použít tento soubor DBML k vytvoření kódu a souboru mapování objektu modelu. Další informace najdete v tématu [mapování vlastních typů SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
<a name="BehaviorDiffs"></a>   
## <a name="behavior-differences-between-clr-and-sql-execution"></a>Rozdíly v chování při provádění CLR a SQL  
 Z důvodu rozdílů v přesnosti a provádění mezi CLR a SQL Server může docházet k různým výsledkům nebo různým chováním v závislosti na tom, kde provádíte výpočty. Výpočty provedené v LINQ to SQLch dotazech jsou ve skutečnosti přeloženy do jazyka Transact-SQL a následně provedeny v databázi SQL Server. Výpočty provedené mimo LINQ to SQL dotazy jsou spouštěny v kontextu CLR.  
  
 Například následuje několik rozdílů v chování mezi CLR a SQL Server:  
  
- SQL Server řadí některé typy dat jinak než data ekvivalentního typu v modulu CLR. Například SQL Server data typu `UNIQUEIDENTIFIER` jsou seřazena jinak než data CLR typu. <xref:System.Guid?displayProperty=nameWithType>  
  
- SQL Server zpracovává některé operace porovnání řetězců jinak než CLR. V SQL Server chování porovnávání řetězců závisí na nastavení kolace na serveru. Další informace najdete v tématu [práce s kolací](https://go.microsoft.com/fwlink/?LinkId=115330) na webu knihy Online pro Microsoft SQL Server.  
  
- SQL Server mohou vracet jiné hodnoty pro některé mapované funkce než CLR. Například funkce rovnosti se budou lišit, protože SQL Server považují dva řetězce za stejné, pokud se liší pouze na konci prázdného místa; vzhledem k tomu, že CLR považuje za nerovné.  
  
<a name="EnumMapping"></a>   
## <a name="enum-mapping"></a>Mapování výčtu  
 LINQ to SQL podporuje mapování typu CLR <xref:System.Enum?displayProperty=nameWithType> na typy SQL Server dvěma způsoby:  
  
- Mapování na číselné typy SQL (`TINYINT`, `SMALLINT`, `INT`, `BIGINT`)  
  
     Pokud namapujete typ <xref:System.Enum?displayProperty=nameWithType> CLR na číselný typ SQL, namapujete základní celočíselnou hodnotu CLR <xref:System.Enum?displayProperty=nameWithType> na hodnotu sloupce databáze SQL Server. Například pokud <xref:System.Enum?displayProperty=nameWithType> pojmenovaný `DaysOfWeek` obsahuje člena s názvem `Tue` s podkladovou celočíselnou hodnotou 3, tento člen se mapuje na hodnotu databáze 3.  
  
- Mapování na textové typy SQL (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`)  
  
     Při mapování typu CLR <xref:System.Enum?displayProperty=nameWithType> na typ textu SQL je hodnota databáze SQL namapována na názvy členů CLR. <xref:System.Enum?displayProperty=nameWithType> Například pokud <xref:System.Enum?displayProperty=nameWithType> pojmenovaný `DaysOfWeek` obsahuje člena s názvem `Tue` s podkladovou celočíselnou hodnotou 3, `Tue`tento člen se mapuje na hodnotu databáze.  
  
> [!NOTE]
> Při mapování typů textu SQL na CLR <xref:System.Enum?displayProperty=nameWithType>zahrňte pouze názvy <xref:System.Enum> členů do namapovaného sloupce SQL. Další hodnoty nejsou podporovány ve sloupci mapovaném na <xref:System.Enum>server SQL.  
  
 Nástroj příkazového řádku pro/R Designer a SQLMetal nemůže automaticky mapovat typ SQL na třídu CLR <xref:System.Enum> . Toto mapování je nutné explicitně nakonfigurovat přizpůsobením souboru DBML pro použití v Návrháři O/R a v SQLMetal. Další informace o mapování vlastních typů naleznete v tématu [mapování vlastních typů SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
 Vzhledem k tomu, že sloupec SQL určený pro výčet bude stejného typu jako jiné číselné a textové sloupce; Tyto nástroje nerozpoznají váš záměr a výchozí mapování, jak je popsáno v následujícím [číselném mapování](#NumericMapping) a oddílech [mapování XML](#TextMapping) . Další informace o generování kódu se souborem DBML naleznete [v tématu generování kódu v LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
 Metoda vytvoří sloupec SQL číselného typu pro mapování typu CLR <xref:System.Enum?displayProperty=nameWithType>. <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>  
  
<a name="NumericMapping"></a>   
## <a name="numeric-mapping"></a>Číselné mapování  
 LINQ to SQL umožňuje mapovat mnoho typů CLR a SQL Server číselné typy. V následující tabulce jsou uvedeny typy CLR, které pro/R Designer a SQLMetal vyberte při sestavování objektového modelu nebo externího mapování na základě vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používaného v/R designeru a SQLMetal|  
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
  
 Následující tabulka ukazuje výchozí mapování typů používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodou k definování, který typ sloupců SQL je vytvořen pro mapování na typy CLR definované v objektovém modelu nebo v externím souboru mapování.  
  
|Typ CLR|Výchozí typ SQL Server používaný nástrojem<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
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
  
 Existuje mnoho dalších číselných mapování, která můžete zvolit, ale některé můžou mít za následek přetečení nebo výjimky ztráty dat při převodu do nebo z databáze. Další informace naleznete v [matici chování mapování typu běhu](#BehaviorMatrix).  
  
### <a name="decimal-and-money-types"></a>Typy Decimal a Money  
 Výchozí přesnost typu SQL Server `DECIMAL` (18 desítkových číslic vlevo a vpravo od desetinné čárky) je mnohem menší než přesnost typu CLR <xref:System.Decimal?displayProperty=nameWithType> , ke kterému je párována ve výchozím nastavení. To může mít za následek ztrátu přesnosti při ukládání dat do databáze. Pouze opak se však může vyskytnout, pokud je `DECIMAL` typ SQL Server nakonfigurovaný s více než 29 číslicemi přesnosti. Pokud SQL Server `DECIMAL` typ byl nakonfigurován s větší přesností než CLR <xref:System.Decimal?displayProperty=nameWithType>, může dojít ke ztrátě přesnosti při načítání dat z databáze.  
  
 Typy SQL Server `MONEY` a `SMALLMONEY` , které jsou ve výchozím nastavení spárovány s typem <xref:System.Decimal?displayProperty=nameWithType> CLR, mají mnohem menší přesnost, což může způsobit přetečení nebo výjimky ztráty dat při ukládání dat do databáze.  
  
<a name="TextMapping"></a>   
## <a name="text-and-xml-mapping"></a>Mapování textu a XML  
 Existuje také mnoho typů založených na textu a XML, které lze namapovat pomocí LINQ to SQL. V následující tabulce jsou uvedeny typy CLR, které pro/R Designer a SQLMetal vyberte při sestavování objektového modelu nebo externího mapování na základě vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používaného v/R designeru a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 Následující tabulka ukazuje výchozí mapování typů používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodou k definování, který typ sloupců SQL je vytvořen pro mapování na typy CLR definované v objektovém modelu nebo v externím souboru mapování.  
  
|Typ CLR|Výchozí typ SQL Server používaný nástrojem<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=nameWithType>[]|`NVARCHAR(4000)`|  
|Implementace `Parse()` vlastního typu a`ToString()`|`NVARCHAR(MAX)`|  
  
 Existuje mnoho dalších textových mapování XML, které si můžete vybrat, ale některé můžou mít za následek přetečení nebo výjimky ztráty dat při převodu do nebo z databáze. Další informace naleznete v [matici chování mapování typu běhu](#BehaviorMatrix).  
  
### <a name="xml-types"></a>Typy XML  
 Datový typ `XML` SQL Server je k dispozici od Microsoft SQL Server 2005. Datový typ SQL Server `XML` lze namapovat na <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>nebo <xref:System.String>. Pokud sloupec ukládá fragmenty XML, které nelze číst do <xref:System.Xml.Linq.XElement>, sloupec musí být namapován na <xref:System.String> , aby se předešlo chybám za běhu. Fragmenty kódu XML, které musí <xref:System.String> být namapovány tak, aby obsahovaly následující:  
  
- Sekvence elementů XML  
  
- Atributy  
  
- Veřejné identifikátory (PI)  
  
- Komentáře  
  
 I když lze <xref:System.Xml.Linq.XElement> namapovat <xref:System.Xml.Linq.XDocument> a na SQL Server, jak je znázorněno v [matici chování při mapování typů](#BehaviorMatrix), <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda nemá pro tyto typy žádné výchozí mapování typu SQL Server.  
  
### <a name="custom-types"></a>Vlastní typy  
 Pokud `Parse()` třída implementuje a `ToString()`, můžete objekt namapovat na libovolný textový typ SQL (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`, `TEXT`, `NTEXT`, `XML`). Objekt je uložen v databázi odesláním hodnoty vrácené `ToString()` do sloupce mapované databáze. Objekt je znovu vytvořen vyvoláním `Parse()` u řetězce vráceného databází.  
  
> [!NOTE]
> LINQ to SQL nepodporuje serializaci pomocí <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.  
  
<a name="DateMapping"></a>   
## <a name="date-and-time-mapping"></a>Mapování data a času  
 Pomocí LINQ to SQL můžete namapovat mnoho SQL Serverch typů data a času. V následující tabulce jsou uvedeny typy CLR, které pro/R Designer a SQLMetal vyberte při sestavování objektového modelu nebo externího mapování na základě vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používaného v/R designeru a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 Následující tabulka ukazuje výchozí mapování typů používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodou k definování, který typ sloupců SQL je vytvořen pro mapování na typy CLR definované v objektovém modelu nebo v externím souboru mapování.  
  
|Typ CLR|Výchozí typ SQL Server používaný nástrojem<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 Existuje mnoho dalších mapování data a času, které můžete vybrat, ale některé můžou mít za následek přetečení nebo výjimky ztráty dat při převodu do nebo z databáze. Další informace naleznete v [matici chování mapování typu běhu](#BehaviorMatrix).  
  
> [!NOTE]
> `DATETIME2`SQL Server typy `DATETIMEOFFSET` ,,a`TIME` jsou k dispozici od Microsoft SQL Server 2008. `DATE` LINQ to SQL podporuje mapování na tyto nové typy od .NET Framework verze 3,5 SP1.  
  
### <a name="systemdatetime"></a>System.Datetime  
 Rozsah a přesnost typu CLR <xref:System.DateTime?displayProperty=nameWithType> je větší než rozsah a přesnost typu SQL Server `DATETIME` , což je <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> výchozí mapování typu pro metodu. Aby nedocházelo k výjimkám s výjimkami souvisejícími `DATETIME`s daty `DATETIME2`mimo rozsah, použijte, který je k dispozici od Microsoft SQL Server 2008. `DATETIME2`může odpovídat rozsahu a přesnosti CLR <xref:System.DateTime?displayProperty=nameWithType>.  
  
 SQL Server data nemají koncept <xref:System.TimeZone>, funkce, která je bohatě podporovaná v modulu CLR. <xref:System.TimeZone>hodnoty se ukládají do databáze bez převodu bez <xref:System.TimeZone> ohledu na původní <xref:System.DateTimeKind> informace. Při <xref:System.DateTime> načítání hodnot z databáze je jejich hodnota načtena jako je do a <xref:System.DateTime> <xref:System.DateTimeKind>. <xref:System.DateTimeKind.Unspecified> Další informace o podporovaných <xref:System.DateTime?displayProperty=nameWithType> metodách naleznete v tématu [System. DateTime Methods](../../../../../../docs/framework/data/adonet/sql/linq/system-datetime-methods.md).  
  
### <a name="systemtimespan"></a>System. TimeSpan  
 Microsoft SQL Server 2008 a .NET Framework 3,5 SP1 vám umožní namapovat typ CLR <xref:System.TimeSpan?displayProperty=nameWithType> na typ SQL Server. `TIME` Existuje však velký rozdíl mezi rozsahem, který modul CLR <xref:System.TimeSpan?displayProperty=nameWithType> podporuje, a jaký typ SQL Server `TIME` podporuje. Mapování hodnot menší než 0 nebo větší než 23:59:59.9999999 hodin do SQL `TIME` bude mít za následek výjimky přetečení. Další informace naleznete v tématu [metody System. TimeSpan](../../../../../../docs/framework/data/adonet/sql/linq/system-timespan-methods.md).  
  
 V Microsoft SQL Server 2000 a SQL Server 2005 nemůžete mapovat pole databáze na <xref:System.TimeSpan>. Operace na <xref:System.TimeSpan> jsou však podporovány, protože <xref:System.TimeSpan> hodnoty mohou být vráceny z <xref:System.DateTime> odčítání nebo zavedeny do výrazu jako literál nebo vázaná proměnná.  
  
<a name="BinaryMapping"></a>   
## <a name="binary-mapping"></a>Mapování binárních souborů  
 Existuje mnoho typů SQL Server, které mohou být mapovány na typ <xref:System.Data.Linq.Binary?displayProperty=nameWithType>CLR. V následující tabulce jsou uvedeny typy SQL Server, které způsobují, že v/R Designer a SQLMetal definuje <xref:System.Data.Linq.Binary?displayProperty=nameWithType> typ CLR při vytváření objektového modelu nebo externího mapování na základě vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používaného v/R designeru a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)``FILESTREAM` s atributem|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 Následující tabulka ukazuje výchozí mapování typů používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodou k definování, který typ sloupců SQL je vytvořen pro mapování na typy CLR definované v objektovém modelu nebo v externím souboru mapování.  
  
|Typ CLR|Výchozí typ SQL Server používaný nástrojem<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 Existuje mnoho dalších binárních mapování, které si můžete vybrat, ale některé můžou mít za následek přetečení nebo výjimky ztráty dat při převodu do nebo z databáze. Další informace naleznete v [matici chování mapování typu běhu](#BehaviorMatrix).  
  
### <a name="sql-server-filestream"></a>SQL Server FILESTREAM  
 `FILESTREAM` Atribut pro`VARBINARY(MAX)` sloupce je k dispozici počínaje Microsoft SQL Server 2008. můžete k němu namapovat LINQ to SQL počínaje verzí .NET Framework 3,5 SP1.  
  
 I když můžete mapovat `VARBINARY(MAX)` sloupce `FILESTREAM` s <xref:System.Data.Linq.Binary> `FILESTREAM` atributem na objekty, metodaneníschopnaautomatickyvytvořitsloupcesatributem.<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Další informace o `FILESTREAM`najdete v tématu [Přehled FILESTREAM](https://go.microsoft.com/fwlink/?LinkId=115291) na webu knihy online Microsoft SQL Server.  
  
<a name="BinarySerialization"></a>   
### <a name="binary-serialization"></a>Binární serializace  
 Pokud třída implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní, můžete serializovat objekt do libovolného binárního pole SQL (`BINARY`, `VARBINARY`, `IMAGE`). Objekt je serializován a rekonstruován podle toho, <xref:System.Runtime.Serialization.ISerializable> jak je rozhraní implementováno. Další informace naleznete v tématu [binární serializace](https://go.microsoft.com/fwlink/?LinkId=115581).  
  
<a name="MiscMapping"></a>   
## <a name="miscellaneous-mapping"></a>Různá mapování  
 Následující tabulka ukazuje výchozí mapování typů pro některé různé typy, které ještě nebyly zmíněny. V následující tabulce jsou uvedeny typy CLR, které pro/R Designer a SQLMetal vyberte při sestavování objektového modelu nebo externího mapování na základě vaší databáze.  
  
|SQL Server Type|Výchozí mapování typu CLR používaného v/R designeru a SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 Následující tabulka ukazuje výchozí mapování typů používané <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metodou k definování, který typ sloupců SQL je vytvořen pro mapování na typy CLR definované v objektovém modelu nebo v externím souboru mapování.  
  
|Typ CLR|Výchozí typ SQL Server používaný nástrojem<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 LINQ to SQL nepodporuje žádné jiné mapování typů pro tyto různé typy.  Další informace naleznete v [matici chování mapování typu běhu](#BehaviorMatrix).  
  
## <a name="see-also"></a>Viz také:

- [Mapování na základě atributů](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [Neshody typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)
