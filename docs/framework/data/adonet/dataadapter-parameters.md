---
title: Parametry adaptéru dat
description: Přečtěte si o vlastnostech objekt DbDataAdapter, které vracejí data ze zdroje dat, a spravujte změny ve zdroji dat.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 74b6787162b48f83a48127257dc8e23e31a859b7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286983"
---
# <a name="dataadapter-parameters"></a>Parametry adaptéru dat
<xref:System.Data.Common.DbDataAdapter>Má čtyři vlastnosti, které se používají k načtení dat z a aktualizace dat na zdroj dat: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> vlastnost vrací data ze zdroje dat a <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> vlastnosti, a <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> se používají ke správě změn ve zdroji dat. `SelectCommand`Vlastnost musí být nastavena před voláním `Fill` metody `DataAdapter` . `InsertCommand`Vlastnosti, `UpdateCommand` nebo `DeleteCommand` musí být nastaveny před `Update` `DataAdapter` voláním metody, v závislosti na tom, jaké změny byly provedeny v datech v <xref:System.Data.DataTable> . Například pokud byly přidány řádky, `InsertCommand` musí být nastavena před voláním `Update` . Při `Update` zpracovávání vloženého, aktualizovaného nebo odstraněného řádku `DataAdapter` používá příslušná `Command` vlastnost ke zpracování akce. Aktuální informace o změněném řádku jsou předány `Command` objektu prostřednictvím `Parameters` kolekce.  
  
 Když aktualizujete řádek ve zdroji dat, zavoláte příkaz UPDATE, který používá jedinečný identifikátor k identifikaci řádku v tabulce, která se má aktualizovat. Jedinečný identifikátor je obvykle hodnota pole primárního klíče. Příkaz UPDATE používá parametry, které obsahují jedinečný identifikátor i sloupce a hodnoty, které mají být aktualizovány, jak je znázorněno v následujícím příkazu jazyka Transact-SQL.  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> Syntaxe zástupných symbolů parametrů závisí na zdroji dat. Tento příklad ukazuje zástupné symboly pro zdroj dat SQL Server. Použijte zástupné symboly otazníku (?) pro <xref:System.Data.OleDb> <xref:System.Data.Odbc> parametry a.  
  
 V tomto Visual Basic příkladu `CompanyName` je pole aktualizováno hodnotou `@CompanyName` parametru pro řádek, který se `CustomerID` rovná hodnotě `@CustomerID` parametru. Parametry načítají informace ze změněného řádku pomocí <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> vlastnosti <xref:System.Data.SqlClient.SqlParameter> objektu. Níže jsou uvedené parametry předchozího příkazu Sample UPDATE. Kód předpokládá, že proměnná `adapter` představuje platný <xref:System.Data.SqlClient.SqlDataAdapter> objekt.  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Add`Metoda `Parameters` kolekce přebírá název parametru, datový typ, velikost (Pokud je k dispozici pro typ) a název <xref:System.Data.Common.DbParameter.SourceColumn%2A> z `DataTable` . Všimněte si, že <xref:System.Data.Common.DbParameter.SourceVersion%2A> `@CustomerID` parametr je nastaven na hodnotu `Original` . Tím se zaručí, že existující řádek ve zdroji dat se aktualizuje, pokud se v úpravě změnila hodnota určujícího sloupce nebo sloupce <xref:System.Data.DataRow> . V takovém případě bude `Original` hodnota řádku odpovídat aktuální hodnotě ve zdroji dat a `Current` hodnota řádku by obsahovala aktualizovanou hodnotu. `SourceVersion`Pro parametr není `@CompanyName` nastavená a používá výchozí `Current` hodnotu řádku.  
  
> [!NOTE]
> Pro `Fill` operace `DataAdapter` a `Get` metod `DataReader` , je typ .NET Framework odvozen od typu vráceného poskytovatelem dat .NET Framework. Odvozené .NET Framework typy a přístupové metody pro datové typy Microsoft SQL Server, OLE DB a ODBC jsou popsány v tématu [mapování datových typů v ADO.NET](data-type-mappings-in-ado-net.md).  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parametr. SourceColumn, Parameter. SourceVersion  
 `SourceColumn`A `SourceVersion` mohou být předány jako argumenty `Parameter` konstruktoru nebo nastaveny jako vlastnosti existující `Parameter` . `SourceColumn`Je název <xref:System.Data.DataColumn> z, <xref:System.Data.DataRow> kde `Parameter` bude načtena hodnota. `SourceVersion`Určuje `DataRow` verzi, kterou `DataAdapter` používá k načtení hodnoty.  
  
 V následující tabulce jsou uvedeny <xref:System.Data.DataRowVersion> hodnoty výčtu, které jsou k dispozici pro použití s `SourceVersion` .  
  
|Výčet DataRowVersion|Popis|  
|--------------------------------|-----------------|  
|`Current`|Parametr používá aktuální hodnotu sloupce. Toto nastavení je výchozí.|  
|`Default`|Parametr používá `DefaultValue` sloupec.|  
|`Original`|Parametr používá původní hodnotu sloupce.|  
|`Proposed`|Parametr používá navrhovanou hodnotu.|  
  
 `SqlClient`Příklad kódu v další části definuje parametr pro <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> , ve kterém `CustomerID` je sloupec použit jako `SourceColumn` pro dva parametry: `@CustomerID` ( `SET CustomerID = @CustomerID` ), a `@OldCustomerID` ( `WHERE CustomerID = @OldCustomerID` ). `@CustomerID`Parametr se používá k aktualizaci sloupce **KódZákazníka** na aktuální hodnotu v `DataRow` . Výsledkem je, že se `CustomerID` `SourceColumn` `SourceVersion` `Current` používá. `@OldCustomerID`Parametr slouží k identifikaci aktuálního řádku ve zdroji dat. Vzhledem k tomu, že hodnota odpovídajícího sloupce je nalezena ve `Original` verzi řádku, je použita stejná hodnota `SourceColumn` ( `CustomerID` ) s a `SourceVersion` `Original` .  
  
## <a name="working-with-sqlclient-parameters"></a>Práce s parametry SqlClient  
 Následující příklad ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlDataAdapter> a nastavit na, aby <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> <xref:System.Data.MissingSchemaAction.AddWithKey> bylo možné načíst další informace o schématu z databáze. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> Nastavení vlastností,, a <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> a jejich odpovídajících <xref:System.Data.SqlClient.SqlParameter> objektů přidaných do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce. Metoda vrací `SqlDataAdapter` objekt.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>Zástupné symboly parametrů OleDb  
 Pro <xref:System.Data.OleDb.OleDbDataAdapter> objekty a je <xref:System.Data.Odbc.OdbcDataAdapter> nutné použít zástupné symboly otazníku (?) k identifikaci parametrů.  
  
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
  
 Parametrizované příkazy dotazu definují, které vstupní a výstupní parametry je třeba vytvořit. Chcete-li vytvořit parametr, použijte `Parameters.Add` metodu nebo `Parameter` konstruktor k určení názvu, datového typu a velikosti sloupce. U vnitřních datových typů, například `Integer` nemusíte vkládat velikost, nebo můžete zadat výchozí velikost.  
  
 Následující příklad kódu vytvoří parametry pro příkaz SQL a pak vyplní `DataSet` .  
  
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
> Pokud není zadán název parametru pro parametr, je parametrem udělen přírůstkový výchozí název parametru*N* *,* počínaje hodnotou "parametr1". Doporučujeme vyhnout se zásadám vytváření názvů parametrů*N* , pokud zadáte název parametru, protože název, který zadáte, může být v konfliktu s existujícím výchozím názvem parametru v `ParameterCollection` . Pokud zadaný název již existuje, je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Aktualizace zdrojů dat pomocí adaptérů dat](updating-data-sources-with-dataadapters.md)
- [Úpravy dat pomocí uložených procedur](modifying-data-with-stored-procedures.md)
- [Mapování datového typu v ADO.NET](data-type-mappings-in-ado-net.md)
- [Přehled ADO.NET](ado-net-overview.md)
