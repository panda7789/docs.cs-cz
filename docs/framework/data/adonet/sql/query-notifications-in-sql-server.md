---
title: Oznámení pro dotazy na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 94171c8dac59fc17b0dd699d87fc043651fa5b7a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791766"
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="5ca59-102">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="5ca59-102">Query Notifications in SQL Server</span></span>
<span data-ttu-id="5ca59-103">Oznámení dotazů, která jsou postavená na Service Broker infrastruktuře, umožňují aplikacím upozorňování na změnu dat.</span><span class="sxs-lookup"><span data-stu-id="5ca59-103">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="5ca59-104">Tato funkce je zvláště užitečná pro aplikace, které poskytují mezipaměť informací z databáze aplikace, jako je například webová aplikace, a musí být upozorněni, když se změní zdrojová data.</span><span class="sxs-lookup"><span data-stu-id="5ca59-104">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="5ca59-105">Existují tři způsoby, jak můžete implementovat oznámení dotazů pomocí ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="5ca59-105">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1. <span data-ttu-id="5ca59-106">Implementace nízké úrovně je poskytována `SqlNotificationRequest` třídou, která zveřejňuje na straně serveru, a umožňuje tak spustit příkaz s požadavkem na oznámení.</span><span class="sxs-lookup"><span data-stu-id="5ca59-106">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2. <span data-ttu-id="5ca59-107">Implementace vysoké úrovně je poskytována `SqlDependency` třídou, což je třída, která poskytuje souhrnnou abstrakci funkcí oznamování mezi zdrojovou aplikací a SQL Server a umožňuje použít závislost ke zjištění změn v WebServer.</span><span class="sxs-lookup"><span data-stu-id="5ca59-107">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="5ca59-108">Ve většině případů je to nejjednodušší a nejúčinnější způsob, jak využít SQL Serverch oznámení pomocí spravovaných klientských aplikací pomocí .NET Framework Zprostředkovatel dat pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ca59-108">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3. <span data-ttu-id="5ca59-109">Kromě toho webové aplikace sestavené pomocí ASP.NET 2,0 nebo novější mohou používat `SqlCacheDependency` pomocné třídy.</span><span class="sxs-lookup"><span data-stu-id="5ca59-109">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="5ca59-110">Oznámení dotazů se používají pro aplikace, které vyžadují aktualizaci zobrazení nebo ukládání do mezipaměti v reakci na změny v podkladových datech.</span><span class="sxs-lookup"><span data-stu-id="5ca59-110">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="5ca59-111">Microsoft SQL Server umožňuje aplikacím .NET Framework odeslat příkaz do SQL Server a požádat o oznámení při spuštění stejného příkazu by vzniklé sady výsledků liší od původně načtených.</span><span class="sxs-lookup"><span data-stu-id="5ca59-111">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="5ca59-112">Oznámení vytvořená na serveru jsou odesílána prostřednictvím front ke zpracování později.</span><span class="sxs-lookup"><span data-stu-id="5ca59-112">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="5ca59-113">Můžete nastavit oznámení pro příkazy SELECT a EXECUTE.</span><span class="sxs-lookup"><span data-stu-id="5ca59-113">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="5ca59-114">Při použití příkazu EXECUTE SQL Server zaregistruje oznámení pro provedení příkazu, nikoli samotný příkaz EXECUTE.</span><span class="sxs-lookup"><span data-stu-id="5ca59-114">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="5ca59-115">Příkaz musí splňovat požadavky a omezení příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="5ca59-115">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="5ca59-116">Když příkaz, který zaregistruje oznámení, obsahuje více než jeden příkaz, vytvoří databázový stroj oznámení pro každý příkaz v dávce.</span><span class="sxs-lookup"><span data-stu-id="5ca59-116">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="5ca59-117">Pokud vyvíjíte aplikaci, kde při změně dat potřebujete spolehlivá e-mailová oznámení, přečtěte si oddíly **Plánování efektivní strategie oznámení** a **alternativ k dotazům na oznámení** v [plánování pro Téma oznámení](https://go.microsoft.com/fwlink/?LinkId=211984) v SQL Server Knihy online.</span><span class="sxs-lookup"><span data-stu-id="5ca59-117">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](https://go.microsoft.com/fwlink/?LinkId=211984) topic in SQL Server Books Online.</span></span> <span data-ttu-id="5ca59-118">Další informace o oznámeních a SQL Server Service Broker dotazů naleznete v následujících odkazech na témata v tématu SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="5ca59-118">For more information about Query Notifications and SQL Server Service Broker, see the following links to topics in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="5ca59-119">**Dokumentace k SQL Server**</span><span class="sxs-lookup"><span data-stu-id="5ca59-119">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="5ca59-120">[Pomocí oznámení dotazů](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="5ca59-120">[Using Query Notifications](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span></span>  
  
- <span data-ttu-id="5ca59-121">[Vytvoření dotazu pro oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="5ca59-121">[Creating a Query for Notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="5ca59-122">[Vývoj (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="5ca59-122">[Development (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span></span>  
  
- <span data-ttu-id="5ca59-123">[InfoCenter pro vývojáře Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="5ca59-123">[Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="5ca59-124">[Příručka pro vývojáře (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="5ca59-124">[Developer's Guide (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ca59-125">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5ca59-125">In This Section</span></span>  
 [<span data-ttu-id="5ca59-126">Povolení oznámení dotazů</span><span class="sxs-lookup"><span data-stu-id="5ca59-126">Enabling Query Notifications</span></span>](enabling-query-notifications.md)  
 <span data-ttu-id="5ca59-127">Popisuje, jak používat oznámení dotazů, včetně požadavků na jejich povolení a používání.</span><span class="sxs-lookup"><span data-stu-id="5ca59-127">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="5ca59-128">SqlDependency v aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5ca59-128">SqlDependency in an ASP.NET Application</span></span>](sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="5ca59-129">Ukazuje, jak používat oznámení dotazů z aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5ca59-129">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="5ca59-130">Detekce změn pomocí SqlDependency</span><span class="sxs-lookup"><span data-stu-id="5ca59-130">Detecting Changes with SqlDependency</span></span>](detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="5ca59-131">Ukazuje, jak rozpoznat, kdy se výsledky dotazu budou lišit od původně přijatých.</span><span class="sxs-lookup"><span data-stu-id="5ca59-131">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="5ca59-132">Provádění SqlCommand pomocí SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="5ca59-132">SqlCommand Execution with a SqlNotificationRequest</span></span>](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="5ca59-133">Ukazuje konfiguraci <xref:System.Data.SqlClient.SqlCommand> objektu pro práci s oznámením dotazu.</span><span class="sxs-lookup"><span data-stu-id="5ca59-133">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5ca59-134">Reference</span><span class="sxs-lookup"><span data-stu-id="5ca59-134">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="5ca59-135"><xref:System.Data.Sql.SqlNotificationRequest> Popisuje třídu a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="5ca59-135">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="5ca59-136"><xref:System.Data.SqlClient.SqlDependency> Popisuje třídu a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="5ca59-136">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="5ca59-137"><xref:System.Web.Caching.SqlCacheDependency> Popisuje třídu a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="5ca59-137">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca59-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ca59-138">See also</span></span>

- [<span data-ttu-id="5ca59-139">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5ca59-139">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="5ca59-140">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5ca59-140">ADO.NET Overview</span></span>](../ado-net-overview.md)
