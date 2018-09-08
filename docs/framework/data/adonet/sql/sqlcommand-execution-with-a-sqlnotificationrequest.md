---
title: Provádění SqlCommand pomocí SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 83450e6ace33e89ddd263a1514f74f4d4e231cf7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44139069"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="2cf1e-102">Provádění SqlCommand pomocí SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="2cf1e-102">SqlCommand Execution with a SqlNotificationRequest</span></span>
<span data-ttu-id="2cf1e-103">A <xref:System.Data.SqlClient.SqlCommand> lze nakonfigurovat pro generování oznámení při změně dat poté, co má byla načtena ze serveru a sadu výsledků dotazu bude odlišná, pokud se dotaz spustit znovu.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="2cf1e-104">To je užitečné pro scénáře, ve které chcete používat vlastní oznámení fronty na serveru nebo pokud nechcete zachovat živé objekty.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>  
  
## <a name="creating-the-notification-request"></a><span data-ttu-id="2cf1e-105">Vytváří se žádost o oznámení.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-105">Creating the Notification Request</span></span>  
 <span data-ttu-id="2cf1e-106">Můžete použít <xref:System.Data.Sql.SqlNotificationRequest> objektu, který chcete vytvořit žádost o oznámení pomocí vytvoření vazby na `SqlCommand` objektu.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="2cf1e-107">Po vytvoření žádosti, které už nepotřebujete `SqlNotificationRequest` objektu.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="2cf1e-108">Se můžete dotazovat frontu pro všechna naše oznámení a reagují odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="2cf1e-109">Oznámení může dojít i v případě, že aplikace se vypne a následně restartuje.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>  
  
 <span data-ttu-id="2cf1e-110">Při spuštění příkazu s související upozornění, všechny změny původní výsledek nastavit aktivační událost odeslání zprávy do fronty SQL Server, který jste nakonfigurovali v žádost o oznámení.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>  
  
 <span data-ttu-id="2cf1e-111">Jak dotazovat fronty SQL serveru a interpretovat zprávy je specifická pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="2cf1e-112">Aplikace zodpovídá za dotazování fronty a reakce na základě obsahu zprávy.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cf1e-113">Při použití SQL serveru na žádosti oznámení se <xref:System.Data.SqlClient.SqlDependency>, vytvořte vlastní název fronty místo použití výchozí název služby.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>  
  
 <span data-ttu-id="2cf1e-114">Neexistují žádné nové prvky zabezpečení na straně klienta pro <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="2cf1e-115">To je především funkce serveru a serveru byla vytvořena zvláštní oprávnění, které uživatelé musí mít na žádost o oznámení.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>  
  
### <a name="example"></a><span data-ttu-id="2cf1e-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="2cf1e-116">Example</span></span>  
 <span data-ttu-id="2cf1e-117">Následující fragment kódu ukazuje, jak vytvořit <xref:System.Data.Sql.SqlNotificationRequest> a přidružte jej k <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="2cf1e-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2cf1e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2cf1e-118">See Also</span></span>  
 [<span data-ttu-id="2cf1e-119">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="2cf1e-119">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="2cf1e-120">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="2cf1e-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
