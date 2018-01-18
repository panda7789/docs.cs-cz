---
title: "Konfigurace parametrů a datové typy parametrů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 537d8a2c-d40b-4000-83eb-bc1fcc93f707
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a71ba7ed12196184b7e826ed70c92a9873efdb0c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="configuring-parameters-and-parameter-data-types"></a>Konfigurace parametrů a datové typy parametrů
Příkaz objekty používají parametry k předání hodnoty do příkazů SQL nebo uložené procedury, kontrola typu a ověření. Na rozdíl od text příkazu parametr vstup považovat za literálovou hodnotou, ne jako spustitelný kód. To pomáhá chránit před útoky "Injektáž SQL", ve kterých útočník vloží příkaz tohoto ohrožení zabezpečení na serveru do příkazu SQL.  
  
 Parametrizované příkazy můžete také zvýšit výkon provádění dotazů, protože mohou pomoci přesně odpovídat příchozí příkaz s plán správné uložené v mezipaměti dotazu databázový server. Další informace najdete v tématu [provádění plánování ukládání do mezipaměti a opětovné používání](http://go.microsoft.com/fwlink/?LinkId=120424) a [parametry a provádění plánování opakovaně používat](http://go.microsoft.com/fwlink/?LinkId=120423) v SQL Server Books Online. Kromě výhody zabezpečení a výkonu parametrizované příkazy poskytují vhodnou metodu pro uspořádání předaných ke zdroji dat hodnot.  
  
 A <xref:System.Data.Common.DbParameter> objekt může být vytvořen pomocí jeho konstruktoru, nebo jejím přidáním do <xref:System.Data.Common.DbCommand.DbParameterCollection%2A> voláním `Add` metodu <xref:System.Data.Common.DbParameterCollection> kolekce. `Add` Metoda bude trvat jako vstupní argumenty konstruktoru nebo existujícího objektu parametr, v závislosti na zprostředkovateli data.  
  
## <a name="supplying-the-parameterdirection-property"></a>Poskytnutí vlastnost ParameterDirection  
 Při přidávání parametrů, je nutné zadat <xref:System.Data.ParameterDirection> vlastnost pro parametry než vstupní parametry. Následující tabulce je zobrazena `ParameterDirection` hodnoty, které můžete použít s <xref:System.Data.ParameterDirection> výčtu.  
  
|Název členu|Popis|  
|-----------------|-----------------|  
|<xref:System.Data.ParameterDirection.Input>|Parametr je vstupní parametr. Toto nastavení je výchozí.|  
|<xref:System.Data.ParameterDirection.InputOutput>|Parametr můžete provádět vstup a výstup.|  
|<xref:System.Data.ParameterDirection.Output>|Parametr je výstupní parametr.|  
|<xref:System.Data.ParameterDirection.ReturnValue>|Parametr reprezentuje návratovou hodnotu z operace jako jsou uložené procedury, integrovaná funkce nebo uživatelsky definované funkce.|  
  
## <a name="working-with-parameter-placeholders"></a>Práce se zástupnými symboly parametru  
 Syntaxe parametru zástupné symboly závisí na zdroji dat. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatelé dat zpracování pojmenování a určení parametrů a zástupné symboly parametrů jinak. Tuto syntaxi upravit tak, aby konkrétní zdroj dat., jak je popsáno v následující tabulce.  
  
|Zprostředkovatel dat|Syntaxe parametru pojmenování|  
|-------------------|-----------------------------|  
|<xref:System.Data.SqlClient>|Používá pojmenované parametry ve formátu `@` *parametername*.|  
|<xref:System.Data.OleDb>|Používá značky poziční parametr indikován otazník (`?`).|  
|<xref:System.Data.Odbc>|Používá značky poziční parametr indikován otazník (`?`).|  
|<xref:System.Data.OracleClient>|Používá pojmenované parametry ve formátu `:` *parmname* (nebo *parmname*).|  
  
## <a name="specifying-parameter-data-types"></a>Zadání parametru datové typy  
 Datový typ parametru je specifické pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dat zprostředkovatele. Určení typu převede hodnotu `Parameter` k [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ zprostředkovatele dat před předáním hodnota ke zdroji dat. Můžete také určit typ `Parameter` obecné způsobem nastavením `DbType` vlastnost `Parameter` objekt, který má určitý <xref:System.Data.DbType>.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Datový typ zprostředkovatele `Parameter` objektu je odvozeno z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ `Value` z `Parameter` objekt, nebo z `DbType` z `Parameter` objektu. V následující tabulce jsou uvedeny odvozené `Parameter` typ založen na objekt předaný jako `Parameter` hodnotu nebo zadaný `DbType`.  
  
|Typ rozhraní .NET Framework|DbType|SqlDbType|OleDbType|OdbcType|OracleType|  
|-------------------------|------------|---------------|---------------|--------------|----------------|  
|<xref:System.Boolean>|Boolean|Bit|Boolean|Bit|Byte|  
|<xref:System.Byte>|Byte|TinyInt|UnsignedTinyInt|TinyInt|Byte|  
|Byte]|binární|VarBinary`.` tento implicitní převod se nezdaří, pokud bajtové pole je větší než maximální velikost parametru VarBinary, což je 8 000 bajtů. Bajtová pole větší než 8 000 bajtů, explicitně nastavit <xref:System.Data.SqlDbType>.|VarBinary|binární|Nezpracovaná|  
|<xref:System.Char>|``|Odvození <xref:System.Data.SqlDbType> z char není podporován.|Char|Char|Byte|  
|<xref:System.DateTime>|DateTime|DateTime|DBTimeStamp|DateTime|DateTime|  
|<xref:System.DateTimeOffset>|DateTimeOffset|Datový typ DateTimeOffset v systému SQL Server 2008. Odvození <xref:System.Data.SqlDbType> z DateTimeOffset není podporována ve verzích systému SQL Server starších než SQL Server 2008.|||DateTime|  
|<xref:System.Decimal>|Desetinné číslo|Desetinné číslo|Desetinné číslo|číselné|Číslo|  
|<xref:System.Double>|Double|Plovoucí desetinná čárka|Double|Double|Double|  
|<xref:System.Single>|Single|Skutečné|Single|Skutečné|Plovoucí desetinná čárka|  
|<xref:System.Guid>|Identifikátor GUID|Typ UniqueIdentifier|Identifikátor GUID|Typ UniqueIdentifier|Nezpracovaná|  
|<xref:System.Int16 >|Int16|SmallInt|SmallInt|SmallInt|Int16|  
|<xref:System.Int32>|Int32|celá čísla|celá čísla|celá čísla|Int32|  
|<xref:System.Int64>|Int64|BigInt|BigInt|BigInt|Číslo|  
|<xref:System.Object>|Objekt|Variant|Variant|Odvození OdbcType: z objektu není podporováno.|Objekt BLOB|  
|<xref:System.String>|String|NVarChar. Tento implicitní převod se nezdaří, pokud řetězec je větší než maximální velikost NVarChar, což je 4 000 znaků. Pro větší než 4 000 znaků řetězce, explicitně nastavit <xref:System.Data.SqlDbType>.|VarWChar|NVarChar|NVarChar|  
|<xref:System.TimeSpan>|Čas|Čas v systému SQL Server 2008. Odvození <xref:System.Data.SqlDbType> z časový interval, není podporována ve verzích systému SQL Server starších než SQL Server 2008.|DBTime|Čas|DateTime|  
|<xref:System.UInt16>|UInt16|Odvození <xref:System.Data.SqlDbType> z UInt16 není podporován.|UnsignedSmallInt|celá čísla|UInt16|  
|<xref:System.UInt32>|UInt32|Odvození <xref:System.Data.SqlDbType> z UInt32 není podporován.|celé číslo bez znaménka|BigInt|UInt32|  
|<xref:System.UInt64>|UInt64|Odvození <xref:System.Data.SqlDbType> z UInt64 není podporován.|UnsignedBigInt|číselné|Číslo|  
||AnsiString|VarChar|VarChar|VarChar|VarChar|  
||AnsiStringFixedLength|Char|Char|Char|Char|  
|``|Měna|peníze|Měna|Odvození `OdbcType` z `Currency` není podporován.|Číslo|  
|``|Datum|Datum v systému SQL Server 2008. Odvození <xref:System.Data.SqlDbType> od data není podporována ve verzích systému SQL Server starších než SQL Server 2008.|DBDate|Datum|DateTime|  
|``|SByte|Odvození <xref:System.Data.SqlDbType> z SByte není podporován.|TinyInt|Odvození `OdbcType` z SByte není podporován.|SByte|  
||StringFixedLength|NChar|WChar|NChar|NChar|  
||Čas|Čas v systému SQL Server 2008. Odvození <xref:System.Data.SqlDbType> od času není podporována ve verzích systému SQL Server starších než SQL Server 2008.|DBTime|Čas|DateTime|  
||VarNumeric|Odvození <xref:System.Data.SqlDbType> z VarNumeric není podporován.|VarNumeric|Odvození `OdbcType` z VarNumeric není podporován.|Číslo|  
|uživatelem definovaný typ (objekt s<xref:Microsoft.SqlServer.Server.SqlUserDefinedAggregateAttribute>|Objekt nebo řetězec, v závislosti zprostředkovatele (SqlClient vždy vrátí hodnotu, k objektu, Odbc vždy vrátí řetězec, zprostředkovatele služeb OleDb spravovaná data můžete zobrazit buď|SqlDbType.Udt Pokud <xref:Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute> je přítomen, jinak hodnota typu Variant|OleDbType.VarWChar (Pokud je hodnota null) jinak OleDbType.Variant.|OdbcType.NVarChar|Nepodporuje se|  
  
> [!NOTE]
>  Převody z decimal na jiné typy jsou zužující převody, které zaokrouhlit Desítková hodnota směrem k nule na nejbližší celé číslo. Pokud není výsledek převodu reprezentovat cílového typu, <xref:System.OverflowException> je vyvolána výjimka.  
  
> [!NOTE]
>  Hodnota null parametru odešlete na server, je nutné zadat <xref:System.DBNull>, nikoli `null` (`Nothing` v [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]). Nulová hodnota v systému je prázdný objekt, který nemá žádnou hodnotu. <xref:System.DBNull>slouží k reprezentaci hodnoty null. Další informace o hodnoty Null databáze najdete v tématu [zpracování hodnot Null](../../../../docs/framework/data/adonet/sql/handling-null-values.md).  
  
## <a name="deriving-parameter-information"></a>Odvozování informace o parametrech  
 Parametry lze také odvodit z pomocí uložené procedury `DbCommandBuilder` třídy. Jak `SqlCommandBuilder` a `OleDbCommandBuilder` třídy zadejte statickou metodu `DeriveParameters`, který automaticky naplní kolekci parametrů příkazu objektu, který používá informace o parametrech z uložené procedury. Všimněte si, že `DeriveParameters` přepíše všechny stávající informace o parametr pro příkaz.  
  
> [!NOTE]
>  Odvozování informace o parametrech způsobuje snížení výkonu, protože vyžaduje další odezvy ke zdroji dat a načte informace. Pokud se informace o parametrech označuje v době návrhu, může zvýšit výkon vaší aplikace explicitně nastavením parametry.  
  
 Další informace najdete v tématu [generování příkazů s CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-parameters-with-a-sqlcommand-and-a-stored-procedure"></a>Použití parametrů SqlCommand a uložené procedury  
 Uložené procedury nabízí celou řadu výhod v datové aplikace. Pomocí uložené procedury databázových operací může být zapouzdřené v příkazu, optimalizované pro nejlepší výkon a rozšířené o zvýšení zabezpečení. I když uložené procedury nelze volat pomocí předání název uložené procedury následuje argumenty parametrů jako příkaz SQL pomocí <xref:System.Data.Common.DbCommand.Parameters%2A> kolekce [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.Common.DbCommand> objektu umožňuje více explicitně definovat uložené Parametry procedur a pro přístup k výstupní parametry a návratové hodnoty.  
  
> [!NOTE]
>  Parametrizované příkazy jsou spouštěny na serveru pomocí `sp_executesql,` což umožňuje pro opakované použití plánu dotazu. Místní kurzory nebo proměnných v `sp_executesql` dávky nejsou viditelné pro dávky, která volá `sp_executesql`. Změny v kontextu databáze poslední pouze na konci `sp_executesql` příkaz. Další informace najdete v tématu SQL Server Books Online.  
  
 Při použití parametrů s <xref:System.Data.SqlClient.SqlCommand> spuštění systému SQL Server uložené procedury, názvy parametrů přidán do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce musí odpovídat názvům značek parametrů v uložené proceduře. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server nepodporuje zástupné znaky otazníku (?) pro předávání parametrů příkazu SQL nebo uloženou proceduru. Ho pracuje s parametry v uložené proceduře jako pojmenované parametry a hledá odpovídající parametr značek. Například `CustOrderHist` uložená procedura se definuje pomocí parametr s názvem `@CustomerID`. Když váš kód provede uloženou proceduru, musíte také použít parametr s názvem `@CustomerID`.  
  
```  
CREATE PROCEDURE dbo.CustOrderHist @CustomerID varchar(5)  
```  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak volání procedury, SQL Server, které jsou uložené `Northwind` ukázkové databáze. Název uložené procedury je `dbo.SalesByCategory` a má vstupní parametr s názvem `@CategoryName` s typem dat `nvarchar(15)`. Kód vytvoří novou <xref:System.Data.SqlClient.SqlConnection> uvnitř pomocí blokovat tak, aby připojení je uvolněno při ukončení procesu. <xref:System.Data.SqlClient.SqlCommand> a <xref:System.Data.SqlClient.SqlParameter> objekty jsou vytvořené a nastavte jejich vlastnosti. A <xref:System.Data.SqlClient.SqlDataReader> provede `SqlCommand` a vrátí výsledek nastavit z uložené procedury, zobrazení výstupu v okně konzoly.  
  
> [!NOTE]
>  Místo vytváření `SqlCommand` a `SqlParameter` objekty a pak nastavení vlastnosti v samostatných příkazů, můžete místo toho vybrat, zda použít jednu z přetížené konstruktory pro nastavení více vlastností v jediném příkazu.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
## <a name="using-parameters-with-an-oledbcommand-or-odbccommand"></a>Pomocí parametrů s OleDbCommand nebo OdbcCommand  
 Při použití parametrů s <xref:System.Data.OleDb.OleDbCommand> nebo <xref:System.Data.Odbc.OdbcCommand>, pořadí parametrů přidán do `Parameters` kolekce musí odpovídat pořadí parametrů definovaných v uložené proceduře. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro OLE DB a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro ODBC zpracování parametrů v uložené proceduře jako zástupné symboly a použít hodnoty parametrů v pořadí. Kromě toho vrátí parametry s hodnotou musí být první parametry přidán do `Parameters` kolekce.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro OLE DB a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro ODBC nepodporují pojmenované parametry pro předávání parametrů příkazu SQL nebo uloženou proceduru. V takovém případě musíte použít zástupné znaky otazníku (?), jako v následujícím příkladu.  
  
```  
SELECT * FROM Customers WHERE CustomerID = ?  
```  
  
 V důsledku toho, v jakém pořadí `Parameter` objekty jsou přidány na `Parameters` kolekce musí odpovídat přímo pozici? Zástupný symbol pro parametr.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Parametry adaptéru dat](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [Mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
