---
title: Konfigurace parametrů a datové typy parametrů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 537d8a2c-d40b-4000-83eb-bc1fcc93f707
ms.openlocfilehash: e4414e33efb077e00e4b38e3e53d218ecd7343a7
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242045"
---
# <a name="configuring-parameters-and-parameter-data-types"></a>Konfigurace parametrů a datové typy parametrů

Objekty příkazů použít parametry k předání hodnoty příkazy SQL nebo úložné procedury, kontrolu typu a ověření. Na rozdíl od text příkazu vstupní parametr je považován za hodnotu literálu, nikoli jako spustitelný kód. To pomáhá chránit před útoky "Útok prostřednictvím injektáže SQL", ve kterých útočník vloží příkaz tohoto ohrožení zabezpečení na serveru do příkazu SQL.

Příkazy s parametry může také zvýšit výkon spuštění dotazů, protože mohou pomoci přesně odpovídat příchozí příkaz s plánem správné dotazu z mezipaměti databázového serveru. Další informace najdete v tématu [spuštění plánu ukládání do mezipaměti a opětovné používání](/sql/relational-databases/query-processing-architecture-guide#execution-plan-caching-and-reuse) a [parametry a provádění plán znovu použít](/sql/relational-databases/query-processing-architecture-guide#PlanReuse). Kromě výhod zabezpečení a výkonu příkazy s parametry poskytují vhodnou metodu pro uspořádání hodnoty předané ke zdroji dat.

A <xref:System.Data.Common.DbParameter> objekt může být vytvořen pomocí konstruktoru, nebo jejím přidáním na <xref:System.Data.Common.DbCommand.DbParameterCollection%2A> voláním `Add` metodu <xref:System.Data.Common.DbParameterCollection> kolekce. `Add` Metoda vezme jako vstupní argumenty konstruktoru nebo existující objekt parametr, v závislosti na poskytovateli data.

## <a name="supplying-the-parameterdirection-property"></a>Zadání vlastnosti ParameterDirection

Při přidávání parametrů, je nutné zadat <xref:System.Data.ParameterDirection> vlastnost pro parametry, než jsou vstupní parametry. Následující tabulka ukazuje `ParameterDirection` hodnoty, které můžete používat <xref:System.Data.ParameterDirection> výčtu.

|Název členu|Popis|
|-----------------|-----------------|
|<xref:System.Data.ParameterDirection.Input>|Parametr je vstupní parametr. Toto nastavení je výchozí.|
|<xref:System.Data.ParameterDirection.InputOutput>|Tento parametr můžete provádět vstup a výstup.|
|<xref:System.Data.ParameterDirection.Output>|Parametr je výstupní parametr.|
|<xref:System.Data.ParameterDirection.ReturnValue>|Parametr reprezentuje návratovou hodnotu z určité operace, například uložené procedury, integrovaná funkce nebo uživatelem definované funkce.|

## <a name="working-with-parameter-placeholders"></a>Práce se zástupnými symboly parametru

Syntaxe pro parametr zástupné symboly závisí na zdroji dat. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatelé dat zpracování pojmenování a určení parametrů a proměnných parametrů odlišně. Tato syntaxe upravit tak, aby konkrétnímu zdroji dat, jak je popsáno v následující tabulce.

|Zprostředkovatel dat|Pojmenování syntaxe parametru|
|-------------------|-----------------------------|
|<xref:System.Data.SqlClient>|Použití pojmenované parametry ve formátu `@` *parametername*.|
|<xref:System.Data.OleDb>|Používá značky pozičních parametrů více dopředu označeny otazníkem (`?`).|
|<xref:System.Data.Odbc>|Používá značky pozičních parametrů více dopředu označeny otazníkem (`?`).|
|<xref:System.Data.OracleClient>|Použití pojmenované parametry ve formátu `:` *parmname* (nebo *parmname*).|

## <a name="specifying-parameter-data-types"></a>Určení datové typy parametrů

Datový typ parametru je specifické pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytovatele dat služeb. Určení typu převede hodnotu `Parameter` k [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ zprostředkovatele dat před předáním této hodnoty ke zdroji dat. Můžete také zadat typ `Parameter` obecný způsobem tak, že nastavíte `DbType` vlastnost `Parameter` objekt ke konkrétní <xref:System.Data.DbType>.

[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Datovým typem zprostředkovatele `Parameter` objekt je odvozen z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ `Value` z `Parameter` objektu, nebo z `DbType` z `Parameter` objektu. V následující tabulce jsou uvedeny odvozené `Parameter` založený na objekt předaný jako typ `Parameter` hodnotu nebo zadaný `DbType`.

|Typ rozhraní .NET Framework|DbType|SqlDbType|OleDbType|OdbcType|OracleType|
|-------------------------|------------|---------------|---------------|--------------|----------------|
|<xref:System.Boolean>|Boolean|Bit|Boolean|Bit|Byte|
|<xref:System.Byte>|Byte|TinyInt|UnsignedTinyInt|TinyInt|Byte|
|Byte|binární|VarBinary. Toto implicitní převod selže, pokud bajtové pole je větší než maximální velikost parametru VarBinary, což je 8 000 bajtů. Bajtová pole větší než 8 000 bajtů, explicitně nastavit <xref:System.Data.SqlDbType>.|VarBinary|binární|nezpracované|
|<xref:System.Char>| |Odvození <xref:System.Data.SqlDbType> z char není podporován.|Char|Char|Byte|
|<xref:System.DateTime>|DateTime|DateTime|DBTimeStamp|DateTime|DateTime|
|<xref:System.DateTimeOffset>|DateTimeOffset|DateTimeOffset v systému SQL Server 2008. Odvození <xref:System.Data.SqlDbType> z DateTimeOffset není podporován ve verzích systému SQL Server starších než SQL Server 2008.|||DateTime|
|<xref:System.Decimal>|Desetinné číslo|Desetinné číslo|Desetinné číslo|Čísla|Číslo|
|<xref:System.Double>|Double|Float|Double|Double|Double|
|<xref:System.Single>|Single|Skutečné|Single|Skutečné|Float|
|<xref:System.Guid>|Guid|UniqueIdentifier|Guid|UniqueIdentifier|nezpracované|
|<xref:System.Int16>|Int16|SmallInt|SmallInt|SmallInt|Int16|
|<xref:System.Int32>|Int32|Int|Int|Int|Int32|
|<xref:System.Int64>|Int64|BigInt|BigInt|BigInt|Číslo|
|<xref:System.Object>|Objekt|Variant|Variant|Odvození OdbcType: z objektu se nepodporuje.|Objekt blob|
|<xref:System.String>|String|NVarChar. Toto implicitní převod se nezdaří, pokud řetězec je větší než maximální velikost NVarChar, což je 4000 znaků. Pro řetězce je větší než 4000 znaků, explicitně nastavit <xref:System.Data.SqlDbType>.|VarWChar|NVarChar|NVarChar|
|<xref:System.TimeSpan>|Čas|Čas v systému SQL Server 2008. Odvození <xref:System.Data.SqlDbType> z TimeSpan není podporován ve verzích systému SQL Server starších než SQL Server 2008.|DBTime|Čas|DateTime|
|<xref:System.UInt16>|UInt16|Odvození <xref:System.Data.SqlDbType> z UInt16 se nepodporuje.|UnsignedSmallInt|Int|UInt16|
|<xref:System.UInt32>|UInt32|Odvození <xref:System.Data.SqlDbType> z UInt32 se nepodporuje.|celé číslo bez znaménka|BigInt|UInt32|
|<xref:System.UInt64>|UInt64|Odvození <xref:System.Data.SqlDbType> z UInt64 se nepodporuje.|UnsignedBigInt|Čísla|Číslo|
||AnsiString|VarChar|VarChar|VarChar|VarChar|
||AnsiStringFixedLength|Char|Char|Char|Char|
||Měna|peníze|Měna|Odvození `OdbcType` z `Currency` se nepodporuje.|Číslo|
||Datum|Datum v systému SQL Server 2008. Odvození <xref:System.Data.SqlDbType> od data není podporováno ve verzích systému SQL Server starších než SQL Server 2008.|DBDate|Datum|DateTime|
||SByte|Odvození <xref:System.Data.SqlDbType> z SByte se nepodporuje.|TinyInt|Odvození `OdbcType` z SByte se nepodporuje.|SByte|
||StringFixedLength|nChar|WChar|nChar|nChar|
||Čas|Čas v systému SQL Server 2008. Odvození <xref:System.Data.SqlDbType> od času není podporováno ve verzích systému SQL Server starších než SQL Server 2008.|DBTime|Čas|DateTime|
||VarNumeric|Odvození <xref:System.Data.SqlDbType> z VarNumeric se nepodporuje.|VarNumeric|Odvození `OdbcType` z VarNumeric se nepodporuje.|Číslo|
|uživatelem definovaný typ (objekt s <xref:Microsoft.SqlServer.Server.SqlUserDefinedAggregateAttribute>|Objekt nebo řetězec, v závislosti poskytovatele (SqlClient vždy vrátí objekt, Odbc vždy vrátí hodnotu typu String a zprostředkovatele služeb OleDb spravovaných dat můžete zobrazit buď|SqlDbType.Udt Pokud <xref:Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute> je k dispozici, jinak Variant|OleDbType.VarWChar (Pokud je hodnota null) OleDbType.Variant jinak.|OdbcType.NVarChar|Nepodporuje se|

> [!NOTE]
> Převody z desítkové na jiné typy jsou zužující převody, které zaokrouhlit desítkovou hodnotu směrem k nule na nejbližší celočíselnou hodnotu. Pokud není výsledek převodu reprezentovat typem cílové <xref:System.OverflowException> je vyvolána výjimka.

> [!NOTE]
> Pokud je hodnota null parametru posíláte na server, je třeba zadat <xref:System.DBNull>, nikoli `null` (`Nothing` v jazyce Visual Basic). Hodnota null v systému je prázdný objekt, který nemá žádnou hodnotu. <xref:System.DBNull> slouží k reprezentaci hodnoty null. Další informace o databázi hodnoty Null, naleznete v tématu [zpracování hodnot Null](./sql/handling-null-values.md).

## <a name="deriving-parameter-information"></a>Odvozené informace o parametrech

Parametry lze také odvodit z uložené procedury pomocí `DbCommandBuilder` třídy. Jak `SqlCommandBuilder` a `OleDbCommandBuilder` třídy poskytují statické metody `DeriveParameters`, který automaticky naplní kolekci parametrů příkazový objekt, který používá informace o parametrech z uložené procedury. Všimněte si, že `DeriveParameters` přepíše všechny stávající informace o parametrech pro příkaz.

> [!NOTE]
> Odvozené informace o parametrech způsobuje snížení výkonu, protože vyžaduje další výměnu zpráv pro zdroj dat pro načtení informací. Pokud informace o parametrech je znám v době návrhu, můžete zvýšit výkon vaší aplikace tak, že nastavíte parametry explicitně.

Další informace najdete v tématu [generování příkazů s CommandBuilders](generating-commands-with-commandbuilders.md).

## <a name="using-parameters-with-a-sqlcommand-and-a-stored-procedure"></a>Pomocí parametrů s SqlCommand a uložené procedury

Uložené procedury nabízí celou řadu výhod v aplikace řízené daty. Pomocí uložených procedur databázových operací můžete být zapouzdřen v rámci jediného příkazu, optimalizované pro výkon a vylepšené o zvýšení zabezpečení. I když uložené procedury lze volat předáním názvu uložené procedury následuje argumenty jako příkaz jazyka SQL s použitím <xref:System.Data.Common.DbCommand.Parameters%2A> kolekce [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.Common.DbCommand> objektu umožňuje více explicitně definovat uložené parametry procedury a pro přístup k výstupní parametry a návratové hodnoty.

> [!NOTE]
> Parametrizované příkazy jsou spouštěny na serveru s použitím `sp_executesql,` tomu pro opakované použití plánu dotazu. Kurzory místní nebo v proměnné `sp_executesql` batch nejsou viditelné na službu batch, která volá `sp_executesql`. Poslední změny v kontextu databáze pouze na konec objektu `sp_executesql` příkazu. Další informace najdete v tématu [sp_executesql (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql).

Při použití s parametry <xref:System.Data.SqlClient.SqlCommand> ke spuštění systému SQL Server uložené procedury, názvy parametrů přidaných do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce musí shodovat s názvy značek parametr v uložené proceduře. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server nepodporuje otazník (?) zástupný symbol pro předání parametrů do příkazu SQL nebo uloženou proceduru. Považuje za parametry v uložené proceduře pojmenované parametry a hledá odpovídající parametr značek. Například `CustOrderHist` uloženou proceduru se definuje pomocí parametr s názvem `@CustomerID`. Pokud váš kód spustí uloženou proceduru, musíte taky použít parametr s názvem `@CustomerID`.

```sql
CREATE PROCEDURE dbo.CustOrderHist @CustomerID varchar(5)
```

### <a name="example"></a>Příklad

Tento příklad ukazuje, jak se volání procedury SQL serveru, které jsou uloženy `Northwind` ukázkovou databázi. Název uložené procedury je `dbo.SalesByCategory` a má vstupní parametr s názvem `@CategoryName` s datovým typem `nvarchar(15)`. Kód vytvoří novou <xref:System.Data.SqlClient.SqlConnection> uvnitř using blokovat tak, že připojení je uvolněna při ukončení procesu. <xref:System.Data.SqlClient.SqlCommand> a <xref:System.Data.SqlClient.SqlParameter> objekty jsou vytvořeny a nastavte jejich vlastnosti. A <xref:System.Data.SqlClient.SqlDataReader> provede `SqlCommand` a vrátí sadu z uložené procedury, v okně konzoly zobrazí výstup výsledků.

> [!NOTE]
> Místo vytváření `SqlCommand` a `SqlParameter` objekty a upravením vlastnosti v samostatných příkazů, můžete místo toho se rozhodnout využít jednu z přetížených konstruktorů pro nastavení více vlastností v jediném příkazu.

[!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]

## <a name="using-parameters-with-an-oledbcommand-or-odbccommand"></a>Pomocí parametrů s OleDbCommand nebo OdbcCommand

Při použití parametrů pomocí <xref:System.Data.OleDb.OleDbCommand> nebo <xref:System.Data.Odbc.OdbcCommand>, pořadí parametrů přidaných do `Parameters` kolekce musí odpovídat pořadí parametrů definovaných v uložené proceduře. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro OLE DB a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro ODBC považovat za parametry v uložené proceduře zástupné symboly a použít hodnoty parametrů v pořadí. Kromě toho vrátí parametry s hodnotou musí být první parametrů přidaných do `Parameters` kolekce.

[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro OLE DB a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro ODBC nepodporují pojmenované parametry pro předání parametrů do příkazu SQL nebo uloženou proceduru. V takovém případě musíte použít zástupný znak otazníku (?), jako v následujícím příkladu.

```sql
SELECT * FROM Customers WHERE CustomerID = ?
```

V důsledku toho pořadí, ve kterém `Parameter` objekty jsou přidány do `Parameters` kolekce musí odpovídat přímo do polohy? Zástupný symbol pro parametr.

### <a name="oledb-example"></a>Příklad OleDb

```vb
Dim command As OleDbCommand = New OleDbCommand( _
  "SampleProc", connection)
command.CommandType = CommandType.StoredProcedure

Dim parameter As OleDbParameter = command.Parameters.Add( _
  "RETURN_VALUE", OleDbType.Integer)
parameter.Direction = ParameterDirection.ReturnValue

parameter = command.Parameters.Add( _
  "@InputParm", OleDbType.VarChar, 12)
parameter.Value = "Sample Value"

parameter = command.Parameters.Add( _
  "@OutputParm", OleDbType.VarChar, 28)
parameter.Direction = ParameterDirection.Output
```

```csharp
OleDbCommand command = new OleDbCommand("SampleProc", connection);
command.CommandType = CommandType.StoredProcedure;

OleDbParameter parameter = command.Parameters.Add(
  "RETURN_VALUE", OleDbType.Integer);
parameter.Direction = ParameterDirection.ReturnValue;

parameter = command.Parameters.Add(
  "@InputParm", OleDbType.VarChar, 12);
parameter.Value = "Sample Value";

parameter = command.Parameters.Add(
  "@OutputParm", OleDbType.VarChar, 28);
parameter.Direction = ParameterDirection.Output;
```

## <a name="odbc-example"></a>Příklad rozhraní ODBC

```vb
Dim command As OdbcCommand = New OdbcCommand( _
  "{ ? = CALL SampleProc(?, ?) }", connection)
command.CommandType = CommandType.StoredProcedure

Dim parameter As OdbcParameter = command.Parameters.Add("RETURN_VALUE", OdbcType.Int)
parameter.Direction = ParameterDirection.ReturnValue

parameter = command.Parameters.Add( _
  "@InputParm", OdbcType.VarChar, 12)
parameter.Value = "Sample Value"

parameter = command.Parameters.Add( _
  "@OutputParm", OdbcType.VarChar, 28)
parameter.Direction = ParameterDirection.Output
```

```csharp
OdbcCommand command = new OdbcCommand( _
  "{ ? = CALL SampleProc(?, ?) }", connection);
command.CommandType = CommandType.StoredProcedure;

OdbcParameter parameter = command.Parameters.Add( _
  "RETURN_VALUE", OdbcType.Int);
parameter.Direction = ParameterDirection.ReturnValue;

parameter = command.Parameters.Add( _
  "@InputParm", OdbcType.VarChar, 12);
parameter.Value = "Sample Value";

parameter = command.Parameters.Add( _
  "@OutputParm", OdbcType.VarChar, 28);
parameter.Direction = ParameterDirection.Output;
```

## <a name="see-also"></a>Viz také:

- [Příkazy a parametry](commands-and-parameters.md)
- [Parametry adaptéru dat](dataadapter-parameters.md)
- [Mapování datového typu v ADO.NET](data-type-mappings-in-ado-net.md)
- [Přehled ADO.NET](ado-net-overview.md)
