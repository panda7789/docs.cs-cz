---
title: Parametry adaptéru dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: e633c7cdd105125fc5fb595566d15cf5f5fe4e6f
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47072456"
---
# <a name="dataadapter-parameters"></a>Parametry adaptéru dat
<xref:System.Data.Common.DbDataAdapter> Má čtyři vlastnosti, které slouží k načtení dat z a aktualizovat data do zdroje dat: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> vlastnost vrací data ze zdroje dat; a <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, a <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> vlastnosti se používají ke správě změny ve zdroji dat. `SelectCommand` Vlastnost musí být nastavena dříve než zavoláte `Fill` metodu `DataAdapter`. `InsertCommand`, `UpdateCommand`, Nebo `DeleteCommand` vlastnosti musí být nastavena před `Update` metodu `DataAdapter` je volána, v závislosti na tom, jaké změny byly provedeny s daty v <xref:System.Data.DataTable>. Například, pokud byl přidán počet řádků `InsertCommand` musí být nastavena dříve než zavoláte `Update`. Když `Update` zpracovává vložený, aktualizovaných nebo odstraněných řádků, `DataAdapter` používá funkcím `Command` vlastnost zpracovat akci. Aktuální informace o upravené řádku je předán `Command` objektu `Parameters` kolekce.  
  
 Při aktualizaci řádků ve zdroji dat zavoláte příkaz UPDATE, který používá k identifikaci odpovídající řádek v tabulce jedinečný identifikátor aktualizovat. Jedinečný identifikátor se obvykle hodnota primárního klíče. Příkaz UPDATE používá parametry, které obsahují jedinečný identifikátor a sloupců a hodnot má být aktualizován, jak je znázorněno v následujícím příkazu jazyka Transact-SQL.  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  Syntaxe pro parametr zástupné symboly závisí na zdroji dat. Tento příklad ukazuje zástupné symboly pro zdroj dat SQL serveru. Použít zástupné znaky otazníku (?) pro <xref:System.Data.OleDb> a <xref:System.Data.Odbc> parametry.  
  
 V tomto příkladu jazyka Visual Basic `CompanyName` pole se aktualizuje s hodnotou `@CompanyName` parametr řádku kde `CustomerID` se rovná hodnotě `@CustomerID` parametr. Parametry načíst informace z řádku upravené pomocí <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> vlastnost <xref:System.Data.SqlClient.SqlParameter> objektu. Následují parametry pro předchozí ukázka příkazu UPDATE. Kód předpokládá, že proměnná `adapter` představuje platnou <xref:System.Data.SqlClient.SqlDataAdapter> objektu.  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Add` Metodu `Parameters` kolekce má název parametru, datový typ a velikost (Pokud je k dispozici na typ) a název <xref:System.Data.Common.DbParameter.SourceColumn%2A> z `DataTable`. Všimněte si, že <xref:System.Data.Common.DbParameter.SourceVersion%2A> z `@CustomerID` parametr je nastaven na `Original`. Zaručí se tak, že pokud byla změněna hodnota identifikační sloupec nebo sloupce se aktualizuje existující řádek ve zdroji dat v upraveném <xref:System.Data.DataRow>. V takovém případě `Original` hodnota řádku odpovídají aktuální hodnotu ve zdroji dat a `Current` hodnota řádku by obsahoval aktualizovanou hodnotu. `SourceVersion` Pro `@CompanyName` není nastaven parametr a použije výchozí `Current` řádek hodnotu.  
  
> [!NOTE]
>  Pro obě `Fill` operací `DataAdapter` a `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ je odvozen od typu vráceného z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytovatele dat služeb. Odvozené [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy a přístupové metody pro datové typy systému Microsoft SQL Server, technologie OLE DB a rozhraní ODBC jsou popsány v [mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter.SourceColumn Parameter.SourceVersion  
 `SourceColumn` a `SourceVersion` může předávat jako argumenty, které mají `Parameter` konstruktoru nebo nastavte jako vlastnosti z existujícího `Parameter`. `SourceColumn` Je název <xref:System.Data.DataColumn> z <xref:System.Data.DataRow> kde hodnotu `Parameter` budou načítat. `SourceVersion` Určuje `DataRow` verze, která `DataAdapter` používá k načtení hodnoty.  
  
 Následující tabulka ukazuje <xref:System.Data.DataRowVersion> hodnot výčtu, které jsou k dispozici pro použití s `SourceVersion`.  
  
|Výčet DataRowVersion|Popis|  
|--------------------------------|-----------------|  
|`Current`|Parametr používá aktuální hodnotu sloupce. Toto nastavení je výchozí.|  
|`Default`|Používá parametr `DefaultValue` sloupce.|  
|`Original`|Parametr používá původní hodnota sloupce.|  
|`Proposed`|Parametr používá navrhovanou hodnotu.|  
  
 `SqlClient` Příklad kódu v další části definuje parametr pro <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> ve kterém `CustomerID` sloupec se používá jako `SourceColumn` pro dva parametry: `@CustomerID` (`SET CustomerID = @CustomerID`), a `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`). `@CustomerID` Parametr se používá k aktualizaci **CustomerID** sloupci je aktuální hodnota `DataRow`. V důsledku toho `CustomerID` `SourceColumn` s `SourceVersion` z `Current` se používá. `@OldCustomerID` Parametr se používá k identifikaci aktuální řádek ve zdroji dat. Protože se nachází na odpovídající hodnotu sloupce v `Original` verzi řádku, stejné `SourceColumn` (`CustomerID`) s `SourceVersion` z `Original` se používá.  
  
## <a name="working-with-sqlclient-parameters"></a>Práce s parametry SqlClient  
 Následující příklad ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlDataAdapter> a nastavit <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> k <xref:System.Data.MissingSchemaAction.AddWithKey> získat informace o dalším schématu z databáze. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, A <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> sadu vlastností a jejich odpovídající <xref:System.Data.SqlClient.SqlParameter> objekty přidané do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce. Metoda vrátí `SqlDataAdapter` objektu.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>Zástupné symboly parametr OleDb  
 Pro <xref:System.Data.OleDb.OleDbDataAdapter> a <xref:System.Data.Odbc.OdbcDataAdapter> objekty, je nutné použít zástupné znaky otazníku (?) k identifikaci parametry.  
  
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
  
 Příkazy parametrický dotaz definovat, která vstupní a výstupní parametry musí být vytvořeny. Chcete-li vytvořit parametr, použijte `Parameters.Add` metoda nebo `Parameter` konstruktor k určení názvu sloupce, datový typ a velikost. Pro vnitřní datové typy jako například `Integer`, není nutné zahrnout velikosti, nebo můžete zadat výchozí velikost.  
  
 Následující příklad kódu vytvoří parametry pro příkaz jazyka SQL a potom vyplní `DataSet`.  
  
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
>  Pokud není zadán název parametru pro parametr, parametr je přiřazen přírůstkové výchozí název parametru*N* *,* počínaje "Parametr1". Doporučujeme vám, že byste se vyhnout parametr*N* zásady vytváření názvů při zadání názvu parametru, protože může být název, který zadáte v konfliktu s existujícím názvem výchozí parametr v `ParameterCollection`. Pokud zadaný název již existuje, je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Úpravy dat pomocí uložených procedur](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [Mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
