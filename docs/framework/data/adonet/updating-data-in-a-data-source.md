---
title: Aktualizace dat ve zdroji dat.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: d7b57a9572a285dfdc13afb0a520de67e231a1c0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463907"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="14cc6-102">Aktualizace dat ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="14cc6-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="14cc6-103">Příkazy SQL, které upravují data (například vložení, aktualizace nebo odstranění) nevracejí řádky.</span><span class="sxs-lookup"><span data-stu-id="14cc6-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="14cc6-104">Podobně mnoho uložené procedury provést akci, ale nevracejí řádky.</span><span class="sxs-lookup"><span data-stu-id="14cc6-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="14cc6-105">Ke spuštění příkazů, které nevracejí řádky, vytvořit **příkaz** objekt s příslušný příkaz SQL a **připojení**, včetně požadované **parametry**.</span><span class="sxs-lookup"><span data-stu-id="14cc6-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="14cc6-106">Příkaz Spustit **metodu ExecuteNonQuery** metodu **příkaz** objektu.</span><span class="sxs-lookup"><span data-stu-id="14cc6-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="14cc6-107">**Metodu ExecuteNonQuery** metoda vrátí celé číslo představující počet řádků, které jsou ovlivněny příkazu nebo uložené procedury, která se spustil.</span><span class="sxs-lookup"><span data-stu-id="14cc6-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="14cc6-108">Pokud více příkazy jsou spouštěny, vrácená hodnota je součtem záznamů ovlivněný všechny příkazy spuštění.</span><span class="sxs-lookup"><span data-stu-id="14cc6-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14cc6-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="14cc6-109">Example</span></span>  
 <span data-ttu-id="14cc6-110">Příkaz INSERT k vložení záznamu do databáze pomocí provádí následující příklad kódu **metodu ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="14cc6-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
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
  
 <span data-ttu-id="14cc6-111">Následující příklad kódu Spustí uloženou proceduru vytvořen ukázkový kód v [provádění operací katalogu](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="14cc6-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span></span> <span data-ttu-id="14cc6-112">Žádné řádky jsou vráceny pomocí uložené procedury, takže **metodu ExecuteNonQuery** metoda se používá, ale zobrazí vstupní parametr uložené procedury a vrátí výstupní parametr a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="14cc6-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="14cc6-113">Pro <xref:System.Data.OleDb.OleDbCommand> objektu, **ReturnValue** parametr musí být přidané do **parametry** kolekce první.</span><span class="sxs-lookup"><span data-stu-id="14cc6-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="14cc6-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="14cc6-114">See Also</span></span>  
 [<span data-ttu-id="14cc6-115">Použití příkazů pro změny dat</span><span class="sxs-lookup"><span data-stu-id="14cc6-115">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [<span data-ttu-id="14cc6-116">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="14cc6-116">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="14cc6-117">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="14cc6-117">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="14cc6-118">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="14cc6-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
