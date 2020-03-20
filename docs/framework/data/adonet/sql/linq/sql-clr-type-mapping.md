---
title: Mapování typů SQL a CLR
ms.date: 07/23/2018
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: 336732e0fe7ca8955702d325309db6a8e61b1722
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174534"
---
# <a name="sql-clr-type-mapping"></a>Mapování typů SQL a CLR
V LINQ na SQL se datový model relační databáze mapuje na objektový model, který je vyjádřen v programovacím jazyce podle vašeho výběru. Při spuštění aplikace LINQ na SQL překládá dotazy integrované jazykem v objektovém modelu do SQL a odešle je do databáze pro spuštění. Když databáze vrátí výsledky, LINQ na SQL převede výsledky zpět na objekty, které můžete pracovat s ve vlastním programovacím jazyce.  
  
 Aby bylo možné překládat data mezi objektovým modelem a databází, musí být *definováno mapování typů.* LINQ na SQL používá mapování typů tak, aby odpovídalo každému typu CLR (CLR) společného jazyka s určitým typem serveru SQL Server. Můžete definovat mapování typů a další informace o mapování, jako je například struktura databáze a relace tabulek, uvnitř objektového modelu s mapováním založeným na atributech. Případně můžete určit informace o mapování mimo objektový model pomocí externího souboru mapování. Další informace naleznete [v tématu Mapování na základě atributů](attribute-based-mapping.md) a [externí mapování](external-mapping.md).  
  
 Toto téma popisuje následující body:  
  
- [Výchozí mapování typů](#DefaultTypeMapping)  
  
- [Matice chování za běhu mapování typu](#BehaviorMatrix)  
  
- [Rozdíly chování mezi clr a sql spuštění](#BehaviorDiffs)  
  
- [Mapování výčtu](#EnumMapping)  
  
- [Číselné mapování](#NumericMapping)  
  
- [Mapování textu a XML](#TextMapping)  
  
- [Mapování data a času](#DateMapping)  
  
- [Binární mapování](#BinaryMapping)  
  
- [Různé mapování](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>
## <a name="default-type-mapping"></a>Výchozí mapování typů  
 Objektový model nebo externí soubor mapování můžete vytvořit automaticky pomocí návrháře relačních objektů (O/R Designer) nebo pomocí nástroje příkazového řádku SQLMetal. Výchozí mapování typů pro tyto nástroje definuje, které typy CLR jsou vybrány k mapování na sloupce uvnitř databáze serveru SQL Server. Další informace o použití těchto nástrojů naleznete [v tématu Vytvoření objektového modelu](creating-the-object-model.md).  
  
 Tuto metodu <xref:System.Data.Linq.DataContext.CreateDatabase%2A> můžete také použít k vytvoření databáze serveru SQL Server na základě informací o mapování v objektovém modelu nebo externím souboru mapování. Výchozí mapování typů pro <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metodu definuje, jaký typ sloupců serveru SQL Server jsou vytvořeny pro mapování na typy CLR v objektovém modelu. Další informace naleznete v [tématu Jak: Dynamicky vytvořit databázi](how-to-dynamically-create-a-database.md).  
  
<a name="BehaviorMatrix"></a>
## <a name="type-mapping-run-time-behavior-matrix"></a>Matice chování za běhu mapování typu  
 Následující diagram znázorňuje očekávané chování za běhu konkrétního mapování typů při načítání dat z databáze nebo do ní uložených. S výjimkou serializace LINQ na SQL nepodporuje mapování mezi všechny clr nebo SQL Server datové typy, které nejsou zadány v této matici. Další informace o podpoře serializace naleznete [v tématu Binary Serialization](#BinarySerialization).  

![Tabulka mapování datového typu SQL Server na SQL CLR](./media/sql-clr-type-mapping.png)

> [!NOTE]
> Některé mapování typů může mít za následek přetečení nebo ztrátu dat výjimky při překladu do nebo z databáze.  
  
### <a name="custom-type-mapping"></a>Vlastní mapování typů  
 S LINQ na SQL, nejste omezeni na výchozí mapování typů používaných O/R Designer, SQLMetal a <xref:System.Data.Linq.DataContext.CreateDatabase%2A> metody. Vlastní mapování typů můžete vytvořit tak, že je explicitně zadáte v souboru DBML. Pak můžete tento soubor DBML použít k vytvoření kódu objektového modelu a souboru mapování. Další informace naleznete v [tématu SQL-CLR Custom Type Mappings](sql-clr-custom-type-mappings.md).  
  
<a name="BehaviorDiffs"></a>
## <a name="behavior-differences-between-clr-and-sql-execution"></a>Rozdíly chování mezi clr a sql spuštění  
 Z důvodu rozdílů v přesnosti a provádění mezi CLR a SQL Server, může získat různé výsledky nebo dochází k různým chování mů e v závislosti na tom, kde provádět výpočty. Výpočty provedené v linq na dotazy SQL jsou ve skutečnosti přeloženy do Transact-SQL a poté provedeny v databázi serveru SQL Server. Výpočty prováděné mimo dotazy LINQ na SQL jsou prováděny v kontextu CLR.  
  
 Například jsou následující rozdíly v chování mezi CLR a SQL Server:  
  
- SQL Server objednává některé datové typy odlišně než data ekvivalentního typu v CLR. Například sql server data `UNIQUEIDENTIFIER` typu je seřazeno <xref:System.Guid?displayProperty=nameWithType>jinak než clr data typu .  
  
- SQL Server zpracovává některé operace porovnání řetězců jinak než CLR. V SQL Server chování porovnání řetězců závisí na nastavení řazení na serveru. Další informace naleznete v [tématu Práce se řazením](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms187582(v=sql.105)) v microsoft sql server knihy online.  
  
- SQL Server může vrátit různé hodnoty pro některé namapované funkce než CLR. Například rovnost funkce se bude lišit, protože SQL Server považuje dva řetězce za rovné, pokud se liší pouze v koncové prázdné místo; vzhledem k tomu, že nařízení CLR je považuje za nerovné.  
  
<a name="EnumMapping"></a>
## <a name="enum-mapping"></a>Mapování výčtu  
 LINQ na SQL podporuje <xref:System.Enum?displayProperty=nameWithType> mapování typu CLR na typy SERVERU SQL server dvěma způsoby:  
  
- Mapování na číselné`TINYINT` `SMALLINT`typy `INT` `BIGINT`SQL ( , , , )  
  
     Když mapujete <xref:System.Enum?displayProperty=nameWithType> typ CLR na číselný typ SQL, namapujete <xref:System.Enum?displayProperty=nameWithType> základní celou hodnotu CLR na hodnotu sloupce databáze serveru SQL Server. Například pokud <xref:System.Enum?displayProperty=nameWithType> pojmenovaný `DaysOfWeek` obsahuje člen `Tue` pojmenovaný s základní celá hodnota 3, tento člen mapuje na databázovou hodnotu 3.  
  
- Mapování na typy`CHAR`textu `NCHAR` `VARCHAR`SQL `NVARCHAR`( , , , )  
  
     Když namapujete <xref:System.Enum?displayProperty=nameWithType> typ CLR na typ textu SQL, hodnota databáze SQL <xref:System.Enum?displayProperty=nameWithType> je mapována na názvy členů CLR. Například pokud <xref:System.Enum?displayProperty=nameWithType> pojmenovaný `DaysOfWeek` obsahuje člen `Tue` pojmenovaný s základní celá hodnota 3, tento člen `Tue`mapuje na databázovou hodnotu .  
  
> [!NOTE]
> Při mapování typů textu SQL <xref:System.Enum?displayProperty=nameWithType>na CLR zahrňte do namapovaného sloupce SQL pouze jména <xref:System.Enum> členů. Ostatní hodnoty nejsou podporovány ve sloupci <xref:System.Enum>-mapované SQL.  
  
 Nástroj příkazového řádku O/R designeru a SQLMetal nemůže automaticky <xref:System.Enum> mapovat typ SQL na třídu CLR. Toto mapování je nutné explicitně nakonfigurovat přizpůsobením souboru DBML pro použití návrhářem O/R a sqlmetalem. Další informace o vlastním mapování typů naleznete v tématu [SQL-CLR Custom Type Mappings](sql-clr-custom-type-mappings.md).  
  
 Vzhledem k tomu, že sloupec SQL určený pro výčet bude stejného typu jako ostatní číselné a textové sloupce; Tyto nástroje nerozpoznají váš záměr a výchozí mapování, jak je popsáno v následujících oddílech [Číselné mapování](#NumericMapping) [a Text a Mapování XML.](#TextMapping) Další informace o generování kódu se souborem DBML naleznete [v tématu Generování kódu v LINQ na SQL](code-generation-in-linq-to-sql.md).  
  
 Metoda <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> vytvoří sloupec SQL číselného typu pro <xref:System.Enum?displayProperty=nameWithType> mapování typu CLR.  
  
<a name="NumericMapping"></a>
## <a name="numeric-mapping"></a>Číselné mapování  
 LINQ na SQL umožňuje mapovat mnoho číselných typů CLR a SQL Server. V následující tabulce jsou uvedeny typy CLR, které o/R Designer a SQLMetal vybrat při vytváření objektového modelu nebo externí mapování souborzaložený na databázi.  
  
|Typ serveru SQL Server|Výchozí mapování typu CLR používané o/R designerem a SQLMetalem|  
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
  
 V následující tabulce jsou uvedeny výchozí <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> mapování typů používané metodou k definování typu sloupců SQL, které jsou vytvořeny k mapování na typy CLR definované v objektovém modelu nebo externím souboru mapování.  
  
|Typ CLR|Výchozí typ serveru SQL Server používaný<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
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
  
 Existuje mnoho dalších číselných mapování, které můžete zvolit, ale některé mohou mít za následek přetečení nebo ztrátu dat výjimky při překladu do nebo z databáze. Další informace naleznete v [matici chování](#BehaviorMatrix)chování typu Mapování běhu .  
  
### <a name="decimal-and-money-types"></a>Desetinné a peněžní typy  
 Výchozí přesnost typu `DECIMAL` SQL Server (18 desetinných míst vlevo a vpravo od desetinné čárky) <xref:System.Decimal?displayProperty=nameWithType> je mnohem menší než přesnost typu CLR, se kterou je ve výchozím nastavení spárován. To může mít za následek ztrátu přesnosti při ukládání dat do databáze. Však opak může dojít, pokud `DECIMAL` sql server typ je nakonfigurován s větší než 29 číslic přesnosti. Pokud byl `DECIMAL` typ serveru SQL Server nakonfigurován s <xref:System.Decimal?displayProperty=nameWithType>větší přesností než CLR , může dojít ke ztrátě přesnosti při načítání dat z databáze.  
  
 SQL Server `MONEY` `SMALLMONEY` a typy, které jsou také <xref:System.Decimal?displayProperty=nameWithType> spárovány s typem CLR ve výchozím nastavení, mají mnohem menší přesnost, což může mít za následek přetečení nebo ztrátu dat výjimky při ukládání dat do databáze.  
  
<a name="TextMapping"></a>
## <a name="text-and-xml-mapping"></a>Mapování textu a XML  
 Existuje také mnoho typů založených na textu a XML, které můžete mapovat pomocí LINQ na SQL. V následující tabulce jsou uvedeny typy CLR, které o/R Designer a SQLMetal vybrat při vytváření objektového modelu nebo externí mapování souborzaložený na databázi.  
  
|Typ serveru SQL Server|Výchozí mapování typu CLR používané o/R designerem a SQLMetalem|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 V následující tabulce jsou uvedeny výchozí <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> mapování typů používané metodou k definování typu sloupců SQL, které jsou vytvořeny k mapování na typy CLR definované v objektovém modelu nebo externím souboru mapování.  
  
|Typ CLR|Výchozí typ serveru SQL Server používaný<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=nameWithType>[]|`NVARCHAR(4000)`|  
|Vlastní typ `Parse()` implementace a`ToString()`|`NVARCHAR(MAX)`|  
  
 Existuje mnoho dalších mapování založených na textu a XML, které můžete zvolit, ale některé mohou mít za následek přetečení nebo výjimky ztráty dat při překladu do nebo z databáze. Další informace naleznete v [matici chování](#BehaviorMatrix)chování typu Mapování běhu .  
  
### <a name="xml-types"></a>Typy XML  
 Datový typ `XML` serveru SQL Server je k dispozici počínaje serverem Microsoft SQL Server 2005. Datový typ serveru `XML` SQL Server <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>můžete <xref:System.String>namapovat na aplikace , nebo . Pokud sloupec ukládá fragmenty XML, <xref:System.Xml.Linq.XElement>do kterých nelze číst <xref:System.String> , musí být sloupec mapován, aby se zabránilo chybám za běhu. Fragmenty XML, které musí <xref:System.String> být mapovány tak, aby zahrnovaly následující:  
  
- Posloupnost elementů XML  
  
- Atributy  
  
- Veřejné identifikátory (PI)  
  
- Komentáře  
  
 Přestože můžete <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> mapovat a sql server, jak je znázorněno v [matici chování chování typu mapování času běhu](#BehaviorMatrix), <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda nemá žádné výchozí mapování typu SQL Server pro tyto typy.  
  
### <a name="custom-types"></a>Vlastní typy  
 Pokud `Parse()` třída implementuje a `ToString()`, můžete objekt namapovat na libovolný text TEXTU SQL (`CHAR`, `NCHAR`, `VARCHAR` `NVARCHAR`, `TEXT`, `NTEXT`, ). `XML` Objekt je uložen v databázi odesláním `ToString()` hodnoty vrácené do sloupce mapované databáze. Objekt je rekonstruován `Parse()` vyvoláním na řetězec vrácený databází.  
  
> [!NOTE]
> LINQ to SQL nepodporuje serializaci pomocí <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.  
  
<a name="DateMapping"></a>
## <a name="date-and-time-mapping"></a>Mapování data a času  
 S LINQ na SQL, můžete mapovat mnoho SQL Server data a času. V následující tabulce jsou uvedeny typy CLR, které o/R Designer a SQLMetal vybrat při vytváření objektového modelu nebo externí mapování souborzaložený na databázi.  
  
|Typ serveru SQL Server|Výchozí mapování typu CLR používané o/R designerem a SQLMetalem|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 V následující tabulce jsou uvedeny výchozí <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> mapování typů používané metodou k definování typu sloupců SQL, které jsou vytvořeny k mapování na typy CLR definované v objektovém modelu nebo externím souboru mapování.  
  
|Typ CLR|Výchozí typ serveru SQL Server používaný<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 Existuje mnoho dalších mapování data a času, které můžete zvolit, ale některé mohou mít za následek přetečení nebo ztrátu dat výjimky při překladu do nebo z databáze. Další informace naleznete v [matici chování](#BehaviorMatrix)chování typu Mapování běhu .  
  
> [!NOTE]
> `DATETIME2`Typy serveru SQL `DATETIMEOFFSET` `DATE`Server `TIME` , , a jsou k dispozici počínaje serverem Microsoft SQL Server 2008. LINQ na SQL podporuje mapování na tyto nové typy počínaje rozhraním .NET Framework verze 3.5 SP1.  
  
### <a name="systemdatetime"></a>System.datetime  
 Rozsah a přesnost typu <xref:System.DateTime?displayProperty=nameWithType> CLR je větší než rozsah a `DATETIME` přesnost typu SQL Server, <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> což je výchozí mapování typu pro metodu. Chcete-li se vyhnout výjimkám souvisejícím s daty mimo rozsah aplikace `DATETIME`, použijte `DATETIME2`program , který je k dispozici počínaje serverem Microsoft SQL Server 2008. `DATETIME2`může odpovídat rozsahu a přesnosti CLR <xref:System.DateTime?displayProperty=nameWithType>.  
  
 Sql Server data nemají <xref:System.TimeZone>žádnou koncepci , funkce, která je bohatě podporována v CLR. <xref:System.TimeZone>hodnoty jsou uloženy stejně <xref:System.TimeZone> jako do databáze <xref:System.DateTimeKind> bez převodu, bez ohledu na původní informace. Při <xref:System.DateTime> načítání hodnot z databáze, jejich hodnota je <xref:System.DateTime> načtena, jak je do s <xref:System.DateTimeKind> a <xref:System.DateTimeKind.Unspecified>. Další informace o <xref:System.DateTime?displayProperty=nameWithType> podporovaných metodách naleznete v tématu [System.DateTime Methods](system-datetime-methods.md).  
  
### <a name="systemtimespan"></a>System.TimeSpan  
 Microsoft SQL Server 2008 a .NET Framework 3.5 SP1 umožňují mapovat typ CLR <xref:System.TimeSpan?displayProperty=nameWithType> na typ serveru SQL Server. `TIME` Existuje však velký rozdíl mezi rozsah, <xref:System.TimeSpan?displayProperty=nameWithType> který podporuje CLR `TIME` a co podporuje typ serveru SQL Server. Mapování hodnoty menší než 0 nebo větší než 23:59:59.9999999 hodin sql `TIME` bude mít za následek výjimky přetečení. Další informace naleznete v tématu [System.TimeSpan Methods](system-timespan-methods.md).  
  
 V aplikacích Microsoft SQL Server 2000 a SQL Server <xref:System.TimeSpan>2005 nelze mapovat databázová pole na aplikaci . Operace na <xref:System.TimeSpan> jsou však podporovány, protože <xref:System.TimeSpan> hodnoty mohou být vráceny z <xref:System.DateTime> odčítání nebo zavedeny do výrazu jako literál nebo vázaná proměnná.  
  
<a name="BinaryMapping"></a>
## <a name="binary-mapping"></a>Binární mapování  
 Existuje mnoho typů SQL Server, které lze <xref:System.Data.Linq.Binary?displayProperty=nameWithType>mapovat na typ CLR . V následující tabulce jsou uvedeny typy serveru SQL Server, které <xref:System.Data.Linq.Binary?displayProperty=nameWithType> způsobují, že O/R Designer a SQLMetal definují typ CLR při vytváření objektového modelu nebo externího mapovacího souboru založeného na databázi.  
  
|Typ serveru SQL Server|Výchozí mapování typu CLR používané o/R designerem a SQLMetalem|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`s `FILESTREAM` atributem|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 V následující tabulce jsou uvedeny výchozí <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> mapování typů používané metodou k definování typu sloupců SQL, které jsou vytvořeny k mapování na typy CLR definované v objektovém modelu nebo externím souboru mapování.  
  
|Typ CLR|Výchozí typ serveru SQL Server používaný<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 Existuje mnoho dalších binární mapování můžete zvolit, ale některé mohou mít za následek přetečení nebo ztrátu dat výjimky při překladu do nebo z databáze. Další informace naleznete v [matici chování](#BehaviorMatrix)chování typu Mapování běhu .  
  
### <a name="sql-server-filestream"></a>SQL Server FILESTREAM  
 Atribut `FILESTREAM` pro `VARBINARY(MAX)` sloupce je k dispozici počínaje serverem Microsoft SQL Server 2008. můžete na něj mapovat pomocí linq na SQL počínaje rozhraním .NET Framework verze 3.5 SP1.  
  
 Přestože můžete `VARBINARY(MAX)` mapovat `FILESTREAM` sloupce <xref:System.Data.Linq.Binary> s <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> atributem na objekty, `FILESTREAM` metoda nemůže automaticky vytvářet sloupce s atributem. Další informace `FILESTREAM`naleznete v [tématu FILESTREAM Overview](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb933993(v=sql.105)).  
  
<a name="BinarySerialization"></a>
### <a name="binary-serialization"></a>Binární serializace  
 Pokud <xref:System.Runtime.Serialization.ISerializable> třída implementuje rozhraní, můžete serializovat objekt do libovolného binárního pole SQL (`BINARY`, `VARBINARY`, `IMAGE`). Objekt je serializován a deserializován <xref:System.Runtime.Serialization.ISerializable> podle způsobu implementace rozhraní. Další informace naleznete [v tématu Binary Serialization](../../../../../standard/serialization/binary-serialization.md).
  
<a name="MiscMapping"></a>
## <a name="miscellaneous-mapping"></a>Různé mapování  
 V následující tabulce jsou uvedeny výchozí mapování typů pro některé různé typy, které ještě nebyly zmíněny. V následující tabulce jsou uvedeny typy CLR, které o/R Designer a SQLMetal vybrat při vytváření objektového modelu nebo externí mapování souborzaložený na databázi.  
  
|Typ serveru SQL Server|Výchozí mapování typu CLR používané o/R designerem a SQLMetalem|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 V následující tabulce jsou uvedeny výchozí <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> mapování typů používané metodou k definování typu sloupců SQL, které jsou vytvořeny k mapování na typy CLR definované v objektovém modelu nebo externím souboru mapování.  
  
|Typ CLR|Výchozí typ serveru SQL Server používaný<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 LINQ na SQL nepodporuje žádné jiné mapování typů pro tyto různé typy.  Další informace naleznete v [matici chování](#BehaviorMatrix)chování typu Mapování běhu .  
  
## <a name="see-also"></a>Viz také

- [Mapování na základě atributů](attribute-based-mapping.md)
- [Externí mapování](external-mapping.md)
- [Datové typy a funkce](data-types-and-functions.md)
- [Neshody typů SQL a CLR](sql-clr-type-mismatches.md)
