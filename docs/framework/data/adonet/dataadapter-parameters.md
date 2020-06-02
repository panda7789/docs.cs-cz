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
# <a name="dataadapter-parameters"></a><span data-ttu-id="1c259-103">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="1c259-103">DataAdapter Parameters</span></span>
<span data-ttu-id="1c259-104"><xref:System.Data.Common.DbDataAdapter>Má čtyři vlastnosti, které se používají k načtení dat z a aktualizace dat na zdroj dat: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> vlastnost vrací data ze zdroje dat a <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> vlastnosti, a <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> se používají ke správě změn ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="1c259-104">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="1c259-105">`SelectCommand`Vlastnost musí být nastavena před voláním `Fill` metody `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="1c259-105">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="1c259-106">`InsertCommand`Vlastnosti, `UpdateCommand` nebo `DeleteCommand` musí být nastaveny před `Update` `DataAdapter` voláním metody, v závislosti na tom, jaké změny byly provedeny v datech v <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="1c259-106">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="1c259-107">Například pokud byly přidány řádky, `InsertCommand` musí být nastavena před voláním `Update` .</span><span class="sxs-lookup"><span data-stu-id="1c259-107">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="1c259-108">Při `Update` zpracovávání vloženého, aktualizovaného nebo odstraněného řádku `DataAdapter` používá příslušná `Command` vlastnost ke zpracování akce.</span><span class="sxs-lookup"><span data-stu-id="1c259-108">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="1c259-109">Aktuální informace o změněném řádku jsou předány `Command` objektu prostřednictvím `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="1c259-109">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="1c259-110">Když aktualizujete řádek ve zdroji dat, zavoláte příkaz UPDATE, který používá jedinečný identifikátor k identifikaci řádku v tabulce, která se má aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="1c259-110">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="1c259-111">Jedinečný identifikátor je obvykle hodnota pole primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="1c259-111">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="1c259-112">Příkaz UPDATE používá parametry, které obsahují jedinečný identifikátor i sloupce a hodnoty, které mají být aktualizovány, jak je znázorněno v následujícím příkazu jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="1c259-112">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> <span data-ttu-id="1c259-113">Syntaxe zástupných symbolů parametrů závisí na zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="1c259-113">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="1c259-114">Tento příklad ukazuje zástupné symboly pro zdroj dat SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1c259-114">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="1c259-115">Použijte zástupné symboly otazníku (?) pro <xref:System.Data.OleDb> <xref:System.Data.Odbc> parametry a.</span><span class="sxs-lookup"><span data-stu-id="1c259-115">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="1c259-116">V tomto Visual Basic příkladu `CompanyName` je pole aktualizováno hodnotou `@CompanyName` parametru pro řádek, který se `CustomerID` rovná hodnotě `@CustomerID` parametru.</span><span class="sxs-lookup"><span data-stu-id="1c259-116">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="1c259-117">Parametry načítají informace ze změněného řádku pomocí <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> vlastnosti <xref:System.Data.SqlClient.SqlParameter> objektu.</span><span class="sxs-lookup"><span data-stu-id="1c259-117">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="1c259-118">Níže jsou uvedené parametry předchozího příkazu Sample UPDATE.</span><span class="sxs-lookup"><span data-stu-id="1c259-118">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="1c259-119">Kód předpokládá, že proměnná `adapter` představuje platný <xref:System.Data.SqlClient.SqlDataAdapter> objekt.</span><span class="sxs-lookup"><span data-stu-id="1c259-119">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="1c259-120">`Add`Metoda `Parameters` kolekce přebírá název parametru, datový typ, velikost (Pokud je k dispozici pro typ) a název <xref:System.Data.Common.DbParameter.SourceColumn%2A> z `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="1c259-120">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="1c259-121">Všimněte si, že <xref:System.Data.Common.DbParameter.SourceVersion%2A> `@CustomerID` parametr je nastaven na hodnotu `Original` .</span><span class="sxs-lookup"><span data-stu-id="1c259-121">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="1c259-122">Tím se zaručí, že existující řádek ve zdroji dat se aktualizuje, pokud se v úpravě změnila hodnota určujícího sloupce nebo sloupce <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="1c259-122">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="1c259-123">V takovém případě bude `Original` hodnota řádku odpovídat aktuální hodnotě ve zdroji dat a `Current` hodnota řádku by obsahovala aktualizovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1c259-123">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="1c259-124">`SourceVersion`Pro parametr není `@CompanyName` nastavená a používá výchozí `Current` hodnotu řádku.</span><span class="sxs-lookup"><span data-stu-id="1c259-124">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c259-125">Pro `Fill` operace `DataAdapter` a `Get` metod `DataReader` , je typ .NET Framework odvozen od typu vráceného poskytovatelem dat .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c259-125">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="1c259-126">Odvozené .NET Framework typy a přístupové metody pro datové typy Microsoft SQL Server, OLE DB a ODBC jsou popsány v tématu [mapování datových typů v ADO.NET](data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="1c259-126">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="1c259-127">Parametr. SourceColumn, Parameter. SourceVersion</span><span class="sxs-lookup"><span data-stu-id="1c259-127">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="1c259-128">`SourceColumn`A `SourceVersion` mohou být předány jako argumenty `Parameter` konstruktoru nebo nastaveny jako vlastnosti existující `Parameter` .</span><span class="sxs-lookup"><span data-stu-id="1c259-128">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="1c259-129">`SourceColumn`Je název <xref:System.Data.DataColumn> z, <xref:System.Data.DataRow> kde `Parameter` bude načtena hodnota.</span><span class="sxs-lookup"><span data-stu-id="1c259-129">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="1c259-130">`SourceVersion`Určuje `DataRow` verzi, kterou `DataAdapter` používá k načtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1c259-130">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="1c259-131">V následující tabulce jsou uvedeny <xref:System.Data.DataRowVersion> hodnoty výčtu, které jsou k dispozici pro použití s `SourceVersion` .</span><span class="sxs-lookup"><span data-stu-id="1c259-131">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="1c259-132">Výčet DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="1c259-132">DataRowVersion Enumeration</span></span>|<span data-ttu-id="1c259-133">Popis</span><span class="sxs-lookup"><span data-stu-id="1c259-133">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="1c259-134">Parametr používá aktuální hodnotu sloupce.</span><span class="sxs-lookup"><span data-stu-id="1c259-134">The parameter uses the current value of the column.</span></span> <span data-ttu-id="1c259-135">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="1c259-135">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="1c259-136">Parametr používá `DefaultValue` sloupec.</span><span class="sxs-lookup"><span data-stu-id="1c259-136">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="1c259-137">Parametr používá původní hodnotu sloupce.</span><span class="sxs-lookup"><span data-stu-id="1c259-137">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="1c259-138">Parametr používá navrhovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1c259-138">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="1c259-139">`SqlClient`Příklad kódu v další části definuje parametr pro <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> , ve kterém `CustomerID` je sloupec použit jako `SourceColumn` pro dva parametry: `@CustomerID` ( `SET CustomerID = @CustomerID` ), a `@OldCustomerID` ( `WHERE CustomerID = @OldCustomerID` ).</span><span class="sxs-lookup"><span data-stu-id="1c259-139">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="1c259-140">`@CustomerID`Parametr se používá k aktualizaci sloupce **KódZákazníka** na aktuální hodnotu v `DataRow` .</span><span class="sxs-lookup"><span data-stu-id="1c259-140">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="1c259-141">Výsledkem je, že se `CustomerID` `SourceColumn` `SourceVersion` `Current` používá.</span><span class="sxs-lookup"><span data-stu-id="1c259-141">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="1c259-142">`@OldCustomerID`Parametr slouží k identifikaci aktuálního řádku ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="1c259-142">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="1c259-143">Vzhledem k tomu, že hodnota odpovídajícího sloupce je nalezena ve `Original` verzi řádku, je použita stejná hodnota `SourceColumn` ( `CustomerID` ) s a `SourceVersion` `Original` .</span><span class="sxs-lookup"><span data-stu-id="1c259-143">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="1c259-144">Práce s parametry SqlClient</span><span class="sxs-lookup"><span data-stu-id="1c259-144">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="1c259-145">Následující příklad ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlDataAdapter> a nastavit na, aby <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> <xref:System.Data.MissingSchemaAction.AddWithKey> bylo možné načíst další informace o schématu z databáze.</span><span class="sxs-lookup"><span data-stu-id="1c259-145">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="1c259-146"><xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> Nastavení vlastností,, a <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> a jejich odpovídajících <xref:System.Data.SqlClient.SqlParameter> objektů přidaných do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="1c259-146">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="1c259-147">Metoda vrací `SqlDataAdapter` objekt.</span><span class="sxs-lookup"><span data-stu-id="1c259-147">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="1c259-148">Zástupné symboly parametrů OleDb</span><span class="sxs-lookup"><span data-stu-id="1c259-148">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="1c259-149">Pro <xref:System.Data.OleDb.OleDbDataAdapter> objekty a je <xref:System.Data.Odbc.OdbcDataAdapter> nutné použít zástupné symboly otazníku (?) k identifikaci parametrů.</span><span class="sxs-lookup"><span data-stu-id="1c259-149">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="1c259-150">Parametrizované příkazy dotazu definují, které vstupní a výstupní parametry je třeba vytvořit.</span><span class="sxs-lookup"><span data-stu-id="1c259-150">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="1c259-151">Chcete-li vytvořit parametr, použijte `Parameters.Add` metodu nebo `Parameter` konstruktor k určení názvu, datového typu a velikosti sloupce.</span><span class="sxs-lookup"><span data-stu-id="1c259-151">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="1c259-152">U vnitřních datových typů, například `Integer` nemusíte vkládat velikost, nebo můžete zadat výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="1c259-152">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="1c259-153">Následující příklad kódu vytvoří parametry pro příkaz SQL a pak vyplní `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="1c259-153">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="1c259-154">Příklad OleDb</span><span class="sxs-lookup"><span data-stu-id="1c259-154">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="1c259-155">Parametry ODBC</span><span class="sxs-lookup"><span data-stu-id="1c259-155">Odbc Parameters</span></span>  
  
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
> <span data-ttu-id="1c259-156">Pokud není zadán název parametru pro parametr, je parametrem udělen přírůstkový výchozí název parametru*N* *,* počínaje hodnotou "parametr1".</span><span class="sxs-lookup"><span data-stu-id="1c259-156">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="1c259-157">Doporučujeme vyhnout se zásadám vytváření názvů parametrů*N* , pokud zadáte název parametru, protože název, který zadáte, může být v konfliktu s existujícím výchozím názvem parametru v `ParameterCollection` .</span><span class="sxs-lookup"><span data-stu-id="1c259-157">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="1c259-158">Pokud zadaný název již existuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1c259-158">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c259-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c259-159">See also</span></span>

- [<span data-ttu-id="1c259-160">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="1c259-160">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="1c259-161">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="1c259-161">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="1c259-162">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="1c259-162">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="1c259-163">Úpravy dat pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="1c259-163">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="1c259-164">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1c259-164">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="1c259-165">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1c259-165">ADO.NET Overview</span></span>](ado-net-overview.md)
