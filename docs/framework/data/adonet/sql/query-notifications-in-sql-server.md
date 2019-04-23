---
title: Oznámení pro dotazy na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: e31a733635cf56a9c5e539dfb1d71d7d7037175a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336665"
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="7449e-102">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="7449e-102">Query Notifications in SQL Server</span></span>
<span data-ttu-id="7449e-103">Oznámení dotazů založené na řešení infrastruktury služby Service Broker, povolit aplikace, která vás upozorní, když se data změnila.</span><span class="sxs-lookup"><span data-stu-id="7449e-103">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="7449e-104">Tato funkce je zvláště užitečná pro aplikace, které poskytují mezipaměť informací z databáze, jako je například v případě webové aplikace a nutné upozornit, když je změněna zdrojová data.</span><span class="sxs-lookup"><span data-stu-id="7449e-104">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="7449e-105">Oznámení dotazů pomocí ADO.NET můžete implementovat třemi způsoby:</span><span class="sxs-lookup"><span data-stu-id="7449e-105">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1. <span data-ttu-id="7449e-106">Nízké úrovně implementace je poskytován `SqlNotificationRequest` třídy, která poskytuje funkce na straně serveru, můžete k provedení příkazu se žádost o oznámení.</span><span class="sxs-lookup"><span data-stu-id="7449e-106">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2. <span data-ttu-id="7449e-107">Poskytuje základní implementaci `SqlDependency` třídu, která je třída, která poskytuje vysokou úroveň abstrakce oznámení funkcí mezi zdrojová aplikace a SQL Server, můžete použít k detekci změn v závislosti Server.</span><span class="sxs-lookup"><span data-stu-id="7449e-107">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="7449e-108">Ve většině případů toto je nejjednodušší a nejúčinnější způsob využití možnosti oznámení systému SQL Server ve spravované klientským aplikacím pomocí zprostředkovatele dat .NET Framework pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7449e-108">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3. <span data-ttu-id="7449e-109">Kromě toho webových aplikací vytvořených pomocí technologie ASP.NET 2.0 nebo novější můžete použít `SqlCacheDependency` pomocné třídy.</span><span class="sxs-lookup"><span data-stu-id="7449e-109">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="7449e-110">Oznámení dotazů se používají pro aplikace, které je potřeba aktualizovat zobrazí nebo ukládá do mezipaměti v reakci na změny v podkladových datech.</span><span class="sxs-lookup"><span data-stu-id="7449e-110">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="7449e-111">Microsoft SQL Server umožňuje aplikacím rozhraní .NET Framework odeslat příkaz k systému SQL Server a žádost o oznámení, pokud spuštění stejného příkazu byste mohli vytvořit sad výsledků dotazu liší od původně načten.</span><span class="sxs-lookup"><span data-stu-id="7449e-111">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="7449e-112">Vygenerovat na serveru oznámení se posílají do fronty mohly být zpracovány později.</span><span class="sxs-lookup"><span data-stu-id="7449e-112">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="7449e-113">Můžete nastavit oznámení pro výběr a spouštění příkazů.</span><span class="sxs-lookup"><span data-stu-id="7449e-113">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="7449e-114">Při použití příkazu EXECUTE, SQL Server zaregistruje oznámení pro příkaz provedený místo samotného příkaz EXECUTE.</span><span class="sxs-lookup"><span data-stu-id="7449e-114">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="7449e-115">Příkaz musí splňovat požadavky a omezení pro příkaz SELECT.</span><span class="sxs-lookup"><span data-stu-id="7449e-115">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="7449e-116">Pokud příkaz, který registruje upozornění obsahuje více než jeden výraz, databázový stroj vytvoří upozornění pro každý příkaz v dávce.</span><span class="sxs-lookup"><span data-stu-id="7449e-116">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="7449e-117">Pokud vyvíjíte aplikaci kdy potřebujete spolehlivé sekunda oznámení při změně dat, přečtěte si oddíly **plánování strategie efektivní oznámení dotazů** a **alternativy k dotazu Oznámení** v [plánování oznámení](https://go.microsoft.com/fwlink/?LinkId=211984) téma v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="7449e-117">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](https://go.microsoft.com/fwlink/?LinkId=211984) topic in SQL Server Books Online.</span></span> <span data-ttu-id="7449e-118">Další informace o oznámení dotazů a SQL Server Service Broker viz následující odkazy na témata v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="7449e-118">For more information about Query Notifications and SQL Server Service Broker, see the following links to topics in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="7449e-119">**Dokumentaci k SQL serveru**</span><span class="sxs-lookup"><span data-stu-id="7449e-119">**SQL Server documentation**</span></span>  
  
-   <span data-ttu-id="7449e-120">[Použití oznámení dotazů](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="7449e-120">[Using Query Notifications](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span></span>  
  
-   <span data-ttu-id="7449e-121">[Vytvoření dotazu pro oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="7449e-121">[Creating a Query for Notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
-   <span data-ttu-id="7449e-122">[Vývoj (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="7449e-122">[Development (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span></span>  
  
-   <span data-ttu-id="7449e-123">[Informační středisko pro vývojáře služby Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="7449e-123">[Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
-   <span data-ttu-id="7449e-124">[Příručka pro vývojáře (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="7449e-124">[Developer's Guide (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7449e-125">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7449e-125">In This Section</span></span>  
 [<span data-ttu-id="7449e-126">Povolení oznámení dotazů</span><span class="sxs-lookup"><span data-stu-id="7449e-126">Enabling Query Notifications</span></span>](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 <span data-ttu-id="7449e-127">Popisuje, jak používat oznámení dotazů, včetně požadavků na povolení a jejich používání.</span><span class="sxs-lookup"><span data-stu-id="7449e-127">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="7449e-128">SqlDependency v aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7449e-128">SqlDependency in an ASP.NET Application</span></span>](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="7449e-129">Ukazuje, jak pomocí dotazu oznámení z aplikace technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7449e-129">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="7449e-130">Detekce změn pomocí SqlDependency</span><span class="sxs-lookup"><span data-stu-id="7449e-130">Detecting Changes with SqlDependency</span></span>](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="7449e-131">Ukazuje, jak zjistit, že výsledky dotazu se bude lišit od těch, které původně obdrželi.</span><span class="sxs-lookup"><span data-stu-id="7449e-131">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="7449e-132">Provádění SqlCommand pomocí SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="7449e-132">SqlCommand Execution with a SqlNotificationRequest</span></span>](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="7449e-133">Ukazuje, konfigurace <xref:System.Data.SqlClient.SqlCommand> objektu pro práci s oznámení o dotazu.</span><span class="sxs-lookup"><span data-stu-id="7449e-133">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7449e-134">Odkaz</span><span class="sxs-lookup"><span data-stu-id="7449e-134">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="7449e-135">Popisuje <xref:System.Data.Sql.SqlNotificationRequest> třídy a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="7449e-135">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="7449e-136">Popisuje <xref:System.Data.SqlClient.SqlDependency> třídy a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="7449e-136">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="7449e-137">Popisuje <xref:System.Web.Caching.SqlCacheDependency> třídy a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="7449e-137">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7449e-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7449e-138">See also</span></span>

- [<span data-ttu-id="7449e-139">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7449e-139">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="7449e-140">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="7449e-140">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
