---
title: Povolení oznámení dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: a2227b33c7caacdd04c7bf50082bb0cfab7f3302
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877614"
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="bab37-102">Povolení oznámení dotazů</span><span class="sxs-lookup"><span data-stu-id="bab37-102">Enabling Query Notifications</span></span>
<span data-ttu-id="bab37-103">Aplikace, které využívají oznámení dotazů mají společnou sadu požadavků.</span><span class="sxs-lookup"><span data-stu-id="bab37-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="bab37-104">Zdroj dat musí být správně nakonfigurované pro podporu oznámení dotazů SQL a uživatel musí mít správná oprávnění na straně klienta i stranu serveru.</span><span class="sxs-lookup"><span data-stu-id="bab37-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="bab37-105">Použití oznámení dotazů, že je nutné:</span><span class="sxs-lookup"><span data-stu-id="bab37-105">To use query notifications you must:</span></span>  
  
- <span data-ttu-id="bab37-106">Povolení oznámení dotazů pro vaši databázi.</span><span class="sxs-lookup"><span data-stu-id="bab37-106">Enable query notifications for your database.</span></span>  
  
- <span data-ttu-id="bab37-107">Ujistěte se, že ID uživatele pro připojení k databázi má potřebná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="bab37-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
- <span data-ttu-id="bab37-108">Použití <xref:System.Data.SqlClient.SqlCommand> pro spuštění platným příkazem SELECT s objektem přidružené oznámení – buď <xref:System.Data.SqlClient.SqlDependency> nebo <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="bab37-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
- <span data-ttu-id="bab37-109">Zadejte kód ke zpracování oznámení, pokud data monitoruje změny.</span><span class="sxs-lookup"><span data-stu-id="bab37-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="bab37-110">Požadavky na oznámení dotazů</span><span class="sxs-lookup"><span data-stu-id="bab37-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="bab37-111">Oznámení dotazů jsou podporována pouze pro příkazy SELECT, které splňují specifické požadavky.</span><span class="sxs-lookup"><span data-stu-id="bab37-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="bab37-112">Následující tabulka obsahuje odkazy na dokumentaci služby Service Broker a oznámení dotazů v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="bab37-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="bab37-113">**Dokumentaci k SQL serveru**</span><span class="sxs-lookup"><span data-stu-id="bab37-113">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="bab37-114">[Vytvoření dotazu pro oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="bab37-114">[Creating a Query for Notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="bab37-115">[Důležité informace o zabezpečení pro službu Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="bab37-115">[Security Considerations for Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span></span>  
  
- <span data-ttu-id="bab37-116">[Zabezpečení a ochranu (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="bab37-116">[Security and Protection (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span></span>  
  
- <span data-ttu-id="bab37-117">[Důležité informace o zabezpečení pro oznámení služby](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="bab37-117">[Security Considerations for Notifications Services](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span></span>  
  
- <span data-ttu-id="bab37-118">[Oprávnění pro dotaz oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="bab37-118">[Query Notification Permissions](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span></span>  
  
- <span data-ttu-id="bab37-119">[Mezinárodní důležité informace týkající se služby Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="bab37-119">[International Considerations for Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span></span>  
  
- <span data-ttu-id="bab37-120">[Aspekty návrhu řešení (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="bab37-120">[Solution Design Considerations (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span></span>  
  
- <span data-ttu-id="bab37-121">[Informační středisko pro vývojáře služby Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="bab37-121">[Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="bab37-122">[Příručka pro vývojáře (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="bab37-122">[Developer's Guide (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="bab37-123">Povolení oznámení dotazů pro spuštění vzorového kódu</span><span class="sxs-lookup"><span data-stu-id="bab37-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="bab37-124">Povolí službu Service Broker na **AdventureWorks** databáze pomocí SQL Server Management Studio, spusťte následující příkaz jazyka Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="bab37-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="bab37-125">Pro ukázky oznámení dotazů spuštěn správně musí provést následující příkazy jazyka Transact-SQL na serveru databáze.</span><span class="sxs-lookup"><span data-stu-id="bab37-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="bab37-126">Oprávnění pro dotaz oznámení</span><span class="sxs-lookup"><span data-stu-id="bab37-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="bab37-127">Uživatelé, kteří příkazy požadování oznámení musí mít odběru oznámení dotazů databáze oprávnění na serveru.</span><span class="sxs-lookup"><span data-stu-id="bab37-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="bab37-128">Kód na straně klienta, který běží v částečném vztahu důvěryhodnosti situace vyžaduje <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="bab37-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="bab37-129">Následující kód vytvoří <xref:System.Data.SqlClient.SqlClientPermission> objekt nastavení <xref:System.Security.Permissions.PermissionState> k <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span><span class="sxs-lookup"><span data-stu-id="bab37-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="bab37-130"><xref:System.Security.CodeAccessPermission.Demand%2A> Vynutí <xref:System.Security.SecurityException> v době běhu, pokud všichni volající v zásobníku volání vyšší nebyla udělena oprávnění.</span><span class="sxs-lookup"><span data-stu-id="bab37-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="bab37-131">Výběr objektu oznámení</span><span class="sxs-lookup"><span data-stu-id="bab37-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="bab37-132">Rozhraní API oznámení dotazů poskytuje dva objekty se zpracovat oznámení: <xref:System.Data.SqlClient.SqlDependency> a <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="bab37-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="bab37-133">Obecně platí, by měl používat většina aplikací – technologie ASP.NET <xref:System.Data.SqlClient.SqlDependency> objektu.</span><span class="sxs-lookup"><span data-stu-id="bab37-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="bab37-134">Aplikace ASP.NET by měly používat vyšší úrovni <xref:System.Web.Caching.SqlCacheDependency>, která zabalí <xref:System.Data.SqlClient.SqlDependency> a poskytuje rozhraní pro správu oznámení a mezipaměti objektů.</span><span class="sxs-lookup"><span data-stu-id="bab37-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="bab37-135">Používání třídy SqlDependency</span><span class="sxs-lookup"><span data-stu-id="bab37-135">Using SqlDependency</span></span>  
 <span data-ttu-id="bab37-136">Chcete-li použít <xref:System.Data.SqlClient.SqlDependency>, služba Service Broker musí být povolené pro databázi serveru SQL Server používá, a uživatelé musí mít oprávnění k přijímání oznámení.</span><span class="sxs-lookup"><span data-stu-id="bab37-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="bab37-137">Objekty služby Service Broker, jako jsou fronty oznámení jsou předdefinovány.</span><span class="sxs-lookup"><span data-stu-id="bab37-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="bab37-138">Kromě toho <xref:System.Data.SqlClient.SqlDependency> automaticky spustí pracovní vlákna ke zpracování oznámení, když jsou odeslány do fronty; také analyzuje zpráv služby Service Broker, odhalení příslušných informací jako argument data události.</span><span class="sxs-lookup"><span data-stu-id="bab37-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="bab37-139"><xref:System.Data.SqlClient.SqlDependency> musí být inicializován pomocí volání `Start` metodu pro vytvoření závislostí do databáze.</span><span class="sxs-lookup"><span data-stu-id="bab37-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="bab37-140">Toto je statická metoda, která musí být volána pouze jednou během inicializace aplikace pro každé připojení databáze vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="bab37-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="bab37-141">`Stop` Metoda by měla být volána při ukončení aplikace pro připojení závislost, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="bab37-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="bab37-142">Pomocí SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="bab37-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="bab37-143">Naproti tomu <xref:System.Data.Sql.SqlNotificationRequest> vyžaduje, abyste implementovat celou infrastrukturu naslouchání sami.</span><span class="sxs-lookup"><span data-stu-id="bab37-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="bab37-144">Kromě toho musí být definovány všechny podpůrné objekty služby Service Broker například fronty, služby a typy podporovaných fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="bab37-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="bab37-145">Tento manuální přístup je užitečný, pokud vaše aplikace vyžaduje speciální oznámení zpráv nebo oznámení chování, nebo pokud vaše aplikace je součástí větší aplikace, které služba Service Broker.</span><span class="sxs-lookup"><span data-stu-id="bab37-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab37-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bab37-146">See also</span></span>

- [<span data-ttu-id="bab37-147">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="bab37-147">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [<span data-ttu-id="bab37-148">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="bab37-148">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
