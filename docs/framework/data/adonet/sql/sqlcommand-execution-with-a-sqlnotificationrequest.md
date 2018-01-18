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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fee008d0b1f278a48eacd8eae70d75bbbfd93691
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="3a59d-102">Provádění SqlCommand s SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="3a59d-102">SqlCommand Execution with a SqlNotificationRequest</span></span>
<span data-ttu-id="3a59d-103">A <xref:System.Data.SqlClient.SqlCommand> může být nakonfigurováno pro generování oznámení při změně dat po získána ze serveru a sadu výsledků dotazu by být různé, pokud byly znovu spustit dotaz.</span><span class="sxs-lookup"><span data-stu-id="3a59d-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="3a59d-104">To je užitečné pro scénáře, ve které chcete používat vlastní oznámení fronty na serveru nebo pokud není chcete zachovat živé objekty.</span><span class="sxs-lookup"><span data-stu-id="3a59d-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>  
  
## <a name="creating-the-notification-request"></a><span data-ttu-id="3a59d-105">Vytvořit žádost o oznámení.</span><span class="sxs-lookup"><span data-stu-id="3a59d-105">Creating the Notification Request</span></span>  
 <span data-ttu-id="3a59d-106">Můžete použít <xref:System.Data.Sql.SqlNotificationRequest> objekt, který chcete vytvořit žádost o oznámení. jeho vazby `SqlCommand` objektu.</span><span class="sxs-lookup"><span data-stu-id="3a59d-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="3a59d-107">Po vytvoření žádost již nepotřebujete `SqlNotificationRequest` objektu.</span><span class="sxs-lookup"><span data-stu-id="3a59d-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="3a59d-108">Se můžete dotazovat fronty pro všechny oznámení a reagují odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="3a59d-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="3a59d-109">Oznámení může dojít i v případě, že je aplikace vypnout a následně restartovat.</span><span class="sxs-lookup"><span data-stu-id="3a59d-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>  
  
 <span data-ttu-id="3a59d-110">Když se spustí příkaz přidružené oznámení, všechny změny na původní výsledek nastavit aktivační událost odeslání zprávy do fronty systému SQL Server, který jste nakonfigurovali v žádost o oznámení.</span><span class="sxs-lookup"><span data-stu-id="3a59d-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>  
  
 <span data-ttu-id="3a59d-111">Jak dotazovat fronty systému SQL Server a interpretovat zprávy je specifický pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3a59d-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="3a59d-112">Aplikace je zodpovědná za dotazování fronty a reaktivní na základě obsahu zprávy.</span><span class="sxs-lookup"><span data-stu-id="3a59d-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a59d-113">Při použití požadavků oznámení systému SQL Server s <xref:System.Data.SqlClient.SqlDependency>, vytvořit svůj vlastní název fronty místo použití výchozí název služby.</span><span class="sxs-lookup"><span data-stu-id="3a59d-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>  
  
 <span data-ttu-id="3a59d-114">Nejsou žádné nové prvky zabezpečení na straně klienta pro <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="3a59d-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="3a59d-115">Toto je primárně funkce serveru a server vytvořil speciální oprávnění, které uživatelé musí mít k vyžádání oznámení.</span><span class="sxs-lookup"><span data-stu-id="3a59d-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3a59d-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a59d-116">Example</span></span>  
 <span data-ttu-id="3a59d-117">Následující fragment kódu ukazuje, jak vytvořit <xref:System.Data.Sql.SqlNotificationRequest> a přidružte ji s <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="3a59d-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a59d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a59d-118">See Also</span></span>  
 [<span data-ttu-id="3a59d-119">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="3a59d-119">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="3a59d-120">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="3a59d-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
