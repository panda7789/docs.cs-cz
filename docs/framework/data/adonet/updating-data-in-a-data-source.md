---
title: Aktualizace dat ve zdroji dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 0926e3c6513a698ae47b9983d0e6ad195394a4df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780611"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="b92ed-102">Aktualizace dat ve zdroji dat</span><span class="sxs-lookup"><span data-stu-id="b92ed-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="b92ed-103">Příkazy jazyka SQL, které upravují data (například INSERT, UPDATE nebo DELETE), nevrací řádky.</span><span class="sxs-lookup"><span data-stu-id="b92ed-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="b92ed-104">Podobně mnoho uložených procedur provádí akci, ale nevrací řádky.</span><span class="sxs-lookup"><span data-stu-id="b92ed-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="b92ed-105">Chcete-li provést příkazy, které nevracejí řádky, vytvořte objekt **příkazu** s příslušným příkazem SQL a **připojením**, včetně požadovaných **parametrů**.</span><span class="sxs-lookup"><span data-stu-id="b92ed-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="b92ed-106">Spusťte příkaz s metodou **ExecuteNonQuery** objektu **Command** .</span><span class="sxs-lookup"><span data-stu-id="b92ed-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="b92ed-107">Metoda **ExecuteNonQuery** vrací celé číslo, které představuje počet řádků ovlivněných příkazem nebo uloženou procedurou, která byla provedena.</span><span class="sxs-lookup"><span data-stu-id="b92ed-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="b92ed-108">Pokud je spuštěno více příkazů, vrácená hodnota je součet záznamů ovlivněných všemi provedenými příkazy.</span><span class="sxs-lookup"><span data-stu-id="b92ed-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b92ed-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b92ed-109">Example</span></span>  
 <span data-ttu-id="b92ed-110">Následující příklad kódu provede příkaz INSERT pro vložení záznamu do databáze pomocí **ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="b92ed-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 <span data-ttu-id="b92ed-111">Následující příklad kódu provede uloženou proceduru vytvořenou vzorovým kódem při [provádění operací katalogu](performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b92ed-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](performing-catalog-operations.md).</span></span> <span data-ttu-id="b92ed-112">Uložený postup nevrátí žádné řádky, takže se použije metoda **ExecuteNonQuery** , ale uložená procedura obdrží vstupní parametr a vrátí výstupní parametr a návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b92ed-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="b92ed-113">Pro objekt je nutné nejprve přidat parametr **ReturnValue** do kolekce Parameters. <xref:System.Data.OleDb.OleDbCommand></span><span class="sxs-lookup"><span data-stu-id="b92ed-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)   
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a><span data-ttu-id="b92ed-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b92ed-114">See also</span></span>

- [<span data-ttu-id="b92ed-115">Použití příkazů pro změny dat</span><span class="sxs-lookup"><span data-stu-id="b92ed-115">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="b92ed-116">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="b92ed-116">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="b92ed-117">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="b92ed-117">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="b92ed-118">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b92ed-118">ADO.NET Overview</span></span>](ado-net-overview.md)
