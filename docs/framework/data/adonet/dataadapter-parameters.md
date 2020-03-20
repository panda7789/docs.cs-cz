---
title: Parametry adaptéru dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 9954570dcf33c5eea4dcccf880de2c307de0aeca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151543"
---
# <a name="dataadapter-parameters"></a>Parametry adaptéru dat
Má <xref:System.Data.Common.DbDataAdapter> čtyři vlastnosti, které se používají k načtení dat <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> ze zdroje dat a k aktualizaci dat: vlastnost vrátí data ze zdroje dat; a <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> vlastnosti <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> , a slouží ke správě změn ve zdroji dat. Vlastnost `SelectCommand` musí být nastavena `Fill` před voláním metody `DataAdapter`. `InsertCommand`Vlastnosti `UpdateCommand`, `DeleteCommand` nebo musí být `Update` nastaveny `DataAdapter` před voláním metody je volána, <xref:System.Data.DataTable>v závislosti na jaké změny byly provedeny v datech v . Pokud byly například přidány řádky, musí být `Update`před voláním `InsertCommand` nastavena sada . Při `Update` zpracování vložený, aktualizovaný nebo odstraněný `DataAdapter` řádek, `Command` používá příslušné vlastnosti ke zpracování akce. Aktuální informace o změněném řádku `Command` jsou `Parameters` předány objektu prostřednictvím kolekce.  
  
 Při aktualizaci řádku ve zdroji dat zavoláte příkaz UPDATE, který používá jedinečný identifikátor k identifikaci řádku v tabulce, který má být aktualizován. Jedinečný identifikátor je obvykle hodnota pole primárního klíče. Příkaz UPDATE používá parametry, které obsahují jedinečný identifikátor a sloupce a hodnoty, které mají být aktualizovány, jak je znázorněno v následujícím příkazu Transact-SQL.  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> Syntaxe pro zástupné symboly parametrů závisí na zdroji dat. Tento příklad ukazuje zástupné symboly pro zdroj dat serveru SQL Server. Použijte zástupné symboly otazníku (?) pro <xref:System.Data.OleDb> parametry. <xref:System.Data.Odbc>  
  
 V tomto `CompanyName` příkladu jazyka je pole aktualizováno `@CompanyName` hodnotou parametru pro řádek, kde `CustomerID` se rovná hodnotě parametru. `@CustomerID` Parametry načítají informace z upraveného řádku pomocí vlastnosti <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> objektu. <xref:System.Data.SqlClient.SqlParameter> Následují parametry pro předchozí ukázkový příkaz UPDATE. Kód předpokládá, že `adapter` proměnná <xref:System.Data.SqlClient.SqlDataAdapter> představuje platný objekt.  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 Metoda `Add` `Parameters` kolekce má název parametru, datový typ, velikost (pokud je to možné pro <xref:System.Data.Common.DbParameter.SourceColumn%2A> typ) `DataTable`a název z . Všimněte <xref:System.Data.Common.DbParameter.SourceVersion%2A> si, `@CustomerID` že parametr `Original`je nastavenna . To zaručuje, že existující řádek ve zdroji dat je aktualizován, pokud byla změněna <xref:System.Data.DataRow>hodnota identifikačního sloupce nebo sloupců v upraveném . V takovém případě `Original` by hodnota řádku odpovídala aktuální hodnotě `Current` ve zdroji dat a hodnota řádku by obsahovala aktualizovanou hodnotu. Parametr `SourceVersion` pro `@CompanyName` parametr není nastaven a `Current` používá výchozí hodnotu řádku.  
  
> [!NOTE]
> Pro `Fill` operace `DataAdapter` a `Get` metody `DataReader`, typ rozhraní .NET Framework je odvozen z typu vráceného od zprostředkovatele dat rozhraní .NET Framework. Odvozené typy rozhraní .NET Framework a metody přistupujícího modulu pro datové typy Serveru Microsoft SQL Server, OLE DB a ODBC jsou popsány v [části Mapování datových typů v ADO.NET](data-type-mappings-in-ado-net.md).  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parametr.SourceColumn, Parametr.SourceVersion  
 A `SourceColumn` `SourceVersion` může být předánjako argumenty konstruktoru `Parameter` nebo nastaveny `Parameter`jako vlastnosti existujícího . Je `SourceColumn` název <xref:System.Data.DataColumn> z kde <xref:System.Data.DataRow> `Parameter` bude načtena hodnota bude načtena. Určuje `SourceVersion` `DataRow` verzi, která `DataAdapter` používá k načtení hodnoty.  
  
 V následující tabulce <xref:System.Data.DataRowVersion> jsou uvedeny hodnoty `SourceVersion`výčtu, které jsou k dispozici pro použití s .  
  
|Výčet dataRowversion|Popis|  
|--------------------------------|-----------------|  
|`Current`|Parametr používá aktuální hodnotu sloupce. Toto nastavení je výchozí.|  
|`Default`|Parametr používá `DefaultValue` sloupec.|  
|`Original`|Parametr používá původní hodnotu sloupce.|  
|`Proposed`|Parametr používá navrhovanou hodnotu.|  
  
 Příklad `SqlClient` <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> kódu v další části definuje parametr, ve `CustomerID` kterém je `SourceColumn` sloupec použit jako `@CustomerID` `SET CustomerID = @CustomerID`pro dva`WHERE CustomerID = @OldCustomerID`parametry: ( ). `@OldCustomerID` Parametr `@CustomerID` se používá k aktualizaci sloupce **CustomerID** `DataRow`na aktuální hodnotu v rozhraní . V důsledku toho `CustomerID` `SourceColumn` se `SourceVersion` `Current` používá s a. Parametr `@OldCustomerID` slouží k identifikaci aktuálního řádku ve zdroji dat. Vzhledem k tomu, že `Original` odpovídající hodnota sloupce `SourceColumn` se`CustomerID`nachází `SourceVersion` ve `Original` verzi řádku, použije se stejná hodnota ( ) s a of.  
  
## <a name="working-with-sqlclient-parameters"></a>Práce s parametry sqlclientu  
 Následující příklad ukazuje, jak <xref:System.Data.SqlClient.SqlDataAdapter> vytvořit a <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> <xref:System.Data.MissingSchemaAction.AddWithKey> nastavit do, aby bylo možné načíst další informace o schématu z databáze. Sada <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>vlastností , <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>a <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> jejich <xref:System.Data.SqlClient.SqlParameter> odpovídající chráničů, které jsou přidány do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce. Metoda vrátí `SqlDataAdapter` objekt.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>Zástupné symboly parametrů OleDb  
 Pro <xref:System.Data.OleDb.OleDbDataAdapter> objekty a <xref:System.Data.Odbc.OdbcDataAdapter> je nutné k identifikaci parametrů použít zástupné symboly otazníku (?).  
  
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
  
 Parametrizované příkazy dotazu definují, které vstupní a výstupní parametry musí být vytvořeny. Chcete-li vytvořit parametr, použijte metodu `Parameters.Add` nebo `Parameter` konstruktor k určení názvu sloupce, datového typu a velikosti. Pro vnitřní datové typy, například `Integer`, není nutné zahrnout velikost nebo můžete zadat výchozí velikost.  
  
 Následující příklad kódu vytvoří parametry pro příkaz SQL `DataSet`a potom vyplní .  
  
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
  
## <a name="odbc-parameters"></a>Parametry Odbc  
  
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
> Pokud pro parametr není zadán název parametru, je mu přidělen přírůstkový výchozí název parametru*N* *,* počínaje parametrem "Parametr1". Doporučujeme vyhnout se konvence pojmenování parametru*N* při zadání názvu parametru, protože název, který `ParameterCollection`zadáte může být v konfliktu s existující výchozí název parametru v . Pokud zadaný název již existuje, je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Aktualizace zdrojů dat pomocí adaptérů dat](updating-data-sources-with-dataadapters.md)
- [Úpravy dat pomocí uložených procedur](modifying-data-with-stored-procedures.md)
- [Mapování datového typu v ADO.NET](data-type-mappings-in-ado-net.md)
- [Přehled ADO.NET](ado-net-overview.md)
