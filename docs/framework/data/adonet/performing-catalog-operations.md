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
# <a name="performing-catalog-operations"></a>Provádění operací katalogu
Chcete-li spustit příkaz pro úpravu databáze nebo katalogu, jako je například příkaz CREATE TABLE nebo CREATE PROCEDURe, vytvořte objekt **příkazu** pomocí příslušných příkazů SQL a objektu **připojení** . Spusťte příkaz s metodou **ExecuteNonQuery** objektu **Command** .  
  
 Následující příklad kódu vytvoří uloženou proceduru v databázi Microsoft SQL Server.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Použití příkazů pro změny dat](using-commands-to-modify-data.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Přehled ADO.NET](ado-net-overview.md)
