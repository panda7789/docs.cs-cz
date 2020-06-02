---
title: Konfigurace parametrů a datových typů parametrů
description: Objekty příkazu používají parametry k předávání hodnot příkazům SQL nebo uloženým procedurám, což zajišťuje kontrolu a ověřování typu v ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 537d8a2c-d40b-4000-83eb-bc1fcc93f707
ms.openlocfilehash: a426eeae785274b0484a84a2fae2dce4572fb4c4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287113"
---
# <a name="configuring-parameters-and-parameter-data-types"></a>Konfigurace parametrů a datových typů parametrů

Objekty příkazu používají parametry k předávání hodnot příkazům SQL nebo uloženým procedurám, což zajišťuje kontrolu a ověřování typu. Na rozdíl od textu příkazu je vstup parametru považován za hodnotu literálu, nikoli jako spustitelný kód. To pomáhá chránit před útoky typu "injektáže SQL", kdy útočník vloží příkaz, který ohrozí zabezpečení serveru, do příkazu SQL.

Parametrizované příkazy mohou také zlepšit výkon při provádění dotazů, protože pomůžou databázovému serveru přesně odpovídat příchozímu příkazu s řádným plánem dotazů v mezipaměti. Další informace najdete v tématu [ukládání do mezipaměti, opakované](/sql/relational-databases/query-processing-architecture-guide#execution-plan-caching-and-reuse) použití a [parametry a opakované použití plánu](/sql/relational-databases/query-processing-architecture-guide#PlanReuse)spuštění. Kromě výhod zabezpečení a výkonu poskytují parametrizované příkazy pohodlný způsob, jak uspořádat hodnoty předané zdroji dat.

<xref:System.Data.Common.DbParameter>Objekt lze vytvořit pomocí jeho konstruktoru nebo jeho přidáním do objektu <xref:System.Data.Common.DbCommand.DbParameterCollection%2A> voláním `Add` metody <xref:System.Data.Common.DbParameterCollection> kolekce. `Add`Metoda provede jako vstup buď argumenty konstruktoru, nebo existující objekt parametru v závislosti na poskytovateli dat.

## <a name="supplying-the-parameterdirection-property"></a>Poskytnutí vlastnosti ParameterDirection

Při přidávání parametrů je nutné zadat <xref:System.Data.ParameterDirection> vlastnost pro jiné parametry než vstupní parametry. V následující tabulce jsou uvedeny `ParameterDirection` hodnoty, které lze použít s <xref:System.Data.ParameterDirection> výčtem.

|Název členu|Popis|
|-----------------|-----------------|
|<xref:System.Data.ParameterDirection.Input>|Parametr je vstupní parametr. Toto nastavení je výchozí.|
|<xref:System.Data.ParameterDirection.InputOutput>|Parametr může provádět vstup i výstup.|
|<xref:System.Data.ParameterDirection.Output>|Parametr je výstupní parametr.|
|<xref:System.Data.ParameterDirection.ReturnValue>|Parametr představuje návratovou hodnotu z operace, jako je uložená procedura, integrovaná funkce nebo uživatelsky definovaná funkce.|

## <a name="working-with-parameter-placeholders"></a>Práce se zástupnými symboly parametrů

Syntaxe zástupných symbolů parametrů závisí na zdroji dat. Poskytovatelé dat .NET Framework řídí pojmenování a zadání parametrů a zástupných symbolů parametrů odlišně. Tato syntaxe je přizpůsobená konkrétnímu zdroji dat, jak je popsáno v následující tabulce.

|Poskytovatel dat|Syntaxe pojmenovávání parametrů|
|-------------------|-----------------------------|
|<xref:System.Data.SqlClient>|Používá pojmenované parametry ve formátu `@` *ParameterName*.|
|<xref:System.Data.OleDb>|Používá poziční značky parametrů, které jsou označeny otazníkem ( `?` ).|
|<xref:System.Data.Odbc>|Používá poziční značky parametrů, které jsou označeny otazníkem ( `?` ).|
|<xref:System.Data.OracleClient>|Používá pojmenované parametry ve formátu `:` *parmname* (nebo *parmname*).|

## <a name="specifying-parameter-data-types"></a>Určení datových typů parametrů

Datový typ parametru je specifický pro poskytovatele .NET Framework dat. Určení typu převede hodnotu `Parameter` typu na .NET Framework typ poskytovatele dat před předáním hodnoty zdroji dat. Můžete také určit typ `Parameter` obecného způsobu nastavením `DbType` vlastnosti `Parameter` objektu na určitou hodnotu <xref:System.Data.DbType> .

Typ poskytovatele .NET Framework dat `Parameter` objektu je odvozený od .NET Frameworkho typu `Value` `Parameter` objektu nebo z `DbType` `Parameter` objektu. Následující tabulka ukazuje odvozený `Parameter` typ založený na objektu předaném jako `Parameter` hodnota nebo zadané `DbType` .

|Typ rozhraní .NET Framework|DbType|Platná|OleDbType|OdbcType:|OracleType|
|-------------------------|------------|---------------|---------------|--------------|----------------|
|<xref:System.Boolean>|Logická hodnota|40bitového|Logická hodnota|40bitového|Byte|
|<xref:System.Byte>|Byte|TinyInt|UnsignedTinyInt|TinyInt|Byte|
|Byte []|Binární|VarBinary. Pokud je bajtové pole větší než maximální velikost VarBinary, což je 8000 bajtů, tento implicitní převod selže. Pro Bajtová pole větší než 8000 bajtů nastavte explicitně <xref:System.Data.SqlDbType> .|VarBinary|Binární|Žádný|
|<xref:System.Char>| |Odvození od typu <xref:System.Data.SqlDbType> char není podporováno.|Char|Char|Byte|
|<xref:System.DateTime>|DateTime|DateTime|DBTimeStamp|DateTime|DateTime|
|<xref:System.DateTimeOffset>|DateTimeOffset|DateTimeOffset v SQL Server 2008. Odvození od typu <xref:System.Data.SqlDbType> DateTimeOffset není podporováno ve verzích SQL Server starších než SQL Server 2008.|||DateTime|
|<xref:System.Decimal>|Desetinné číslo|Desetinné číslo|Desetinné číslo|Numeric|Číslo|
|<xref:System.Double>|Double|Float|Double|Double|Double|
|<xref:System.Single>|Single|Skutečné|Single|Skutečné|Float|
|<xref:System.Guid>|Identifikátor GUID|UniqueIdentifier|Identifikátor GUID|UniqueIdentifier|Žádný|
|<xref:System.Int16>|Int16|SmallInt|SmallInt|SmallInt|Int16|
|<xref:System.Int32>|Int32|Int|Int|Int|Int32|
|<xref:System.Int64>|Int64|BigInt|BigInt|BigInt|Číslo|
|<xref:System.Object>|Objekt|Variantní|Variantní|Odvození OdbcType: z objektu není podporováno.|Objekt blob|
|<xref:System.String>|Řetězec|NVarChar. Tento implicitní převod se nezdaří, pokud je řetězec větší než maximální velikost NVarChar, což je 4000 znaků. Pro řetězce větší než 4000 znaků explicitně nastavte <xref:System.Data.SqlDbType> .|VarWChar|NVarChar|NVarChar|
|<xref:System.TimeSpan>|Čas|Čas v SQL Server 2008. Odvození typu <xref:System.Data.SqlDbType> z TimeSpan není podporováno ve verzích SQL Server starších než SQL Server 2008.|DBTime|Čas|DateTime|
|<xref:System.UInt16>|UInt16|Odvození <xref:System.Data.SqlDbType> od UInt16 se nepodporuje.|UnsignedSmallInt|Int|UInt16|
|<xref:System.UInt32>|UInt32|Odvození z typu <xref:System.Data.SqlDbType> UInt32 není podporováno.|UnsignedInt|BigInt|UInt32|
|<xref:System.UInt64>|UInt64|Odvození <xref:System.Data.SqlDbType> od UInt64 se nepodporuje.|UnsignedBigInt|Numeric|Číslo|
||AnsiString|VarChar|VarChar|VarChar|VarChar|
||AnsiStringFixedLength|Char|Char|Char|Char|
||Měna|Peněžní částka|Měna|Odvození `OdbcType` od `Currency` není podporováno.|Číslo|
||Datum|Datum v SQL Server 2008. Odvození <xref:System.Data.SqlDbType> od data není podporováno ve verzích SQL Server starších než SQL Server 2008.|DBDate|Datum|DateTime|
||SByte|Odvození <xref:System.Data.SqlDbType> od SByte se nepodporuje.|TinyInt|Odvození `OdbcType` od SByte se nepodporuje.|SByte|
||StringFixedLength|NChar|WChar|NChar|NChar|
||Čas|Čas v SQL Server 2008. Odvození <xref:System.Data.SqlDbType> od času není podporováno ve verzích SQL Server starších než SQL Server 2008.|DBTime|Čas|DateTime|
||VarNumeric|Odvození <xref:System.Data.SqlDbType> od VarNumeric se nepodporuje.|VarNumeric|Odvození `OdbcType` od VarNumeric se nepodporuje.|Číslo|
|uživatelsky definovaný typ (objekt s<xref:Microsoft.SqlServer.Server.SqlUserDefinedAggregateAttribute>|Objekt nebo řetězec, v závislosti na poskytovateli (SqlClient vždy vrátí objekt, rozhraní ODBC vždycky vrátí řetězec a zprostředkovatel spravovaných dat OleDb uvidí buď|SqlDbType. UDT <xref:Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute> , pokud je k dispozici, jinak varianta|OleDbType. VarWChar (Pokud je hodnota null) jinak OleDbType. variant.|OdbcType:. NVarChar|nepodporováno|

> [!NOTE]
> Převody z typu Decimal na jiné typy jsou zužující převody, které zaokrouhlují desítkovou hodnotu na nejbližší celočíselnou hodnotu směrem nula. Pokud výsledek převodu není reprezentovatelné v cílovém typu, <xref:System.OverflowException> je vyvolána výjimka.

> [!NOTE]
> Když odešlete hodnotu parametru s hodnotou null na server, je nutné zadat <xref:System.DBNull> , ne `null` ( `Nothing` v Visual Basic). Hodnota null v systému je prázdný objekt, který nemá žádnou hodnotu. <xref:System.DBNull>slouží k reprezentaci hodnot null. Další informace o hodnotách null databáze naleznete v tématu [zpracování hodnot null](./sql/handling-null-values.md).

## <a name="deriving-parameter-information"></a>Odvození informací o parametrech

Parametry lze také odvodit z uložené procedury pomocí `DbCommandBuilder` třídy. `SqlCommandBuilder` `OleDbCommandBuilder` Třídy i poskytují statickou metodu, `DeriveParameters` která automaticky naplní kolekci Parameters pro objekt příkazu, který používá informace o parametrech z uložené procedury. Všimněte si, že `DeriveParameters` přepíše všechny existující informace o parametrech pro příkaz.

> [!NOTE]
> Vyloučení informací o parametrech má vliv na výkon, protože ke zdroji dat vyžaduje další zpáteční cestu, aby se tyto informace načetly. Pokud jsou informace o parametrech známy v době návrhu, můžete zvýšit výkon aplikace nastavením parametrů explicitně.

Další informace najdete v tématu [generování příkazů pomocí CommandBuilders](generating-commands-with-commandbuilders.md).

## <a name="using-parameters-with-a-sqlcommand-and-a-stored-procedure"></a>Použití parametrů s metodami SqlCommand a uloženou procedurou

Uložené procedury nabízejí mnoho výhod v aplikacích řízených daty. Pomocí uložených procedur je možné databázové operace zapouzdřit do jediného příkazu, optimalizace pro zajištění nejlepšího výkonu a vylepšení s vyšším zabezpečením. I když uloženou proceduru lze volat předáním názvu uložené procedury následovaný argumenty parametru jako příkaz jazyka SQL, pomocí <xref:System.Data.Common.DbCommand.Parameters%2A> kolekce <xref:System.Data.Common.DbCommand> objektu ADO.NET můžete explicitně definovat parametry uložené procedury a získat přístup k výstupním parametrům a návratovým hodnotám.

> [!NOTE]
> Parametrizované příkazy jsou spouštěny na serveru pomocí příkazu `sp_executesql,` , který umožňuje opakované použití plánu dotazů. Místní kurzory nebo proměnné v `sp_executesql` dávce nejsou viditelné pro dávku, která volá `sp_executesql` . Změny v kontextu databáze poslední pouze na konci `sp_executesql` příkazu. Další informace naleznete v tématu [sp_executesql (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql).

Při použití parametrů s a <xref:System.Data.SqlClient.SqlCommand> ke spuštění uložené procedury SQL Server musí názvy parametrů přidaných do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce odpovídat názvům značek parametrů v uložené proceduře. .NET Framework Zprostředkovatel dat pro SQL Server nepodporuje zástupné znaky otazníku (?) pro předávání parametrů příkazu SQL nebo uložené proceduře. Zpracovává parametry v uložené proceduře jako pojmenované parametry a hledá vyhovující značky parametrů. Například `CustOrderHist` uložená procedura je definována pomocí parametru s názvem `@CustomerID` . Když váš kód provede uloženou proceduru, musí také použít parametr s názvem `@CustomerID` .

```sql
CREATE PROCEDURE dbo.CustOrderHist @CustomerID varchar(5)
```

### <a name="example"></a>Příklad

Tento příklad ukazuje, jak volat SQL Server uloženou proceduru v `Northwind` ukázkové databázi. Název uložené procedury je `dbo.SalesByCategory` a má vstupní parametr s názvem `@CategoryName` s datovým typem `nvarchar(15)` . Kód vytvoří nový <xref:System.Data.SqlClient.SqlConnection> uvnitř bloku using, aby připojení bylo uvolněno při ukončení procedury. <xref:System.Data.SqlClient.SqlCommand>Objekty a <xref:System.Data.SqlClient.SqlParameter> jsou vytvořeny a jejich vlastnosti nastaveny. <xref:System.Data.SqlClient.SqlDataReader>Provede `SqlCommand` a vrátí sadu výsledků z uložené procedury a zobrazí výstup v okně konzoly.

> [!NOTE]
> Namísto vytváření `SqlCommand` a `SqlParameter` nastavování objektů a pak nastavení vlastností v samostatných příkazech můžete místo toho použít jeden z přetížených konstruktorů k nastavení více vlastností v jednom příkazu.

[!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]

## <a name="using-parameters-with-an-oledbcommand-or-odbccommand"></a>Použití parametrů s OleDbCommand nebo OdbcCommand

Při použití parametrů s <xref:System.Data.OleDb.OleDbCommand> nebo se <xref:System.Data.Odbc.OdbcCommand> musí pořadí parametrů přidaných do `Parameters` kolekce shodovat s pořadím parametrů definovaných v uložené proceduře. .NET Framework Zprostředkovatel dat pro OLE DB a .NET Framework Zprostředkovatel dat pro rozhraní ODBC považovat parametry v uložené proceduře jako zástupné symboly a hodnoty parametrů v daném pořadí. Kromě toho musí být parametry návratové hodnoty prvními parametry přidanými do `Parameters` kolekce.

Zprostředkovatel dat .NET Framework pro OLE DB a .NET Framework Zprostředkovatel dat pro rozhraní ODBC nepodporují pojmenované parametry pro předávání parametrů příkazu SQL nebo uložené proceduře. V takovém případě je nutné použít zástupný znak otazník (?), jak je uvedeno v následujícím příkladu.

```sql
SELECT * FROM Customers WHERE CustomerID = ?
```

V důsledku toho je pořadí, ve kterém `Parameter` jsou objekty přidány do `Parameters` kolekce, musí přímo odpovídat pozici? zástupný symbol pro parametr

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

## <a name="odbc-example"></a>Příklad ODBC

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

## <a name="see-also"></a>Viz také

- [Příkazy a parametry](commands-and-parameters.md)
- [Parametry adaptéru dat](dataadapter-parameters.md)
- [Mapování datového typu v ADO.NET](data-type-mappings-in-ado-net.md)
- [Přehled ADO.NET](ado-net-overview.md)
