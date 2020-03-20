---
title: Aktualizace dat ve zdroji dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 18bb03e17b19243ee1bc6e3f7ebd70afb4d4c60b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174443"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="a139f-102">Aktualizace dat ve zdroji dat</span><span class="sxs-lookup"><span data-stu-id="a139f-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="a139f-103">Příkazy SQL, které upravují data (například INSERT, UPDATE nebo DELETE), nevracejí řádky.</span><span class="sxs-lookup"><span data-stu-id="a139f-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="a139f-104">Podobně mnoho uložené procedury provést akci, ale nevracejí řádky.</span><span class="sxs-lookup"><span data-stu-id="a139f-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="a139f-105">Chcete-li spouštět příkazy, které nevracejí řádky, vytvořte objekt **Příkaz** s příslušným příkazem SQL a **připojením**, včetně všech **požadovaných parametrů**.</span><span class="sxs-lookup"><span data-stu-id="a139f-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="a139f-106">Spusťte příkaz metodou **ExecuteNonQuery** objektu **Command.**</span><span class="sxs-lookup"><span data-stu-id="a139f-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="a139f-107">Metoda **ExecuteNonQuery** vrátí celé číslo, které představuje počet řádků ovlivněných příkazem nebo uloženou procedurou, která byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="a139f-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="a139f-108">Pokud je provedeno více příkazů, vrácená hodnota je součtem záznamů ovlivněných všemi příkazy.</span><span class="sxs-lookup"><span data-stu-id="a139f-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a139f-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a139f-109">Example</span></span>  
 <span data-ttu-id="a139f-110">Následující příklad kódu provede příkaz INSERT pro vložení záznamu do databáze pomocí **příkazu ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="a139f-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
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
  
 <span data-ttu-id="a139f-111">Následující příklad kódu provede uloženou proceduru vytvořenou ukázkovým kódem [v provedení operací katalogu](performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a139f-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](performing-catalog-operations.md).</span></span> <span data-ttu-id="a139f-112">Uložená procedura nevrací žádné řádky, takže se používá metoda **ExecuteNonQuery,** ale uložená procedura obdrží vstupní parametr a vrátí výstupní parametr a vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a139f-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="a139f-113">Pro <xref:System.Data.OleDb.OleDbCommand> objekt **returnvalue** parametr musí být přidán do **kolekce Parameters** jako první.</span><span class="sxs-lookup"><span data-stu-id="a139f-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a139f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a139f-114">See also</span></span>

- [<span data-ttu-id="a139f-115">Použití příkazů pro změny dat</span><span class="sxs-lookup"><span data-stu-id="a139f-115">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="a139f-116">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="a139f-116">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="a139f-117">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="a139f-117">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="a139f-118">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a139f-118">ADO.NET Overview</span></span>](ado-net-overview.md)
