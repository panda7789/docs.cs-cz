---
title: "Provádění operací katalogu"
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
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f67f393dce518a76b80d91f7294ed19e9a0f411a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="654e5-102">Provádění operací katalogu</span><span class="sxs-lookup"><span data-stu-id="654e5-102">Performing Catalog Operations</span></span>
<span data-ttu-id="654e5-103">K provedení příkazu k úpravě databáze nebo katalogu, jako je například příkaz CREATE TABLE nebo CREATE PROCEDURE vytvořit **příkaz** pomocí příslušné příkazy SQL a **připojení** objektu.</span><span class="sxs-lookup"><span data-stu-id="654e5-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="654e5-104">Spusťte příkaz se **ExecuteNonQuery** metodu **příkaz** objektu.</span><span class="sxs-lookup"><span data-stu-id="654e5-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="654e5-105">Následující příklad kódu vytvoří uloženou proceduru v databázi Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="654e5-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="654e5-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="654e5-106">See Also</span></span>  
 [<span data-ttu-id="654e5-107">Příkazy ke změně dat</span><span class="sxs-lookup"><span data-stu-id="654e5-107">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [<span data-ttu-id="654e5-108">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="654e5-108">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="654e5-109">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="654e5-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
