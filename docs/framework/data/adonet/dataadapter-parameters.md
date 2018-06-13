---
title: Parametry DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: ad046e4695365780bc6059617766a488ba85f642
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759368"
---
# <a name="dataadapter-parameters"></a>Parametry DataAdapter
<xref:System.Data.Common.DbDataAdapter> Má čtyři vlastnosti, které slouží k načtení dat z a aktualizovat data do zdroje dat: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> vlastnost vrací data ze zdroje dat; a <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, a <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> vlastnosti se používají ke správě změny ve zdroji dat. `SelectCommand` Musí být nastavena vlastnost před voláním `Fill` metodu `DataAdapter`. `InsertCommand`, `UpdateCommand`, Nebo `DeleteCommand` vlastnosti musí být nastavená před `Update` metodu `DataAdapter` je volána, v závislosti na tom, jaké změny byly provedeny k datům ve <xref:System.Data.DataTable>. Pokud byl přidán počet řádků, například `InsertCommand` musí být nastaven před voláním `Update`. Když `Update` zpracovává vložené, aktualizovaných nebo odstraněných řádků, `DataAdapter` používá příslušných `Command` vlastnost zpracovat akci. Aktuální informace o upravené řádek je předán `Command` objektu prostřednictvím `Parameters` kolekce.  
  
 Při aktualizaci řádek ve zdroji dat, zavoláte příkaz UPDATE, který používá jedinečný identifikátor pro identifikaci řádek v tabulce aktualizovat. Jedinečný identifikátor je obvykle hodnota pole primárního klíče. Příkaz UPDATE používá parametry, které obsahují jedinečný identifikátor a sloupců a hodnoty pro aktualizaci, jak je znázorněno v následujícím příkazu Transact-SQL.  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  Syntaxe parametru zástupné symboly závisí na zdroji dat. Tento příklad ukazuje zástupné symboly pro zdroj dat systému SQL Server. Použít zástupné znaky otazníku (?) pro <xref:System.Data.OleDb> a <xref:System.Data.Odbc> parametry.  
  
 V tomto příkladu jazyka Visual Basic `CompanyName` pole je aktualizováno s hodnotou `@CompanyName` parametr pro řádek kde `CustomerID` se rovná hodnotě `@CustomerID` parametr. Parametry načtení informací z řádku upravené pomocí <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> vlastnost <xref:System.Data.SqlClient.SqlParameter> objektu. Níže jsou uvedeny parametry pro předchozí příkaz Ukázka aktualizace. Kód předpokládá, že proměnná `adapter` představuje platnou <xref:System.Data.SqlClient.SqlDataAdapter> objektu.  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Add` Metodu `Parameters` kolekce přebírá název parametru, datový typ, velikost (Pokud je k dispozici typu) a název <xref:System.Data.Common.DbParameter.SourceColumn%2A> z `DataTable`. Všimněte si, že <xref:System.Data.Common.DbParameter.SourceVersion%2A> z `@CustomerID` parametr je nastaven na `Original`. To zaručuje, že se aktualizuje stávající řádek ve zdroji dat, došlo ke změně hodnoty identifikační sloupec nebo sloupce v upravenou <xref:System.Data.DataRow>. V takovém případě `Original` odpovídá hodnota řádku je aktuální hodnota ve zdroji dat a `Current` hodnota řádku by obsahovat aktualizované hodnoty. `SourceVersion` Pro `@CompanyName` parametr není nastaven a použije výchozí `Current` řádek hodnotu.  
  
> [!NOTE]
>  Pro oba `Fill` operace `DataAdapter` a `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ je odvozen od typu vrácená z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat. Odvozené [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy a metody přístupových objektů pro typy dat Microsoft SQL Server, technologie OLE DB a rozhraní ODBC jsou popsané v [mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter.SourceColumn Parameter.SourceVersion  
 `SourceColumn` a `SourceVersion` může být předána jako argumenty, které mají `Parameter` konstruktoru, nebo nastavit jako vlastnosti z existující `Parameter`. `SourceColumn` Je název <xref:System.Data.DataColumn> z <xref:System.Data.DataRow> kde hodnotu `Parameter` bude načten. `SourceVersion` Určuje `DataRow` verze, `DataAdapter` používá k načtení hodnoty.  
  
 Následující tabulce je zobrazena <xref:System.Data.DataRowVersion> hodnot výčtu, které jsou k dispozici pro použití s `SourceVersion`.  
  
|DataRowVersion – výčet|Popis|  
|--------------------------------|-----------------|  
|`Current`|Parametr používá aktuální hodnotu sloupce. Toto nastavení je výchozí.|  
|`Default`|Parametr používá `DefaultValue` sloupce.|  
|`Original`|Parametr používá původní hodnotu pro sloupec.|  
|`Proposed`|Parametr používá navrhované hodnotu.|  
  
 `SqlClient` Příklad kódu v další části definuje parametr pro <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> ve kterém `CustomerID` sloupec slouží jako `SourceColumn` pro dva parametry: `@CustomerID` (`SET CustomerID = @CustomerID`), a `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`). `@CustomerID` Parametr se používá k aktualizaci **CustomerID** sloupec, který se aktuální hodnota v `DataRow`. V důsledku toho `CustomerID` `SourceColumn` s `SourceVersion` z `Current` se používá. *@OldCustomerID* Parametr se používá k identifikaci na aktuálním řádku v datovém zdroji. Protože je nalezen odpovídající hodnota sloupce v `Original` verze řádku, stejné `SourceColumn` (`CustomerID`) s `SourceVersion` z `Original` se používá.  
  
## <a name="working-with-sqlclient-parameters"></a>Práce s parametry SqlClient  
 Následující příklad ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlDataAdapter> a nastavte <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> k <xref:System.Data.MissingSchemaAction.AddWithKey> Chcete-li získat další informace o schématu z databáze. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, A <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> sadu vlastností a jejich odpovídajících <xref:System.Data.SqlClient.SqlParameter> objektů přidaných do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce. Vrátí metodu `SqlDataAdapter` objektu.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>Zástupné symboly parametrů OleDb  
 Pro <xref:System.Data.OleDb.OleDbDataAdapter> a <xref:System.Data.Odbc.OdbcDataAdapter> objekty, musíte použít zástupné znaky otazníku (?) k identifikaci parametry.  
  
```vb  
Dim selectSQL As String = _  
  "SELECT CustomerID, CompanyName FROM Customers " & _  
  "WHERE CountryRegion = ? AND City = ?"  
Dim insertSQL AS String = _  
  "INSERT INTO Customers (CustomerID, CompanyName) VALUES (?, ?)"  
Dim updateSQL AS String = _  
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " & _  
  WHERE CustomerID = ?"  
Dim deleteSQL As String = "DELETE FROM Customers WHERE CustomerID = ?"  
```  
  
```csharp  
string selectSQL =   
  "SELECT CustomerID, CompanyName FROM Customers " +  
  "WHERE CountryRegion = ? AND City = ?";  
string insertSQL =   
  "INSERT INTO Customers (CustomerID, CompanyName) " +  
  "VALUES (?, ?)";  
string updateSQL =   
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " +  
  "WHERE CustomerID = ? ";  
string deleteSQL = "DELETE FROM Customers WHERE CustomerID = ?";  
```  
  
 Příkazy parametrizovaného dotazu definovat, které vstupní a výstupní parametry musí být vytvořen. Chcete-li vytvořit parametr, použijte `Parameters.Add` metoda nebo `Parameter` konstruktor a zadat název sloupce, datový typ a velikost. Pro vnitřní datové typy jako například `Integer`, není nutné zahrnovat velikost, nebo můžete zadat výchozí velikost.  
  
 Následující příklad kódu vytvoří parametry příkazu jazyka SQL a pak vyplní `DataSet`.  
  
## <a name="oledb-example"></a>Příklad OleDb  
  
```vb  
' Assumes that connection is a valid OleDbConnection object.  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter   
  
Dim selectCMD AS OleDbCommand = New OleDbCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add parameters and set values.  
selectCMD.Parameters.Add( _  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add( _  
  "@City", OleDbType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OleDbConnection object.  
OleDbDataAdapter adapter = new OleDbDataAdapter();  
  
OleDbCommand selectCMD = new OleDbCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
// Add parameters and set values.  
selectCMD.Parameters.Add(  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add(  
  "@City", OleDbType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
## <a name="odbc-parameters"></a>Parametry ODBC  
  
```vb  
' Assumes that connection is a valid OdbcConnection object.  
Dim adapter As OdbcDataAdapter = New OdbcDataAdapter  
  
Dim selectCMD AS OdbcCommand = New OdbcCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OdbcConnection object.  
OdbcDataAdapter adapter = new OdbcDataAdapter();  
  
OdbcCommand selectCMD = new OdbcCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
//Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
>  Pokud je název parametru není zadaný pro parametr, parametr dostane přírůstkové výchozí název parametru*N* *,* počínaje "Parameter1". Doporučujeme, abyste parametr*N* zásady vytváření názvů když zadáte název parametru, protože název, který zadáte může být v konfliktu s existujícím názvem výchozí parametr v `ParameterCollection`. Pokud se zadaným názvem již existuje, je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Úpravy dat pomocí uložených procedur](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [Mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
