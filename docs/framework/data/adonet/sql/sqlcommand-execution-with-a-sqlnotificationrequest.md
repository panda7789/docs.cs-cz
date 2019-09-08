---
title: Provádění SqlCommand pomocí SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 3115bfb80d4e5e61ed49da11e36eaa37bc24334f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791530"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="40d32-102">Provádění SqlCommand pomocí SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="40d32-102">SqlCommand Execution with a SqlNotificationRequest</span></span>

<span data-ttu-id="40d32-103"><xref:System.Data.SqlClient.SqlCommand> Dá se nakonfigurovat tak, aby vygeneroval oznámení, když se změní data po načtení ze serveru, a sada výsledků by byla odlišná, pokud se dotaz znovu spustil.</span><span class="sxs-lookup"><span data-stu-id="40d32-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="40d32-104">To je užitečné ve scénářích, kdy chcete používat vlastní fronty oznámení na serveru nebo když nechcete zachovat živé objekty.</span><span class="sxs-lookup"><span data-stu-id="40d32-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>

## <a name="creating-the-notification-request"></a><span data-ttu-id="40d32-105">Vytváření žádosti o oznámení</span><span class="sxs-lookup"><span data-stu-id="40d32-105">Creating the Notification Request</span></span>

<span data-ttu-id="40d32-106">Pomocí <xref:System.Data.Sql.SqlNotificationRequest> objektu můžete vytvořit žádost o oznámení tak, že ji vytvoříte vazbou `SqlCommand` na objekt.</span><span class="sxs-lookup"><span data-stu-id="40d32-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="40d32-107">Po vytvoření žádosti už `SqlNotificationRequest` objekt nebudete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="40d32-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="40d32-108">Můžete zadat dotaz na frontu pro všechna oznámení a odpovídajícím způsobem reagovat.</span><span class="sxs-lookup"><span data-stu-id="40d32-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="40d32-109">K oznámením může dojít i v případě, že se aplikace vypíná a následně restartuje.</span><span class="sxs-lookup"><span data-stu-id="40d32-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>

<span data-ttu-id="40d32-110">Když se spustí příkaz s přidruženým oznámením, všechny změny v původní aktivační události sady výsledků odesílají zprávu do fronty SQL Server, která byla nakonfigurovaná v žádosti o oznámení.</span><span class="sxs-lookup"><span data-stu-id="40d32-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>

<span data-ttu-id="40d32-111">Způsob dotazování fronty SQL Server a interpretace zprávy jsou specifické pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="40d32-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="40d32-112">Aplikace zodpovídá za cyklické dotazování fronty a na základě obsahu zprávy.</span><span class="sxs-lookup"><span data-stu-id="40d32-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>

> [!NOTE]
> <span data-ttu-id="40d32-113">Pokud používáte požadavky na oznamování <xref:System.Data.SqlClient.SqlDependency>SQL Server s, vytvořte vlastní název fronty namísto použití výchozího názvu služby.</span><span class="sxs-lookup"><span data-stu-id="40d32-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>

<span data-ttu-id="40d32-114">Neexistují žádné nové prvky zabezpečení na straně klienta pro <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="40d32-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="40d32-115">Tato funkce je primárně součástí serveru a Server vytvořil zvláštní oprávnění, která musí uživatelé vyžadovat pro vyžádání oznámení.</span><span class="sxs-lookup"><span data-stu-id="40d32-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>

### <a name="example"></a><span data-ttu-id="40d32-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="40d32-116">Example</span></span>

<span data-ttu-id="40d32-117">Následující fragment kódu ukazuje, jak vytvořit <xref:System.Data.Sql.SqlNotificationRequest> a přidružit ho <xref:System.Data.SqlClient.SqlCommand>k.</span><span class="sxs-lookup"><span data-stu-id="40d32-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>

```vb
' Assume connection is an open SqlConnection.
' Create a new SqlCommand object.
Dim command As New SqlCommand( _
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)

' Create a SqlNotificationRequest object.
Dim notifcationRequest As New SqlNotificationRequest()
notificationRequest.id = "NotificationID"
notificationRequest.Service = "mySSBQueue"

' Associate the notification request with the command.
command.Notification = notificationRequest
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
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="see-also"></a><span data-ttu-id="40d32-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40d32-118">See also</span></span>

- [<span data-ttu-id="40d32-119">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="40d32-119">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="40d32-120">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="40d32-120">ADO.NET Overview</span></span>](../ado-net-overview.md)
