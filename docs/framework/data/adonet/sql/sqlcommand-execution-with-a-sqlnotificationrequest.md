---
title: Provádění SqlCommand pomocí SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 83450e6ace33e89ddd263a1514f74f4d4e231cf7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798570"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Provádění SqlCommand pomocí SqlNotificationRequest
A <xref:System.Data.SqlClient.SqlCommand> lze nakonfigurovat pro generování oznámení při změně dat poté, co má byla načtena ze serveru a sadu výsledků dotazu bude odlišná, pokud se dotaz spustit znovu. To je užitečné pro scénáře, ve které chcete používat vlastní oznámení fronty na serveru nebo pokud nechcete zachovat živé objekty.  
  
## <a name="creating-the-notification-request"></a>Vytváří se žádost o oznámení.  
 Můžete použít <xref:System.Data.Sql.SqlNotificationRequest> objektu, který chcete vytvořit žádost o oznámení pomocí vytvoření vazby na `SqlCommand` objektu. Po vytvoření žádosti, které už nepotřebujete `SqlNotificationRequest` objektu. Se můžete dotazovat frontu pro všechna naše oznámení a reagují odpovídajícím způsobem. Oznámení může dojít i v případě, že aplikace se vypne a následně restartuje.  
  
 Při spuštění příkazu s související upozornění, všechny změny původní výsledek nastavit aktivační událost odeslání zprávy do fronty SQL Server, který jste nakonfigurovali v žádost o oznámení.  
  
 Jak dotazovat fronty SQL serveru a interpretovat zprávy je specifická pro vaši aplikaci. Aplikace zodpovídá za dotazování fronty a reakce na základě obsahu zprávy.  
  
> [!NOTE]
>  Při použití SQL serveru na žádosti oznámení se <xref:System.Data.SqlClient.SqlDependency>, vytvořte vlastní název fronty místo použití výchozí název služby.  
  
 Neexistují žádné nové prvky zabezpečení na straně klienta pro <xref:System.Data.Sql.SqlNotificationRequest>. To je především funkce serveru a serveru byla vytvořena zvláštní oprávnění, které uživatelé musí mít na žádost o oznámení.  
  
### <a name="example"></a>Příklad  
 Následující fragment kódu ukazuje, jak vytvořit <xref:System.Data.Sql.SqlNotificationRequest> a přidružte jej k <xref:System.Data.SqlClient.SqlCommand>.  
  
```vb  
' Assume connection is an open SqlConnection.  
' Create a new SqlCommand object.  
Dim command As New SqlCommand( _  
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)  
  
' Create a SqlNotificationRequest object.  
Dim notficationRequest As New SqlNotificationRequest()  
notficationRequest.id = "NotificationID"  
notficationRequest.Service = "mySSBQueue"  
  
' Associate the notification request with the command.  
command.Notification = notficationRequest  
' Execute the command.  
command.ExecuteReader()  
' Process the DataReader.  
' You can use Transact-SQL syntax to periodically poll the   
' SQL Server queue to see if you have a new message.  
```  
  
```csharp  
// Assume connection is an open SqlConnection.  
// Create a new SqlCommand object.  
SqlCommand command=new SqlCommand(  
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);  
  
// Create a SqlNotificationRequest object.  
SqlNotificationRequest notficationRequest=new SqlNotificationRequest();  
notficationRequest.id="NotificationID";  
notficationRequest.Service="mySSBQueue";  
  
// Associate the notification request with the command.  
command.Notification=notficationRequest;  
// Execute the command.  
command.ExecuteReader();  
// Process the DataReader.  
// You can use Transact-SQL syntax to periodically poll the   
// SQL Server queue to see if you have a new message.  
```  
  
## <a name="see-also"></a>Viz také  
 [Oznámení pro dotazy na SQL Serveru](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
