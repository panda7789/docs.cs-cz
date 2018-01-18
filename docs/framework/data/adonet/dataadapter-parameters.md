---
title: Parametry DataAdapter
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
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4b5cc66e1d2240450743afa8ca8aaa6efe94398d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="9e8d5-102">Parametry DataAdapter</span><span class="sxs-lookup"><span data-stu-id="9e8d5-102">DataAdapter Parameters</span></span>
<span data-ttu-id="9e8d5-103"><xref:System.Data.Common.DbDataAdapter> Má čtyři vlastnosti, které slouží k načtení dat z a aktualizovat data do zdroje dat: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> vlastnost vrací data ze zdroje dat; a <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, a <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> vlastnosti se používají ke správě změny ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="9e8d5-104">`SelectCommand` Musí být nastavena vlastnost před voláním `Fill` metodu `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="9e8d5-105">`InsertCommand`, `UpdateCommand`, Nebo `DeleteCommand` vlastnosti musí být nastavená před `Update` metodu `DataAdapter` je volána, v závislosti na tom, jaké změny byly provedeny k datům ve <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="9e8d5-106">Pokud byl přidán počet řádků, například `InsertCommand` musí být nastaven před voláním `Update`.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="9e8d5-107">Když `Update` zpracovává vložené, aktualizovaných nebo odstraněných řádků, `DataAdapter` používá příslušných `Command` vlastnost zpracovat akci.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="9e8d5-108">Aktuální informace o upravené řádek je předán `Command` objektu prostřednictvím `Parameters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="9e8d5-109">Při aktualizaci řádek ve zdroji dat, zavoláte příkaz UPDATE, který používá jedinečný identifikátor pro identifikaci řádek v tabulce aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table be updated.</span></span> <span data-ttu-id="9e8d5-110">Jedinečný identifikátor je obvykle hodnota pole primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="9e8d5-111">Příkaz UPDATE používá parametry, které obsahují jedinečný identifikátor a sloupců a hodnoty pro aktualizaci, jak je znázorněno v následujícím příkazu Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  <span data-ttu-id="9e8d5-112">Syntaxe parametru zástupné symboly závisí na zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="9e8d5-113">Tento příklad ukazuje zástupné symboly pro zdroj dat systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="9e8d5-114">Použít zástupné znaky otazníku (?) pro <xref:System.Data.OleDb> a <xref:System.Data.Odbc> parametry.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="9e8d5-115">V tomto [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] například `CompanyName` pole je aktualizováno s hodnotou `@CompanyName` parametr pro řádek kde `CustomerID` se rovná hodnotě `@CustomerID` parametr.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-115">In this [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="9e8d5-116">Parametry načtení informací z řádku upravené pomocí <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> vlastnost <xref:System.Data.SqlClient.SqlParameter> objektu.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="9e8d5-117">Níže jsou uvedeny parametry pro předchozí příkaz Ukázka aktualizace.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="9e8d5-118">Kód předpokládá, že proměnná `adapter` představuje platnou <xref:System.Data.SqlClient.SqlDataAdapter> objektu.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="9e8d5-119">`Add` Metodu `Parameters` kolekce přebírá název parametru, datový typ, velikost (Pokud je k dispozici typu) a název <xref:System.Data.Common.DbParameter.SourceColumn%2A> z `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="9e8d5-120">Všimněte si, že <xref:System.Data.Common.DbParameter.SourceVersion%2A> z `@CustomerID` parametr je nastaven na `Original`.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="9e8d5-121">To zaručuje, že se aktualizuje stávající řádek ve zdroji dat, došlo ke změně hodnoty identifikační sloupec nebo sloupce v upravenou <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="9e8d5-122">V takovém případě `Original` odpovídá hodnota řádku je aktuální hodnota ve zdroji dat a `Current` hodnota řádku by obsahovat aktualizované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="9e8d5-123">`SourceVersion` Pro `@CompanyName` parametr není nastaven a použije výchozí `Current` řádek hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e8d5-124">Pro oba `Fill` operace `DataAdapter` a `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ je odvozen od typu vrácená z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type is inferred from the type returned from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="9e8d5-125">Odvozené [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy a metody přístupových objektů pro typy dat Microsoft SQL Server, technologie OLE DB a rozhraní ODBC jsou popsané v [mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="9e8d5-125">The inferred [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="9e8d5-126">Parameter.SourceColumn, Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="9e8d5-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="9e8d5-127">`SourceColumn` a `SourceVersion` může být předána jako argumenty, které mají `Parameter` konstruktoru, nebo nastavit jako vlastnosti z existující `Parameter`.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="9e8d5-128">`SourceColumn` Je název <xref:System.Data.DataColumn> z <xref:System.Data.DataRow> kde hodnotu `Parameter` bude načten.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="9e8d5-129">`SourceVersion` Určuje `DataRow` verze, `DataAdapter` používá k načtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="9e8d5-130">Následující tabulce je zobrazena <xref:System.Data.DataRowVersion> hodnot výčtu, které jsou k dispozici pro použití s `SourceVersion`.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="9e8d5-131">DataRowVersion – výčet</span><span class="sxs-lookup"><span data-stu-id="9e8d5-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="9e8d5-132">Popis</span><span class="sxs-lookup"><span data-stu-id="9e8d5-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="9e8d5-133">Parametr používá aktuální hodnotu sloupce.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="9e8d5-134">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="9e8d5-135">Parametr používá `DefaultValue` sloupce.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="9e8d5-136">Parametr používá původní hodnotu pro sloupec.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="9e8d5-137">Parametr používá navrhované hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="9e8d5-138">`SqlClient` Příklad kódu v další části definuje parametr pro <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> ve kterém `CustomerID` sloupec slouží jako `SourceColumn` pro dva parametry: `@CustomerID` (`SET CustomerID = @CustomerID`), a `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span><span class="sxs-lookup"><span data-stu-id="9e8d5-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="9e8d5-139">`@CustomerID` Parametr se používá k aktualizaci **CustomerID** sloupec, který se aktuální hodnota v `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="9e8d5-140">V důsledku toho `CustomerID` `SourceColumn` s `SourceVersion` z `Current` se používá.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="9e8d5-141"> *@OldCustomerID*  Parametr se používá k identifikaci na aktuálním řádku v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-141">The *@OldCustomerID* parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="9e8d5-142">Protože je nalezen odpovídající hodnota sloupce v `Original` verze řádku, stejné `SourceColumn` (`CustomerID`) s `SourceVersion` z `Original` se používá.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="9e8d5-143">Práce s parametry SqlClient</span><span class="sxs-lookup"><span data-stu-id="9e8d5-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="9e8d5-144">Následující příklad ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlDataAdapter> a nastavte <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> k <xref:System.Data.MissingSchemaAction.AddWithKey> Chcete-li získat další informace o schématu z databáze.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="9e8d5-145"><xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, A <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> sadu vlastností a jejich odpovídajících <xref:System.Data.SqlClient.SqlParameter> objektů přidaných do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="9e8d5-146">Vrátí metodu `SqlDataAdapter` objektu.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="9e8d5-147">Zástupné symboly parametrů OleDb</span><span class="sxs-lookup"><span data-stu-id="9e8d5-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="9e8d5-148">Pro <xref:System.Data.OleDb.OleDbDataAdapter> a <xref:System.Data.Odbc.OdbcDataAdapter> objekty, musíte použít zástupné znaky otazníku (?) k identifikaci parametry.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="9e8d5-149">Příkazy parametrizovaného dotazu definovat, které vstupní a výstupní parametry musí být vytvořen.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="9e8d5-150">Chcete-li vytvořit parametr, použijte `Parameters.Add` metoda nebo `Parameter` konstruktor a zadat název sloupce, datový typ a velikost.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="9e8d5-151">Pro vnitřní datové typy jako například `Integer`, není nutné zahrnovat velikost, nebo můžete zadat výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="9e8d5-152">Následující příklad kódu vytvoří parametry příkazu jazyka SQL a pak vyplní `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="9e8d5-153">Příklad OleDb</span><span class="sxs-lookup"><span data-stu-id="9e8d5-153">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="9e8d5-154">Odbc Parameters</span><span class="sxs-lookup"><span data-stu-id="9e8d5-154">Odbc Parameters</span></span>  
  
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
>  <span data-ttu-id="9e8d5-155">Pokud je název parametru není zadaný pro parametr, parametr dostane přírůstkové výchozí název parametru*N* *,* počínaje "Parameter1".</span><span class="sxs-lookup"><span data-stu-id="9e8d5-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="9e8d5-156">Doporučujeme, abyste parametr*N* zásady vytváření názvů když zadáte název parametru, protože název, který zadáte může být v konfliktu s existujícím názvem výchozí parametr v `ParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="9e8d5-157">Pokud se zadaným názvem již existuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9e8d5-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e8d5-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e8d5-158">See Also</span></span>  
 [<span data-ttu-id="9e8d5-159">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="9e8d5-159">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="9e8d5-160">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="9e8d5-160">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="9e8d5-161">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="9e8d5-161">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="9e8d5-162">Úpravy dat pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="9e8d5-162">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [<span data-ttu-id="9e8d5-163">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9e8d5-163">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="9e8d5-164">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="9e8d5-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
