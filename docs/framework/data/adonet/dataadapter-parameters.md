---
title: Parametry adaptéru dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: b8284f45d769f018655ee35a5f0b067703963634
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034486"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="15ef6-102">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="15ef6-102">DataAdapter Parameters</span></span>
<span data-ttu-id="15ef6-103"><xref:System.Data.Common.DbDataAdapter> Má čtyři vlastnosti, které slouží k načtení dat z a aktualizovat data do zdroje dat: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> vlastnost vrací data ze zdroje dat; a <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, a <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> vlastnosti se používají ke správě změny ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="15ef6-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="15ef6-104">`SelectCommand` Vlastnost musí být nastavena dříve než zavoláte `Fill` metodu `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="15ef6-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="15ef6-105">`InsertCommand`, `UpdateCommand`, Nebo `DeleteCommand` vlastnosti musí být nastavena před `Update` metodu `DataAdapter` je volána, v závislosti na tom, jaké změny byly provedeny s daty v <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="15ef6-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="15ef6-106">Například, pokud byl přidán počet řádků `InsertCommand` musí být nastavena dříve než zavoláte `Update`.</span><span class="sxs-lookup"><span data-stu-id="15ef6-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="15ef6-107">Když `Update` zpracovává vložený, aktualizovaných nebo odstraněných řádků, `DataAdapter` používá funkcím `Command` vlastnost zpracovat akci.</span><span class="sxs-lookup"><span data-stu-id="15ef6-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="15ef6-108">Aktuální informace o upravené řádku je předán `Command` objektu `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="15ef6-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="15ef6-109">Při aktualizaci řádků ve zdroji dat, je zavolat příkaz UPDATE, který používá k identifikaci odpovídající řádek v tabulce aktualizovat jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="15ef6-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="15ef6-110">Jedinečný identifikátor se obvykle hodnota primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="15ef6-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="15ef6-111">Příkaz UPDATE používá parametry, které obsahují jedinečný identifikátor a sloupců a hodnot má být aktualizován, jak je znázorněno v následujícím příkazu jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="15ef6-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  <span data-ttu-id="15ef6-112">Syntaxe pro parametr zástupné symboly závisí na zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="15ef6-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="15ef6-113">Tento příklad ukazuje zástupné symboly pro zdroj dat SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="15ef6-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="15ef6-114">Použít zástupné znaky otazníku (?) pro <xref:System.Data.OleDb> a <xref:System.Data.Odbc> parametry.</span><span class="sxs-lookup"><span data-stu-id="15ef6-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="15ef6-115">V tomto příkladu jazyka Visual Basic `CompanyName` pole se aktualizuje s hodnotou `@CompanyName` parametr řádku kde `CustomerID` se rovná hodnotě `@CustomerID` parametr.</span><span class="sxs-lookup"><span data-stu-id="15ef6-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="15ef6-116">Parametry načíst informace z řádku upravené pomocí <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> vlastnost <xref:System.Data.SqlClient.SqlParameter> objektu.</span><span class="sxs-lookup"><span data-stu-id="15ef6-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="15ef6-117">Následují parametry pro předchozí ukázka příkazu UPDATE.</span><span class="sxs-lookup"><span data-stu-id="15ef6-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="15ef6-118">Kód předpokládá, že proměnná `adapter` představuje platnou <xref:System.Data.SqlClient.SqlDataAdapter> objektu.</span><span class="sxs-lookup"><span data-stu-id="15ef6-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="15ef6-119">`Add` Metodu `Parameters` kolekce má název parametru, datový typ a velikost (Pokud je k dispozici na typ) a název <xref:System.Data.Common.DbParameter.SourceColumn%2A> z `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="15ef6-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="15ef6-120">Všimněte si, že <xref:System.Data.Common.DbParameter.SourceVersion%2A> z `@CustomerID` parametr je nastaven na `Original`.</span><span class="sxs-lookup"><span data-stu-id="15ef6-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="15ef6-121">Zaručí se tak, že pokud byla změněna hodnota identifikační sloupec nebo sloupce se aktualizuje existující řádek ve zdroji dat v upraveném <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="15ef6-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="15ef6-122">V takovém případě `Original` hodnota řádku odpovídají aktuální hodnotu ve zdroji dat a `Current` hodnota řádku by obsahoval aktualizovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15ef6-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="15ef6-123">`SourceVersion` Pro `@CompanyName` není nastaven parametr a použije výchozí `Current` řádek hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15ef6-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15ef6-124">Pro obě `Fill` operací `DataAdapter` a `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ je odvozen od typu vráceného z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytovatele dat služeb.</span><span class="sxs-lookup"><span data-stu-id="15ef6-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type is inferred from the type returned from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="15ef6-125">Odvozené [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy a přístupové metody pro datové typy systému Microsoft SQL Server, technologie OLE DB a rozhraní ODBC jsou popsány v [mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="15ef6-125">The inferred [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="15ef6-126">Parameter.SourceColumn Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="15ef6-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="15ef6-127">`SourceColumn` a `SourceVersion` může předávat jako argumenty, které mají `Parameter` konstruktoru nebo nastavte jako vlastnosti z existujícího `Parameter`.</span><span class="sxs-lookup"><span data-stu-id="15ef6-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="15ef6-128">`SourceColumn` Je název <xref:System.Data.DataColumn> z <xref:System.Data.DataRow> kde hodnotu `Parameter` budou načítat.</span><span class="sxs-lookup"><span data-stu-id="15ef6-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="15ef6-129">`SourceVersion` Určuje `DataRow` verze, která `DataAdapter` používá k načtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="15ef6-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="15ef6-130">Následující tabulka ukazuje <xref:System.Data.DataRowVersion> hodnot výčtu, které jsou k dispozici pro použití s `SourceVersion`.</span><span class="sxs-lookup"><span data-stu-id="15ef6-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="15ef6-131">DataRowVersion Enumeration</span><span class="sxs-lookup"><span data-stu-id="15ef6-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="15ef6-132">Popis</span><span class="sxs-lookup"><span data-stu-id="15ef6-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="15ef6-133">Parametr používá aktuální hodnotu sloupce.</span><span class="sxs-lookup"><span data-stu-id="15ef6-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="15ef6-134">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="15ef6-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="15ef6-135">Používá parametr `DefaultValue` sloupce.</span><span class="sxs-lookup"><span data-stu-id="15ef6-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="15ef6-136">Parametr používá původní hodnota sloupce.</span><span class="sxs-lookup"><span data-stu-id="15ef6-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="15ef6-137">Parametr používá navrhovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15ef6-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="15ef6-138">`SqlClient` Příklad kódu v další části definuje parametr pro <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> ve kterém `CustomerID` sloupec se používá jako `SourceColumn` pro dva parametry: `@CustomerID` (`SET CustomerID = @CustomerID`), a `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span><span class="sxs-lookup"><span data-stu-id="15ef6-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="15ef6-139">`@CustomerID` Parametr se používá k aktualizaci **CustomerID** sloupci je aktuální hodnota `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="15ef6-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="15ef6-140">V důsledku toho `CustomerID` `SourceColumn` s `SourceVersion` z `Current` se používá.</span><span class="sxs-lookup"><span data-stu-id="15ef6-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="15ef6-141">`@OldCustomerID` Parametr se používá k identifikaci aktuální řádek ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="15ef6-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="15ef6-142">Protože se nachází na odpovídající hodnotu sloupce v `Original` verzi řádku, stejné `SourceColumn` (`CustomerID`) s `SourceVersion` z `Original` se používá.</span><span class="sxs-lookup"><span data-stu-id="15ef6-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="15ef6-143">Práce s parametry SqlClient</span><span class="sxs-lookup"><span data-stu-id="15ef6-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="15ef6-144">Následující příklad ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlDataAdapter> a nastavit <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> k <xref:System.Data.MissingSchemaAction.AddWithKey> získat informace o dalším schématu z databáze.</span><span class="sxs-lookup"><span data-stu-id="15ef6-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="15ef6-145"><xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, A <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> sadu vlastností a jejich odpovídající <xref:System.Data.SqlClient.SqlParameter> objekty přidané do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="15ef6-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="15ef6-146">Metoda vrátí `SqlDataAdapter` objektu.</span><span class="sxs-lookup"><span data-stu-id="15ef6-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="15ef6-147">Zástupné symboly parametr OleDb</span><span class="sxs-lookup"><span data-stu-id="15ef6-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="15ef6-148">Pro <xref:System.Data.OleDb.OleDbDataAdapter> a <xref:System.Data.Odbc.OdbcDataAdapter> objekty, je nutné použít zástupné znaky otazníku (?) k identifikaci parametry.</span><span class="sxs-lookup"><span data-stu-id="15ef6-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="15ef6-149">Příkazy parametrický dotaz definovat, která vstupní a výstupní parametry musí být vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="15ef6-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="15ef6-150">Chcete-li vytvořit parametr, použijte `Parameters.Add` metoda nebo `Parameter` konstruktor k určení názvu sloupce, datový typ a velikost.</span><span class="sxs-lookup"><span data-stu-id="15ef6-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="15ef6-151">Pro vnitřní datové typy jako například `Integer`, není nutné zahrnout velikosti, nebo můžete zadat výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="15ef6-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="15ef6-152">Následující příklad kódu vytvoří parametry pro příkaz jazyka SQL a potom vyplní `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="15ef6-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="15ef6-153">Příklad OleDb</span><span class="sxs-lookup"><span data-stu-id="15ef6-153">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="15ef6-154">Parametry ODBC</span><span class="sxs-lookup"><span data-stu-id="15ef6-154">Odbc Parameters</span></span>  
  
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
>  <span data-ttu-id="15ef6-155">Pokud není zadán název parametru pro parametr, parametr je přiřazen přírůstkové výchozí název parametru*N* *,* počínaje "Parametr1".</span><span class="sxs-lookup"><span data-stu-id="15ef6-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="15ef6-156">Doporučujeme vám, že byste se vyhnout parametr*N* zásady vytváření názvů při zadání názvu parametru, protože může být název, který zadáte v konfliktu s existujícím názvem výchozí parametr v `ParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="15ef6-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="15ef6-157">Pokud zadaný název již existuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="15ef6-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ef6-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15ef6-158">See also</span></span>

- [<span data-ttu-id="15ef6-159">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="15ef6-159">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="15ef6-160">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="15ef6-160">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="15ef6-161">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="15ef6-161">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="15ef6-162">Úpravy dat pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="15ef6-162">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="15ef6-163">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15ef6-163">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="15ef6-164">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="15ef6-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
