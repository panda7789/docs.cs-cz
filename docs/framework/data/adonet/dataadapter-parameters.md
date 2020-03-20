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
# <a name="dataadapter-parameters"></a><span data-ttu-id="53d10-102">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="53d10-102">DataAdapter Parameters</span></span>
<span data-ttu-id="53d10-103">Má <xref:System.Data.Common.DbDataAdapter> čtyři vlastnosti, které se používají k načtení dat <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> ze zdroje dat a k aktualizaci dat: vlastnost vrátí data ze zdroje dat; a <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> vlastnosti <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> , a slouží ke správě změn ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="53d10-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="53d10-104">Vlastnost `SelectCommand` musí být nastavena `Fill` před voláním metody `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="53d10-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="53d10-105">`InsertCommand`Vlastnosti `UpdateCommand`, `DeleteCommand` nebo musí být `Update` nastaveny `DataAdapter` před voláním metody je volána, <xref:System.Data.DataTable>v závislosti na jaké změny byly provedeny v datech v .</span><span class="sxs-lookup"><span data-stu-id="53d10-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="53d10-106">Pokud byly například přidány řádky, musí být `Update`před voláním `InsertCommand` nastavena sada .</span><span class="sxs-lookup"><span data-stu-id="53d10-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="53d10-107">Při `Update` zpracování vložený, aktualizovaný nebo odstraněný `DataAdapter` řádek, `Command` používá příslušné vlastnosti ke zpracování akce.</span><span class="sxs-lookup"><span data-stu-id="53d10-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="53d10-108">Aktuální informace o změněném řádku `Command` jsou `Parameters` předány objektu prostřednictvím kolekce.</span><span class="sxs-lookup"><span data-stu-id="53d10-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="53d10-109">Při aktualizaci řádku ve zdroji dat zavoláte příkaz UPDATE, který používá jedinečný identifikátor k identifikaci řádku v tabulce, který má být aktualizován.</span><span class="sxs-lookup"><span data-stu-id="53d10-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="53d10-110">Jedinečný identifikátor je obvykle hodnota pole primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="53d10-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="53d10-111">Příkaz UPDATE používá parametry, které obsahují jedinečný identifikátor a sloupce a hodnoty, které mají být aktualizovány, jak je znázorněno v následujícím příkazu Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="53d10-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> <span data-ttu-id="53d10-112">Syntaxe pro zástupné symboly parametrů závisí na zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="53d10-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="53d10-113">Tento příklad ukazuje zástupné symboly pro zdroj dat serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="53d10-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="53d10-114">Použijte zástupné symboly otazníku (?) pro <xref:System.Data.OleDb> parametry. <xref:System.Data.Odbc></span><span class="sxs-lookup"><span data-stu-id="53d10-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="53d10-115">V tomto `CompanyName` příkladu jazyka je pole aktualizováno `@CompanyName` hodnotou parametru pro řádek, kde `CustomerID` se rovná hodnotě parametru. `@CustomerID`</span><span class="sxs-lookup"><span data-stu-id="53d10-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="53d10-116">Parametry načítají informace z upraveného řádku pomocí vlastnosti <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> objektu. <xref:System.Data.SqlClient.SqlParameter></span><span class="sxs-lookup"><span data-stu-id="53d10-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="53d10-117">Následují parametry pro předchozí ukázkový příkaz UPDATE.</span><span class="sxs-lookup"><span data-stu-id="53d10-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="53d10-118">Kód předpokládá, že `adapter` proměnná <xref:System.Data.SqlClient.SqlDataAdapter> představuje platný objekt.</span><span class="sxs-lookup"><span data-stu-id="53d10-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="53d10-119">Metoda `Add` `Parameters` kolekce má název parametru, datový typ, velikost (pokud je to možné pro <xref:System.Data.Common.DbParameter.SourceColumn%2A> typ) `DataTable`a název z .</span><span class="sxs-lookup"><span data-stu-id="53d10-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="53d10-120">Všimněte <xref:System.Data.Common.DbParameter.SourceVersion%2A> si, `@CustomerID` že parametr `Original`je nastavenna .</span><span class="sxs-lookup"><span data-stu-id="53d10-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="53d10-121">To zaručuje, že existující řádek ve zdroji dat je aktualizován, pokud byla změněna <xref:System.Data.DataRow>hodnota identifikačního sloupce nebo sloupců v upraveném .</span><span class="sxs-lookup"><span data-stu-id="53d10-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="53d10-122">V takovém případě `Original` by hodnota řádku odpovídala aktuální hodnotě `Current` ve zdroji dat a hodnota řádku by obsahovala aktualizovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="53d10-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="53d10-123">Parametr `SourceVersion` pro `@CompanyName` parametr není nastaven a `Current` používá výchozí hodnotu řádku.</span><span class="sxs-lookup"><span data-stu-id="53d10-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53d10-124">Pro `Fill` operace `DataAdapter` a `Get` metody `DataReader`, typ rozhraní .NET Framework je odvozen z typu vráceného od zprostředkovatele dat rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="53d10-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="53d10-125">Odvozené typy rozhraní .NET Framework a metody přistupujícího modulu pro datové typy Serveru Microsoft SQL Server, OLE DB a ODBC jsou popsány v [části Mapování datových typů v ADO.NET](data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="53d10-125">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="53d10-126">Parametr.SourceColumn, Parametr.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="53d10-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="53d10-127">A `SourceColumn` `SourceVersion` může být předánjako argumenty konstruktoru `Parameter` nebo nastaveny `Parameter`jako vlastnosti existujícího .</span><span class="sxs-lookup"><span data-stu-id="53d10-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="53d10-128">Je `SourceColumn` název <xref:System.Data.DataColumn> z kde <xref:System.Data.DataRow> `Parameter` bude načtena hodnota bude načtena.</span><span class="sxs-lookup"><span data-stu-id="53d10-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="53d10-129">Určuje `SourceVersion` `DataRow` verzi, která `DataAdapter` používá k načtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="53d10-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="53d10-130">V následující tabulce <xref:System.Data.DataRowVersion> jsou uvedeny hodnoty `SourceVersion`výčtu, které jsou k dispozici pro použití s .</span><span class="sxs-lookup"><span data-stu-id="53d10-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="53d10-131">Výčet dataRowversion</span><span class="sxs-lookup"><span data-stu-id="53d10-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="53d10-132">Popis</span><span class="sxs-lookup"><span data-stu-id="53d10-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="53d10-133">Parametr používá aktuální hodnotu sloupce.</span><span class="sxs-lookup"><span data-stu-id="53d10-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="53d10-134">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="53d10-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="53d10-135">Parametr používá `DefaultValue` sloupec.</span><span class="sxs-lookup"><span data-stu-id="53d10-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="53d10-136">Parametr používá původní hodnotu sloupce.</span><span class="sxs-lookup"><span data-stu-id="53d10-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="53d10-137">Parametr používá navrhovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="53d10-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="53d10-138">Příklad `SqlClient` <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> kódu v další části definuje parametr, ve `CustomerID` kterém je `SourceColumn` sloupec použit jako `@CustomerID` `SET CustomerID = @CustomerID`pro dva`WHERE CustomerID = @OldCustomerID`parametry: ( ). `@OldCustomerID`</span><span class="sxs-lookup"><span data-stu-id="53d10-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="53d10-139">Parametr `@CustomerID` se používá k aktualizaci sloupce **CustomerID** `DataRow`na aktuální hodnotu v rozhraní .</span><span class="sxs-lookup"><span data-stu-id="53d10-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="53d10-140">V důsledku toho `CustomerID` `SourceColumn` se `SourceVersion` `Current` používá s a.</span><span class="sxs-lookup"><span data-stu-id="53d10-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="53d10-141">Parametr `@OldCustomerID` slouží k identifikaci aktuálního řádku ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="53d10-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="53d10-142">Vzhledem k tomu, že `Original` odpovídající hodnota sloupce `SourceColumn` se`CustomerID`nachází `SourceVersion` ve `Original` verzi řádku, použije se stejná hodnota ( ) s a of.</span><span class="sxs-lookup"><span data-stu-id="53d10-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="53d10-143">Práce s parametry sqlclientu</span><span class="sxs-lookup"><span data-stu-id="53d10-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="53d10-144">Následující příklad ukazuje, jak <xref:System.Data.SqlClient.SqlDataAdapter> vytvořit a <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> <xref:System.Data.MissingSchemaAction.AddWithKey> nastavit do, aby bylo možné načíst další informace o schématu z databáze.</span><span class="sxs-lookup"><span data-stu-id="53d10-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="53d10-145">Sada <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>vlastností , <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>a <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> jejich <xref:System.Data.SqlClient.SqlParameter> odpovídající chráničů, které jsou přidány do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="53d10-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="53d10-146">Metoda vrátí `SqlDataAdapter` objekt.</span><span class="sxs-lookup"><span data-stu-id="53d10-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="53d10-147">Zástupné symboly parametrů OleDb</span><span class="sxs-lookup"><span data-stu-id="53d10-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="53d10-148">Pro <xref:System.Data.OleDb.OleDbDataAdapter> objekty a <xref:System.Data.Odbc.OdbcDataAdapter> je nutné k identifikaci parametrů použít zástupné symboly otazníku (?).</span><span class="sxs-lookup"><span data-stu-id="53d10-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="53d10-149">Parametrizované příkazy dotazu definují, které vstupní a výstupní parametry musí být vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="53d10-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="53d10-150">Chcete-li vytvořit parametr, použijte metodu `Parameters.Add` nebo `Parameter` konstruktor k určení názvu sloupce, datového typu a velikosti.</span><span class="sxs-lookup"><span data-stu-id="53d10-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="53d10-151">Pro vnitřní datové typy, například `Integer`, není nutné zahrnout velikost nebo můžete zadat výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="53d10-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="53d10-152">Následující příklad kódu vytvoří parametry pro příkaz SQL `DataSet`a potom vyplní .</span><span class="sxs-lookup"><span data-stu-id="53d10-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="53d10-153">Příklad OleDb</span><span class="sxs-lookup"><span data-stu-id="53d10-153">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="53d10-154">Parametry Odbc</span><span class="sxs-lookup"><span data-stu-id="53d10-154">Odbc Parameters</span></span>  
  
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
> <span data-ttu-id="53d10-155">Pokud pro parametr není zadán název parametru, je mu přidělen přírůstkový výchozí název parametru*N* *,* počínaje parametrem "Parametr1".</span><span class="sxs-lookup"><span data-stu-id="53d10-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="53d10-156">Doporučujeme vyhnout se konvence pojmenování parametru*N* při zadání názvu parametru, protože název, který `ParameterCollection`zadáte může být v konfliktu s existující výchozí název parametru v .</span><span class="sxs-lookup"><span data-stu-id="53d10-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="53d10-157">Pokud zadaný název již existuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="53d10-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d10-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="53d10-158">See also</span></span>

- [<span data-ttu-id="53d10-159">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="53d10-159">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="53d10-160">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="53d10-160">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="53d10-161">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="53d10-161">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="53d10-162">Úpravy dat pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="53d10-162">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="53d10-163">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="53d10-163">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="53d10-164">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="53d10-164">ADO.NET Overview</span></span>](ado-net-overview.md)
