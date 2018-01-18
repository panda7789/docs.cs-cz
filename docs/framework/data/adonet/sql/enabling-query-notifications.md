---
title: "Povolení oznámení dotazů"
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
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c7b02ba7959a5cfc2205222655460026847c3098
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="50de3-102">Povolení oznámení dotazů</span><span class="sxs-lookup"><span data-stu-id="50de3-102">Enabling Query Notifications</span></span>
<span data-ttu-id="50de3-103">Aplikace, které využívají oznámení dotazů mají společnou sadu požadavků.</span><span class="sxs-lookup"><span data-stu-id="50de3-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="50de3-104">Váš zdroj dat musí být správně nakonfigurované pro podporu oznámení dotazů SQL a uživatel musí mít správná oprávnění na straně klienta a na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="50de3-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="50de3-105">Použití dotazu oznámení, že je potřeba:</span><span class="sxs-lookup"><span data-stu-id="50de3-105">To use query notifications you must:</span></span>  
  
-   <span data-ttu-id="50de3-106">Povolte oznámení dotazů pro vaši databázi.</span><span class="sxs-lookup"><span data-stu-id="50de3-106">Enable query notifications for your database.</span></span>  
  
-   <span data-ttu-id="50de3-107">Ujistěte se, že ID uživatele používané pro připojení k databázi musí mít potřebná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="50de3-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
-   <span data-ttu-id="50de3-108">Použití <xref:System.Data.SqlClient.SqlCommand> objekt, který chcete spustit platný příkaz SELECT s objektem přidružené oznámení – buď <xref:System.Data.SqlClient.SqlDependency> nebo <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="50de3-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
-   <span data-ttu-id="50de3-109">Zadejte kód pro zpracování oznámení, pokud data změny.</span><span class="sxs-lookup"><span data-stu-id="50de3-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="50de3-110">Požadavky na oznámení dotazu</span><span class="sxs-lookup"><span data-stu-id="50de3-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="50de3-111">Oznámení dotazů jsou podporována pouze pro příkazy SELECT, které splňují specifické požadavky.</span><span class="sxs-lookup"><span data-stu-id="50de3-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="50de3-112">Následující tabulka obsahuje odkazy na dokumentaci služby Service Broker a oznámení dotazů v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="50de3-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="50de3-113">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="50de3-113">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="50de3-114">Vytváření dotazu pro oznámení</span><span class="sxs-lookup"><span data-stu-id="50de3-114">Creating a Query for Notification</span></span>](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [<span data-ttu-id="50de3-115">Důležité informace o zabezpečení pro služby Service Broker</span><span class="sxs-lookup"><span data-stu-id="50de3-115">Security Considerations for Service Broker</span></span>](http://msdn.microsoft.com/library/ms166059.aspx)  
  
-   [<span data-ttu-id="50de3-116">Zabezpečení a ochrana (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="50de3-116">Security and Protection (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522911.aspx)  
  
-   [<span data-ttu-id="50de3-117">Důležité informace o zabezpečení pro služby oznámení</span><span class="sxs-lookup"><span data-stu-id="50de3-117">Security Considerations for Notifications Services</span></span>](http://msdn.microsoft.com/library/ms172604.aspx)  
  
-   [<span data-ttu-id="50de3-118">Oprávnění oznámení dotazu</span><span class="sxs-lookup"><span data-stu-id="50de3-118">Query Notification Permissions</span></span>](http://msdn.microsoft.com/library/ms188311.aspx)  
  
-   [<span data-ttu-id="50de3-119">Mezinárodní důležité informace týkající se služby Service Broker</span><span class="sxs-lookup"><span data-stu-id="50de3-119">International Considerations for Service Broker</span></span>](http://msdn.microsoft.com/library/ms166028.aspx)  
  
-   [<span data-ttu-id="50de3-120">Aspekty návrhu řešení (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="50de3-120">Solution Design Considerations (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522899.aspx)  
  
-   [<span data-ttu-id="50de3-121">Service Broker vývojáře informační středisko</span><span class="sxs-lookup"><span data-stu-id="50de3-121">Service Broker Developer InfoCenter</span></span>](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [<span data-ttu-id="50de3-122">Příručka pro vývojáře (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="50de3-122">Developer's Guide (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="50de3-123">Povolení oznámení dotazů spustit ukázkový kód</span><span class="sxs-lookup"><span data-stu-id="50de3-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="50de3-124">Chcete-li povolit služby Service Broker na **AdventureWorks** databázi pomocí SQL Server Management Studio, spusťte následující příkaz Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="50de3-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="50de3-125">Pro ukázky oznámení dotazů správné fungování je třeba spustit následující příkazy jazyka Transact-SQL na serveru databáze.</span><span class="sxs-lookup"><span data-stu-id="50de3-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="50de3-126">Oprávnění oznámení dotazu</span><span class="sxs-lookup"><span data-stu-id="50de3-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="50de3-127">Uživatelé, kteří spuštěním příkazů požadování oznámení musí mít přihlášení k odběru oznámení dotazů v databázi oprávnění na serveru.</span><span class="sxs-lookup"><span data-stu-id="50de3-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="50de3-128">Vyžaduje klienta kód, který běží v situaci, částečné důvěryhodnosti <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="50de3-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="50de3-129">Následující kód vytvoří <xref:System.Data.SqlClient.SqlClientPermission> objektu, nastavení <xref:System.Security.Permissions.PermissionState> k <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span><span class="sxs-lookup"><span data-stu-id="50de3-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="50de3-130"><xref:System.Security.CodeAccessPermission.Demand%2A> Vynutí <xref:System.Security.SecurityException> za běhu, pokud všechny volajícím vyšší v zásobníku volání nebylo uděleno oprávnění.</span><span class="sxs-lookup"><span data-stu-id="50de3-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="50de3-131">Výběr objekt oznámení</span><span class="sxs-lookup"><span data-stu-id="50de3-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="50de3-132">Rozhraní API oznámení dotazů poskytuje dva objekty zpracovat oznámení: <xref:System.Data.SqlClient.SqlDependency> a <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="50de3-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="50de3-133">Obecně platí, měli používat většinu aplikací technologie ASP.NET <xref:System.Data.SqlClient.SqlDependency> objektu.</span><span class="sxs-lookup"><span data-stu-id="50de3-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="50de3-134">Aplikace ASP.NET by měly používat vyšší úrovni <xref:System.Web.Caching.SqlCacheDependency>, která zabalí <xref:System.Data.SqlClient.SqlDependency> a poskytuje rozhraní pro správu oznámení a mezipaměti objektů.</span><span class="sxs-lookup"><span data-stu-id="50de3-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="50de3-135">Používání třídy SqlDependency</span><span class="sxs-lookup"><span data-stu-id="50de3-135">Using SqlDependency</span></span>  
 <span data-ttu-id="50de3-136">Chcete-li použít <xref:System.Data.SqlClient.SqlDependency>, služby Service Broker musí být povolena pro databázi systému SQL Server používá, a uživatelé musí mít oprávnění pro příjem oznámení.</span><span class="sxs-lookup"><span data-stu-id="50de3-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="50de3-137">Objekty služby Service Broker, například fronty oznámení jsou předdefinovány.</span><span class="sxs-lookup"><span data-stu-id="50de3-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="50de3-138">Kromě toho <xref:System.Data.SqlClient.SqlDependency> automaticky spustí pracovní vlákna ke zpracování oznámení, když jsou odeslány do fronty, je také analyzuje zpráv služby Service Broker, odhalení příslušných informací jako argument data události.</span><span class="sxs-lookup"><span data-stu-id="50de3-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="50de3-139"><xref:System.Data.SqlClient.SqlDependency>musí se inicializuje pomocí volání `Start` metodu pro vytvoření závislosti do databáze.</span><span class="sxs-lookup"><span data-stu-id="50de3-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="50de3-140">Toto je statickou metodu, kterou je lze volat pouze jednou během inicializace aplikace pro každé připojení databáze vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="50de3-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="50de3-141">`Stop` Metoda by měla být volána při ukončení aplikace pro každé připojení závislost, která byla vytvořená.</span><span class="sxs-lookup"><span data-stu-id="50de3-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="50de3-142">Pomocí SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="50de3-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="50de3-143">Naproti tomu <xref:System.Data.Sql.SqlNotificationRequest> vyžaduje, abyste implementovat celé infrastruktury naslouchání sami.</span><span class="sxs-lookup"><span data-stu-id="50de3-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="50de3-144">Kromě toho je nutné definovat všechny podpůrné objekty služby Service Broker například fronty, služby a typy nepodporuje fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="50de3-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="50de3-145">Tento ruční přístup je užitečné, pokud vaše aplikace vyžaduje speciální oznamující zprávy nebo oznámení chování, nebo pokud je aplikace součástí větší aplikace služby Service Broker.</span><span class="sxs-lookup"><span data-stu-id="50de3-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50de3-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="50de3-146">See Also</span></span>  
 [<span data-ttu-id="50de3-147">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="50de3-147">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="50de3-148">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="50de3-148">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
