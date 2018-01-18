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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b5ac8d5522b599eb1d426314eda1d7d9e406da90
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="030ae-102">Provádění operací katalogu</span><span class="sxs-lookup"><span data-stu-id="030ae-102">Performing Catalog Operations</span></span>
<span data-ttu-id="030ae-103">K provedení příkazu k úpravě databáze nebo katalogu, jako je například příkaz CREATE TABLE nebo CREATE PROCEDURE vytvořit **příkaz** pomocí příslušné příkazy SQL a **připojení** objektu.</span><span class="sxs-lookup"><span data-stu-id="030ae-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="030ae-104">Spusťte příkaz se **ExecuteNonQuery** metodu **příkaz** objektu.</span><span class="sxs-lookup"><span data-stu-id="030ae-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="030ae-105">Následující příklad kódu vytvoří uloženou proceduru v databázi Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="030ae-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="030ae-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="030ae-106">See Also</span></span>  
 [<span data-ttu-id="030ae-107">Použití příkazů pro změny dat</span><span class="sxs-lookup"><span data-stu-id="030ae-107">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [<span data-ttu-id="030ae-108">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="030ae-108">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="030ae-109">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="030ae-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
