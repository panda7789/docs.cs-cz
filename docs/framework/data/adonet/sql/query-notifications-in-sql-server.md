---
title: "Oznámení dotazu v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d922598cb31e60b1c1648884555695c1ba089726
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="66edd-102">Oznámení dotazu v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="66edd-102">Query Notifications in SQL Server</span></span>
<span data-ttu-id="66edd-103">Oznámení dotazů postavená na infrastruktuře služby Service Broker, umožňují aplikacím být upozorněni, když se data změnila.</span><span class="sxs-lookup"><span data-stu-id="66edd-103">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="66edd-104">Tato funkce je obzvláště užitečná pro aplikace, které poskytují mezipaměť informací z databáze, např. webové aplikace a musí být upozorněni, když se změní zdrojová data.</span><span class="sxs-lookup"><span data-stu-id="66edd-104">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="66edd-105">Můžete implementovat oznámení dotazů pomocí ADO.NET třemi způsoby:</span><span class="sxs-lookup"><span data-stu-id="66edd-105">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1.  <span data-ttu-id="66edd-106">Nízké úrovně implementace poskytuje `SqlNotificationRequest` třída, která zveřejňuje funkce na straně serveru, umožňuje spouštění příkazu se žádost o oznámení.</span><span class="sxs-lookup"><span data-stu-id="66edd-106">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2.  <span data-ttu-id="66edd-107">Poskytuje základní implementaci `SqlDependency` třídy, která je třída, která poskytuje vysokou úroveň abstrakce oznámení funkcí mezi zdrojová aplikace a SQL Server, což umožňuje použít ke zjištění změny v závislosti Server.</span><span class="sxs-lookup"><span data-stu-id="66edd-107">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="66edd-108">Ve většině případů je to nejjednodušší a co nejúčinnější způsob, jak využívat funkce oznámení systému SQL Server ve spravované klientským aplikacím pomocí zprostředkovatele dat .NET Framework pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="66edd-108">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3.  <span data-ttu-id="66edd-109">Kromě toho webové aplikace vyvíjené v technologii ASP.NET 2.0 nebo novější můžete použít `SqlCacheDependency` pomocné třídy.</span><span class="sxs-lookup"><span data-stu-id="66edd-109">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="66edd-110">Oznámení dotazů se používají pro aplikace, které potřebují k aktualizaci zobrazí nebo ukládá do mezipaměti v reakci na změny v základních datech.</span><span class="sxs-lookup"><span data-stu-id="66edd-110">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="66edd-111">Microsoft SQL Server umožňuje aplikacím rozhraní .NET Framework pro odeslání příkazu serveru SQL Server a žádost o oznámení, pokud provádění stejný příkaz vytvoří liší od nastavení nejdřív načíst sad výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="66edd-111">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="66edd-112">Vygenerovat na serveru se posílají oznámení prostřednictvím fronty zpracovat později.</span><span class="sxs-lookup"><span data-stu-id="66edd-112">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="66edd-113">Můžete nastavit oznámení pro vyberte a příkazy EXECUTE.</span><span class="sxs-lookup"><span data-stu-id="66edd-113">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="66edd-114">Při použití příkazu EXECUTE, zaregistruje systému SQL Server oznámení pro příkaz proveden místo příkaz EXECUTE sám sebe.</span><span class="sxs-lookup"><span data-stu-id="66edd-114">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="66edd-115">Příkaz musí splňovat požadavky a omezení pro příkaz SELECT.</span><span class="sxs-lookup"><span data-stu-id="66edd-115">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="66edd-116">Když příkaz, který registruje oznámení obsahuje více než jednoho příkazu, databázový stroj vytvoří oznámení pro každý příkaz v dávce.</span><span class="sxs-lookup"><span data-stu-id="66edd-116">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="66edd-117">Pokud vyvíjíte aplikace kde potřebujete spolehlivé dílčí sekundu oznámení při změně dat, přečtěte si oddíly **plánování strategie efektivní oznámení dotazu** a **alternativy k dotazu Oznámení** v [plánování oznámení](http://go.microsoft.com/fwlink/?LinkId=211984) téma v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="66edd-117">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](http://go.microsoft.com/fwlink/?LinkId=211984) topic in SQL Server Books Online.</span></span> <span data-ttu-id="66edd-118">Další informace o oznámení dotazů a SQL Server Service Broker najdete v následujících odkazů na témata v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="66edd-118">For more information about Query Notifications and SQL Server Service Broker, see the following links to topics in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="66edd-119">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="66edd-119">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="66edd-120">Pomocí oznámení dotazů</span><span class="sxs-lookup"><span data-stu-id="66edd-120">Using Query Notifications</span></span>](http://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [<span data-ttu-id="66edd-121">Vytváření dotazu pro oznámení</span><span class="sxs-lookup"><span data-stu-id="66edd-121">Creating a Query for Notification</span></span>](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [<span data-ttu-id="66edd-122">Služba Service Broker</span><span class="sxs-lookup"><span data-stu-id="66edd-122">Service Broker</span></span>](http://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [<span data-ttu-id="66edd-123">Service Broker vývojáře informační středisko</span><span class="sxs-lookup"><span data-stu-id="66edd-123">Service Broker Developer InfoCenter</span></span>](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [<span data-ttu-id="66edd-124">Vývoj (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="66edd-124">Development (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a><span data-ttu-id="66edd-125">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="66edd-125">In This Section</span></span>  
 [<span data-ttu-id="66edd-126">Povolení oznámení dotazů</span><span class="sxs-lookup"><span data-stu-id="66edd-126">Enabling Query Notifications</span></span>](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 <span data-ttu-id="66edd-127">Popisuje, jak používat oznámení dotazu, včetně požadavků pro povolení a jejich používání.</span><span class="sxs-lookup"><span data-stu-id="66edd-127">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="66edd-128">SqlDependency v aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66edd-128">SqlDependency in an ASP.NET Application</span></span>](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="66edd-129">Ukazuje, jak používat oznámení dotazu z aplikace technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="66edd-129">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="66edd-130">Detekce změn pomocí SqlDependency</span><span class="sxs-lookup"><span data-stu-id="66edd-130">Detecting Changes with SqlDependency</span></span>](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="66edd-131">Ukazuje, jak zjistit, kdy výsledky dotazu se bude lišit od těch, které původně obdrželi.</span><span class="sxs-lookup"><span data-stu-id="66edd-131">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="66edd-132">Provádění SqlCommand pomocí SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="66edd-132">SqlCommand Execution with a SqlNotificationRequest</span></span>](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="66edd-133">Ukazuje, konfigurace <xref:System.Data.SqlClient.SqlCommand> objekt pro práci s oznámení o dotazu.</span><span class="sxs-lookup"><span data-stu-id="66edd-133">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="66edd-134">Odkaz</span><span class="sxs-lookup"><span data-stu-id="66edd-134">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="66edd-135">Popisuje <xref:System.Data.Sql.SqlNotificationRequest> třídy a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="66edd-135">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="66edd-136">Popisuje <xref:System.Data.SqlClient.SqlDependency> třídy a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="66edd-136">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="66edd-137">Popisuje <xref:System.Web.Caching.SqlCacheDependency> třídy a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="66edd-137">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66edd-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="66edd-138">See Also</span></span>  
 [<span data-ttu-id="66edd-139">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="66edd-139">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="66edd-140">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="66edd-140">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
