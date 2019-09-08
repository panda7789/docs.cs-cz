---
title: Parametry adaptéru dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 83fc3101b0eb428def6cbc446e634e9bb45de350
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785606"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="e5ce2-102">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="e5ce2-102">DataAdapter Parameters</span></span>
<span data-ttu-id="e5ce2-103"><xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>Má čtyři vlastnosti, které se používají k načtení dat z a aktualizace dat na zdroj dat: vlastnost vrací data ze zdroje dat a vlastnosti, a se používají ke správě. <xref:System.Data.Common.DbDataAdapter> změny ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="e5ce2-104">Vlastnost musí být nastavena před `Fill` voláním metody `DataAdapter`. `SelectCommand`</span><span class="sxs-lookup"><span data-stu-id="e5ce2-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="e5ce2-105">`Update` Vlastnosti `InsertCommand`, `UpdateCommand`nebo `DeleteCommand` musíbýtnastavenypřed<xref:System.Data.DataTable>voláním metody ,vzávislostinatom,`DataAdapter` jaké změny byly provedeny v datech v.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="e5ce2-106">Například pokud byly přidány řádky, `InsertCommand` musí být nastavena před voláním. `Update`</span><span class="sxs-lookup"><span data-stu-id="e5ce2-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="e5ce2-107">Při `Update` zpracovávání vloženého, aktualizovaného nebo odstraněného řádku `DataAdapter` používá příslušná `Command` vlastnost ke zpracování akce.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="e5ce2-108">Aktuální informace o změněném řádku jsou předány `Command` objektu `Parameters` prostřednictvím kolekce.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="e5ce2-109">Když aktualizujete řádek ve zdroji dat, zavoláte příkaz UPDATE, který používá jedinečný identifikátor k identifikaci řádku v tabulce, která se má aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="e5ce2-110">Jedinečný identifikátor je obvykle hodnota pole primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="e5ce2-111">Příkaz UPDATE používá parametry, které obsahují jedinečný identifikátor i sloupce a hodnoty, které mají být aktualizovány, jak je znázorněno v následujícím příkazu jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> <span data-ttu-id="e5ce2-112">Syntaxe zástupných symbolů parametrů závisí na zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="e5ce2-113">Tento příklad ukazuje zástupné symboly pro zdroj dat SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="e5ce2-114">Použijte zástupné symboly otazníku (? <xref:System.Data.OleDb> ) <xref:System.Data.Odbc> pro parametry a.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="e5ce2-115">V tomto Visual Basic `CompanyName` příkladu je pole aktualizováno hodnotou `@CompanyName` parametru pro řádek, `CustomerID` který se rovná hodnotě `@CustomerID` parametru.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="e5ce2-116">Parametry načítají informace ze změněného řádku pomocí <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> vlastnosti <xref:System.Data.SqlClient.SqlParameter> objektu.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="e5ce2-117">Níže jsou uvedené parametry předchozího příkazu Sample UPDATE.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="e5ce2-118">Kód předpokládá, že proměnná `adapter` představuje platný <xref:System.Data.SqlClient.SqlDataAdapter> objekt.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="e5ce2-119">Metoda kolekce přebírá název parametru, datový typ, velikost (Pokud je k dispozici pro typ) <xref:System.Data.Common.DbParameter.SourceColumn%2A> a `DataTable`název z. `Parameters` `Add`</span><span class="sxs-lookup"><span data-stu-id="e5ce2-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="e5ce2-120">Všimněte si, <xref:System.Data.Common.DbParameter.SourceVersion%2A> že `@CustomerID` parametr je nastaven na `Original`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="e5ce2-121">Tím se zaručí, že existující řádek ve zdroji dat se aktualizuje, pokud se v úpravě <xref:System.Data.DataRow>změnila hodnota určujícího sloupce nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="e5ce2-122">V takovém případě `Original` bude hodnota řádku odpovídat aktuální hodnotě ve zdroji dat `Current` a hodnota řádku by obsahovala aktualizovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="e5ce2-123">Pro parametr není nastavená `Current` a používá výchozí hodnotu řádku. `@CompanyName` `SourceVersion`</span><span class="sxs-lookup"><span data-stu-id="e5ce2-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5ce2-124">`Fill` Pro operace `DataAdapter` a`Get` metod ,jetyp.NETFrameworkodvozenodtypuvrácenéhoposkytovatelemdat.NETFramework.`DataReader`</span><span class="sxs-lookup"><span data-stu-id="e5ce2-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="e5ce2-125">Odvozené .NET Framework typy a přístupové metody pro datové typy Microsoft SQL Server, OLE DB a ODBC jsou popsány v tématu [mapování datových typů v ADO.NET](data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="e5ce2-125">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="e5ce2-126">Parametr. SourceColumn, Parameter. SourceVersion</span><span class="sxs-lookup"><span data-stu-id="e5ce2-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="e5ce2-127">A mohou být předány `Parameter`jako argumenty konstruktorunebonastavenyjakovlastnostiexistující.`Parameter` `SourceVersion` `SourceColumn`</span><span class="sxs-lookup"><span data-stu-id="e5ce2-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="e5ce2-128">`SourceColumn` Je název `Parameter` z, <xref:System.Data.DataRow> kde bude <xref:System.Data.DataColumn> načtena hodnota.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="e5ce2-129">Určuje verzi, kterou`DataAdapter` používá k načtení hodnoty. `DataRow` `SourceVersion`</span><span class="sxs-lookup"><span data-stu-id="e5ce2-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="e5ce2-130">V následující tabulce jsou uvedeny <xref:System.Data.DataRowVersion> hodnoty výčtu, které jsou k `SourceVersion`dispozici pro použití s.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="e5ce2-131">Výčet DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="e5ce2-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="e5ce2-132">Popis</span><span class="sxs-lookup"><span data-stu-id="e5ce2-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="e5ce2-133">Parametr používá aktuální hodnotu sloupce.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="e5ce2-134">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="e5ce2-135">Parametr používá `DefaultValue` sloupec.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="e5ce2-136">Parametr používá původní hodnotu sloupce.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="e5ce2-137">Parametr používá navrhovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="e5ce2-138">`SourceColumn` <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> `CustomerID` `@OldCustomerID` `@CustomerID` `WHERE CustomerID = @OldCustomerID``SET CustomerID = @CustomerID`Příklad kódu v další části definuje parametr pro, ve kterém je sloupec použit jako pro dva parametry: (), a (). `SqlClient`</span><span class="sxs-lookup"><span data-stu-id="e5ce2-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="e5ce2-139">Parametr se používá k aktualizaci sloupce **KódZákazníka** na `DataRow`aktuální hodnotu v. `@CustomerID`</span><span class="sxs-lookup"><span data-stu-id="e5ce2-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="e5ce2-140">`CustomerID` `SourceColumn` Výsledkem je`Current` , že`SourceVersion` se používá.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="e5ce2-141">`@OldCustomerID` Parametr slouží k identifikaci aktuálního řádku ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="e5ce2-142">Vzhledem k tomu, že hodnota odpovídajícího sloupce je `Original` nalezena ve verzi řádku, je použita `SourceColumn` stejná`CustomerID`hodnota `Original` () `SourceVersion` s a.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="e5ce2-143">Práce s parametry SqlClient</span><span class="sxs-lookup"><span data-stu-id="e5ce2-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="e5ce2-144">Následující příklad ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlDataAdapter> a <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> nastavit <xref:System.Data.MissingSchemaAction.AddWithKey> na, aby bylo možné načíst další informace o schématu z databáze.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="e5ce2-145"><xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>Nastavení vlastností, ,<xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>a a <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> jejich odpovídajících objektůpřidanýchdokolekce<xref:System.Data.SqlClient.SqlParameter>. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A></span><span class="sxs-lookup"><span data-stu-id="e5ce2-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="e5ce2-146">Metoda vrací `SqlDataAdapter` objekt.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="e5ce2-147">Zástupné symboly parametrů OleDb</span><span class="sxs-lookup"><span data-stu-id="e5ce2-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="e5ce2-148">Pro objekty <xref:System.Data.Odbc.OdbcDataAdapter> a je nutné použít zástupné symboly otazníku (?) k identifikaci parametrů. <xref:System.Data.OleDb.OleDbDataAdapter></span><span class="sxs-lookup"><span data-stu-id="e5ce2-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="e5ce2-149">Parametrizované příkazy dotazu definují, které vstupní a výstupní parametry je třeba vytvořit.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="e5ce2-150">Chcete-li vytvořit parametr, použijte `Parameters.Add` metodu `Parameter` nebo konstruktor k určení názvu, datového typu a velikosti sloupce.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="e5ce2-151">U vnitřních datových typů, například `Integer`nemusíte vkládat velikost, nebo můžete zadat výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="e5ce2-152">Následující příklad kódu vytvoří parametry pro příkaz SQL a pak vyplní `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="e5ce2-153">Příklad OleDb</span><span class="sxs-lookup"><span data-stu-id="e5ce2-153">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="e5ce2-154">Parametry ODBC</span><span class="sxs-lookup"><span data-stu-id="e5ce2-154">Odbc Parameters</span></span>  
  
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
> <span data-ttu-id="e5ce2-155">Pokud není zadán název parametru pro parametr, je parametrem udělen přírůstkový výchozí název parametru*N* *,* počínaje hodnotou "parametr1".</span><span class="sxs-lookup"><span data-stu-id="e5ce2-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="e5ce2-156">Doporučujeme vyhnout se zásadám vytváření názvů parametrů*N* , pokud zadáte název parametru, protože název, který zadáte, může být v konfliktu s existujícím výchozím názvem parametru `ParameterCollection`v.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="e5ce2-157">Pokud zadaný název již existuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e5ce2-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ce2-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5ce2-158">See also</span></span>

- [<span data-ttu-id="e5ce2-159">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="e5ce2-159">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="e5ce2-160">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="e5ce2-160">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="e5ce2-161">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="e5ce2-161">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="e5ce2-162">Úpravy dat pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="e5ce2-162">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="e5ce2-163">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e5ce2-163">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="e5ce2-164">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e5ce2-164">ADO.NET Overview</span></span>](ado-net-overview.md)
