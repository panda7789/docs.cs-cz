---
title: Provádění operací katalogu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: 0291b6684092ec15fc672c39c909caf7781194e3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783253"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="6f885-102">Provádění operací katalogu</span><span class="sxs-lookup"><span data-stu-id="6f885-102">Performing Catalog Operations</span></span>
<span data-ttu-id="6f885-103">Chcete-li spustit příkaz pro úpravu databáze nebo katalogu, jako je například příkaz CREATE TABLE nebo CREATE PROCEDURe, vytvořte objekt **příkazu** pomocí příslušných příkazů SQL a objektu **připojení** .</span><span class="sxs-lookup"><span data-stu-id="6f885-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="6f885-104">Spusťte příkaz s metodou **ExecuteNonQuery** objektu **Command** .</span><span class="sxs-lookup"><span data-stu-id="6f885-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="6f885-105">Následující příklad kódu vytvoří uloženou proceduru v databázi Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6f885-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +   
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +   
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +   
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f885-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f885-106">See also</span></span>

- [<span data-ttu-id="6f885-107">Použití příkazů pro změny dat</span><span class="sxs-lookup"><span data-stu-id="6f885-107">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="6f885-108">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="6f885-108">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="6f885-109">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6f885-109">ADO.NET Overview</span></span>](ado-net-overview.md)
