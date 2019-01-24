---
title: Provádění operací katalogu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: 1b13d1e3e210964331a710512876bd1f8503069e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648073"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="dba1a-102">Provádění operací katalogu</span><span class="sxs-lookup"><span data-stu-id="dba1a-102">Performing Catalog Operations</span></span>
<span data-ttu-id="dba1a-103">K provedení příkazu k úpravě databáze nebo katalog, jako například výkaz CREATE TABLE nebo CREATE PROCEDURE vytvořit **příkaz** pomocí odpovídající příkazy SQL a **připojení** objektu.</span><span class="sxs-lookup"><span data-stu-id="dba1a-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="dba1a-104">Příkaz Spustit **metodu ExecuteNonQuery** metodu **příkaz** objektu.</span><span class="sxs-lookup"><span data-stu-id="dba1a-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="dba1a-105">Následující příklad kódu vytvoří uloženou proceduru v databázi Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dba1a-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dba1a-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dba1a-106">See also</span></span>
- [<span data-ttu-id="dba1a-107">Použití příkazů pro změny dat</span><span class="sxs-lookup"><span data-stu-id="dba1a-107">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)
- [<span data-ttu-id="dba1a-108">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="dba1a-108">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="dba1a-109">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="dba1a-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
