---
title: Povolení oznámení dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 84048a3fba2b32b1ae745160e2b405c04b738c65
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040230"
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="264e9-102">Povolení oznámení dotazů</span><span class="sxs-lookup"><span data-stu-id="264e9-102">Enabling Query Notifications</span></span>
<span data-ttu-id="264e9-103">Aplikace, které využívají oznámení dotazů, mají společnou sadu požadavků.</span><span class="sxs-lookup"><span data-stu-id="264e9-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="264e9-104">Váš zdroj dat musí být správně nakonfigurovaný tak, aby podporoval oznamování dotazů SQL, a uživatel musí mít správná oprávnění na straně klienta a na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="264e9-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="264e9-105">Pokud chcete používat oznámení dotazů, musíte:</span><span class="sxs-lookup"><span data-stu-id="264e9-105">To use query notifications you must:</span></span>  
  
- <span data-ttu-id="264e9-106">Povolí oznámení dotazů pro vaši databázi.</span><span class="sxs-lookup"><span data-stu-id="264e9-106">Enable query notifications for your database.</span></span>  
  
- <span data-ttu-id="264e9-107">Ujistěte se, že ID uživatele používané pro připojení k databázi má potřebná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="264e9-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
- <span data-ttu-id="264e9-108">Použijte objekt <xref:System.Data.SqlClient.SqlCommand> k provedení platného příkazu SELECT s přidruženým objektem oznámení – buď <xref:System.Data.SqlClient.SqlDependency> nebo <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="264e9-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
- <span data-ttu-id="264e9-109">Poskytněte kód pro zpracování oznámení v případě, že se data monitorují.</span><span class="sxs-lookup"><span data-stu-id="264e9-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="264e9-110">Požadavky na oznámení dotazů</span><span class="sxs-lookup"><span data-stu-id="264e9-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="264e9-111">Oznámení dotazů jsou podporována pouze pro příkazy SELECT, které splňují specifické požadavky.</span><span class="sxs-lookup"><span data-stu-id="264e9-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="264e9-112">Následující tabulka obsahuje odkazy na Service Broker a dokumentaci k oznámením o dotazech v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="264e9-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="264e9-113">**Dokumentace k SQL Server**</span><span class="sxs-lookup"><span data-stu-id="264e9-113">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="264e9-114">[Vytvoření dotazu pro oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="264e9-114">[Creating a Query for Notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="264e9-115">[Požadavky na zabezpečení pro Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="264e9-115">[Security Considerations for Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span></span>  
  
- <span data-ttu-id="264e9-116">[Zabezpečení a ochrana (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="264e9-116">[Security and Protection (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span></span>  
  
- <span data-ttu-id="264e9-117">[Bezpečnostní opatření pro služby oznamování](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="264e9-117">[Security Considerations for Notifications Services](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span></span>  
  
- <span data-ttu-id="264e9-118">[Oprávnění pro oznamování dotazů](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="264e9-118">[Query Notification Permissions](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span></span>  
  
- <span data-ttu-id="264e9-119">[Mezinárodní požadavky na Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="264e9-119">[International Considerations for Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span></span>  
  
- <span data-ttu-id="264e9-120">[Požadavky na návrh řešení (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="264e9-120">[Solution Design Considerations (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span></span>  
  
- <span data-ttu-id="264e9-121">[InfoCenter pro vývojáře Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="264e9-121">[Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="264e9-122">[Příručka pro vývojáře (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="264e9-122">[Developer's Guide (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="264e9-123">Povolení oznámení dotazů ke spuštění ukázkového kódu</span><span class="sxs-lookup"><span data-stu-id="264e9-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="264e9-124">Chcete-li povolit Service Broker v databázi **AdventureWorks** pomocí SQL Server Management Studio, spusťte následující příkaz Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="264e9-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="264e9-125">Aby ukázky oznámení dotazů běžely správně, musí se na databázovém serveru spustit následující příkazy jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="264e9-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="264e9-126">Oprávnění pro oznamování dotazů</span><span class="sxs-lookup"><span data-stu-id="264e9-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="264e9-127">Uživatelé, kteří provádějí příkazy požadující oznámení, musí mít oprávnění k přihlášení k odběru databáze oznámení na serveru.</span><span class="sxs-lookup"><span data-stu-id="264e9-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="264e9-128">Kód na straně klienta, který běží v případě částečné důvěryhodnosti, vyžaduje <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="264e9-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="264e9-129">Následující kód vytvoří objekt <xref:System.Data.SqlClient.SqlClientPermission> a nastaví <xref:System.Security.Permissions.PermissionState> na <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span><span class="sxs-lookup"><span data-stu-id="264e9-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="264e9-130"><xref:System.Security.CodeAccessPermission.Demand%2A> vynutí <xref:System.Security.SecurityException> v době běhu, pokud mu nebyla udělena žádná oprávnění volající vyšší v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="264e9-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="264e9-131">Výběr objektu oznámení</span><span class="sxs-lookup"><span data-stu-id="264e9-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="264e9-132">Rozhraní API pro oznamování dotazů poskytuje dva objekty pro zpracování oznámení: <xref:System.Data.SqlClient.SqlDependency> a <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="264e9-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="264e9-133">Obecně platí, že většina aplikací non-ASP.NET by měla používat objekt <xref:System.Data.SqlClient.SqlDependency>.</span><span class="sxs-lookup"><span data-stu-id="264e9-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="264e9-134">ASP.NET aplikace by měly používat vyšší úroveň <xref:System.Web.Caching.SqlCacheDependency>, která zabalí <xref:System.Data.SqlClient.SqlDependency> a poskytuje rozhraní pro správu oznámení a objektů mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="264e9-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="264e9-135">Použití třídy SqlDependency</span><span class="sxs-lookup"><span data-stu-id="264e9-135">Using SqlDependency</span></span>  
 <span data-ttu-id="264e9-136">Aby bylo možné použít <xref:System.Data.SqlClient.SqlDependency>, musí být pro SQL Server databázi povoleny Service Broker a uživatelé musí mít oprávnění k přijímání oznámení.</span><span class="sxs-lookup"><span data-stu-id="264e9-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="264e9-137">Service Broker objekty, jako je například fronta oznámení, jsou předdefinovány.</span><span class="sxs-lookup"><span data-stu-id="264e9-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="264e9-138">Kromě toho <xref:System.Data.SqlClient.SqlDependency> automaticky spouští pracovní vlákno pro zpracování oznámení, která jsou publikována do fronty. také analyzuje zprávu Service Broker a zpřístupňuje informace jako data argumentu události.</span><span class="sxs-lookup"><span data-stu-id="264e9-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="264e9-139"><xref:System.Data.SqlClient.SqlDependency> musí být inicializována voláním metody `Start` k vytvoření závislosti na databázi.</span><span class="sxs-lookup"><span data-stu-id="264e9-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="264e9-140">Toto je statická metoda, kterou je třeba volat pouze jednou při inicializaci aplikace pro každé požadované připojení databáze.</span><span class="sxs-lookup"><span data-stu-id="264e9-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="264e9-141">Metoda `Stop` by měla být volána při ukončení aplikace pro každé připojení závislosti, které bylo provedeno.</span><span class="sxs-lookup"><span data-stu-id="264e9-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="264e9-142">Použití SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="264e9-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="264e9-143">Naproti tomu <xref:System.Data.Sql.SqlNotificationRequest> vyžaduje, abyste sami implementovali celou naslouchající infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="264e9-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="264e9-144">Kromě toho musí být definované všechny podpůrné Service Broker objekty, jako jsou fronty, služby a typy zpráv podporované frontou.</span><span class="sxs-lookup"><span data-stu-id="264e9-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="264e9-145">Tento ruční přístup je užitečný v případě, že vaše aplikace vyžaduje speciální oznamovací zprávy nebo oznamovací chování nebo pokud je vaše aplikace součástí větší Service Broker aplikace.</span><span class="sxs-lookup"><span data-stu-id="264e9-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="264e9-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="264e9-146">See also</span></span>

- [<span data-ttu-id="264e9-147">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="264e9-147">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="264e9-148">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="264e9-148">ADO.NET Overview</span></span>](../ado-net-overview.md)
