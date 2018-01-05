---
title: "Provádění SqlCommand s SqlNotificationRequest"
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
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 509c25f5c6d1108b76028af5cfd8f2a090c92137
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Provádění SqlCommand s SqlNotificationRequest
A <xref:System.Data.SqlClient.SqlCommand> může být nakonfigurováno pro generování oznámení při změně dat po získána ze serveru a sadu výsledků dotazu by být různé, pokud byly znovu spustit dotaz. To je užitečné pro scénáře, ve které chcete používat vlastní oznámení fronty na serveru nebo pokud není chcete zachovat živé objekty.  
  
## <a name="creating-the-notification-request"></a>Vytvořit žádost o oznámení.  
 Můžete použít <xref:System.Data.Sql.SqlNotificationRequest> objekt, který chcete vytvořit žádost o oznámení. jeho vazby `SqlCommand` objektu. Po vytvoření žádost již nepotřebujete `SqlNotificationRequest` objektu. Se můžete dotazovat fronty pro všechny oznámení a reagují odpovídajícím způsobem. Oznámení může dojít i v případě, že je aplikace vypnout a následně restartovat.  
  
 Když se spustí příkaz přidružené oznámení, všechny změny na původní výsledek nastavit aktivační událost odeslání zprávy do fronty systému SQL Server, který jste nakonfigurovali v žádost o oznámení.  
  
 Jak dotazovat fronty systému SQL Server a interpretovat zprávy je specifický pro vaši aplikaci. Aplikace je zodpovědná za dotazování fronty a reaktivní na základě obsahu zprávy.  
  
> [!NOTE]
>  Při použití požadavků oznámení systému SQL Server s <xref:System.Data.SqlClient.SqlDependency>, vytvořit svůj vlastní název fronty místo použití výchozí název služby.  
  
 Nejsou žádné nové prvky zabezpečení na straně klienta pro <xref:System.Data.Sql.SqlNotificationRequest>. Toto je primárně funkce serveru a server vytvořil speciální oprávnění, které uživatelé musí mít k vyžádání oznámení.  
  
### <a name="example"></a>Příklad  
 Následující fragment kódu ukazuje, jak vytvořit <xref:System.Data.Sql.SqlNotificationRequest> a přidružte ji s <xref:System.Data.SqlClient.SqlCommand>.  
  
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
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
