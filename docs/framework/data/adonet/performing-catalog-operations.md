---
title: Provádění operací katalogu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: bedeb4e9c510a3feeedc038e9c4cef6c4721e345
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149242"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="ef8fc-102">Provádění operací katalogu</span><span class="sxs-lookup"><span data-stu-id="ef8fc-102">Performing Catalog Operations</span></span>
<span data-ttu-id="ef8fc-103">Chcete-li spustit příkaz k úpravě databáze nebo katalogu, například příkaz vytvořit tabulku nebo příkaz VYTVOŘIT PROCEDURU, vytvořte objekt **Příkaz** pomocí příslušných příkazů SQL a objektu **Connection.**</span><span class="sxs-lookup"><span data-stu-id="ef8fc-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="ef8fc-104">Spusťte příkaz metodou **ExecuteNonQuery** objektu **Command.**</span><span class="sxs-lookup"><span data-stu-id="ef8fc-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="ef8fc-105">Následující příklad kódu vytvoří uloženou proceduru v databázi serveru Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ef8fc-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef8fc-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef8fc-106">See also</span></span>

- [<span data-ttu-id="ef8fc-107">Použití příkazů pro změny dat</span><span class="sxs-lookup"><span data-stu-id="ef8fc-107">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="ef8fc-108">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="ef8fc-108">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="ef8fc-109">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ef8fc-109">ADO.NET Overview</span></span>](ado-net-overview.md)
