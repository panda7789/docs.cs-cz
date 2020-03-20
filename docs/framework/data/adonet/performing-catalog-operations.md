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
# <a name="performing-catalog-operations"></a>Provádění operací katalogu
Chcete-li spustit příkaz k úpravě databáze nebo katalogu, například příkaz vytvořit tabulku nebo příkaz VYTVOŘIT PROCEDURU, vytvořte objekt **Příkaz** pomocí příslušných příkazů SQL a objektu **Connection.** Spusťte příkaz metodou **ExecuteNonQuery** objektu **Command.**  
  
 Následující příklad kódu vytvoří uloženou proceduru v databázi serveru Microsoft SQL Server.  
  
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
  
## <a name="see-also"></a>Viz také

- [Použití příkazů pro změny dat](using-commands-to-modify-data.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Přehled ADO.NET](ado-net-overview.md)
