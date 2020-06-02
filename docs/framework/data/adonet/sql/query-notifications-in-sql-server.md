---
title: Oznámení pro dotazy na SQL Serveru
description: Naučte se používat oznámení dotazů k upozorňování aplikací na změnu dat v SQL Server databázi, například na aktualizace zobrazení aplikace.
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 1351c83b6cc5837115321d53e8779c0f364c3099
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286220"
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="29cb0-103">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="29cb0-103">Query Notifications in SQL Server</span></span>
<span data-ttu-id="29cb0-104">Oznámení dotazů, která jsou postavená na Service Broker infrastruktuře, umožňují aplikacím upozorňování na změnu dat.</span><span class="sxs-lookup"><span data-stu-id="29cb0-104">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="29cb0-105">Tato funkce je zvláště užitečná pro aplikace, které poskytují mezipaměť informací z databáze aplikace, jako je například webová aplikace, a musí být upozorněni, když se změní zdrojová data.</span><span class="sxs-lookup"><span data-stu-id="29cb0-105">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="29cb0-106">Existují tři způsoby, jak můžete implementovat oznámení dotazů pomocí ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="29cb0-106">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1. <span data-ttu-id="29cb0-107">Implementace nízké úrovně je poskytována `SqlNotificationRequest` třídou, která zveřejňuje na straně serveru, a umožňuje tak spustit příkaz s požadavkem na oznámení.</span><span class="sxs-lookup"><span data-stu-id="29cb0-107">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2. <span data-ttu-id="29cb0-108">Implementace vysoké úrovně je poskytována `SqlDependency` třídou, což je třída, která poskytuje souhrnnou abstrakci funkcí oznamování mezi zdrojovou aplikací a SQL Server a umožňuje použít závislost ke zjištění změn na serveru.</span><span class="sxs-lookup"><span data-stu-id="29cb0-108">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="29cb0-109">Ve většině případů je to nejjednodušší a nejúčinnější způsob, jak využít SQL Serverch oznámení pomocí spravovaných klientských aplikací pomocí .NET Framework Zprostředkovatel dat pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="29cb0-109">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3. <span data-ttu-id="29cb0-110">Kromě toho webové aplikace sestavené pomocí ASP.NET 2,0 nebo novější mohou používat `SqlCacheDependency` pomocné třídy.</span><span class="sxs-lookup"><span data-stu-id="29cb0-110">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="29cb0-111">Oznámení dotazů se používají pro aplikace, které vyžadují aktualizaci zobrazení nebo ukládání do mezipaměti v reakci na změny v podkladových datech.</span><span class="sxs-lookup"><span data-stu-id="29cb0-111">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="29cb0-112">Microsoft SQL Server umožňuje aplikacím .NET Framework odeslat příkaz do SQL Server a požádat o oznámení při spuštění stejného příkazu by vzniklé sady výsledků liší od původně načtených.</span><span class="sxs-lookup"><span data-stu-id="29cb0-112">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="29cb0-113">Oznámení vytvořená na serveru jsou odesílána prostřednictvím front ke zpracování později.</span><span class="sxs-lookup"><span data-stu-id="29cb0-113">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="29cb0-114">Můžete nastavit oznámení pro příkazy SELECT a EXECUTE.</span><span class="sxs-lookup"><span data-stu-id="29cb0-114">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="29cb0-115">Při použití příkazu EXECUTE SQL Server zaregistruje oznámení pro provedení příkazu, nikoli samotný příkaz EXECUTE.</span><span class="sxs-lookup"><span data-stu-id="29cb0-115">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="29cb0-116">Příkaz musí splňovat požadavky a omezení příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="29cb0-116">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="29cb0-117">Když příkaz, který zaregistruje oznámení, obsahuje více než jeden příkaz, vytvoří databázový stroj oznámení pro každý příkaz v dávce.</span><span class="sxs-lookup"><span data-stu-id="29cb0-117">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="29cb0-118">Pokud vyvíjíte aplikaci, kde při změně dat potřebujete spolehlivá e-mailová oznámení, přečtěte si část **Plánování efektivní strategie oznámení dotazů** a **alternativy k dotazům na oznámení** v článku [plánování oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) .</span><span class="sxs-lookup"><span data-stu-id="29cb0-118">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) article.</span></span> <span data-ttu-id="29cb0-119">Další informace o oznámeních a SQL Server Service Brokerech dotazů naleznete v následujících odkazech na články v dokumentaci k SQL Server.</span><span class="sxs-lookup"><span data-stu-id="29cb0-119">For more information about Query Notifications and SQL Server Service Broker, see the following links to articles in the SQL Server documentation.</span></span>  
  
 <span data-ttu-id="29cb0-120">**Dokumentace SQL Serveru**</span><span class="sxs-lookup"><span data-stu-id="29cb0-120">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="29cb0-121">[Pomocí oznámení dotazů](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="29cb0-121">[Using Query Notifications](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span></span>  
  
- <span data-ttu-id="29cb0-122">[Vytvoření dotazu pro oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="29cb0-122">[Creating a Query for Notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="29cb0-123">[Vývoj (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="29cb0-123">[Development (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span></span>  
  
- <span data-ttu-id="29cb0-124">[InfoCenter pro vývojáře Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="29cb0-124">[Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="29cb0-125">[Příručka pro vývojáře (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="29cb0-125">[Developer's Guide (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="29cb0-126">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="29cb0-126">In This Section</span></span>  
 [<span data-ttu-id="29cb0-127">Povolení oznámení dotazů</span><span class="sxs-lookup"><span data-stu-id="29cb0-127">Enabling Query Notifications</span></span>](enabling-query-notifications.md)  
 <span data-ttu-id="29cb0-128">Popisuje, jak používat oznámení dotazů, včetně požadavků na jejich povolení a používání.</span><span class="sxs-lookup"><span data-stu-id="29cb0-128">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="29cb0-129">SqlDependency v aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="29cb0-129">SqlDependency in an ASP.NET Application</span></span>](sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="29cb0-130">Ukazuje, jak používat oznámení dotazů z aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="29cb0-130">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="29cb0-131">Detekce změn pomocí SqlDependency</span><span class="sxs-lookup"><span data-stu-id="29cb0-131">Detecting Changes with SqlDependency</span></span>](detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="29cb0-132">Ukazuje, jak rozpoznat, kdy se výsledky dotazu budou lišit od původně přijatých.</span><span class="sxs-lookup"><span data-stu-id="29cb0-132">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="29cb0-133">Provádění SqlCommand pomocí SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="29cb0-133">SqlCommand Execution with a SqlNotificationRequest</span></span>](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="29cb0-134">Ukazuje konfiguraci <xref:System.Data.SqlClient.SqlCommand> objektu pro práci s oznámením dotazu.</span><span class="sxs-lookup"><span data-stu-id="29cb0-134">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="29cb0-135">Odkaz</span><span class="sxs-lookup"><span data-stu-id="29cb0-135">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="29cb0-136">Popisuje <xref:System.Data.Sql.SqlNotificationRequest> třídu a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="29cb0-136">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="29cb0-137">Popisuje <xref:System.Data.SqlClient.SqlDependency> třídu a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="29cb0-137">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="29cb0-138">Popisuje <xref:System.Web.Caching.SqlCacheDependency> třídu a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="29cb0-138">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29cb0-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="29cb0-139">See also</span></span>

- [<span data-ttu-id="29cb0-140">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="29cb0-140">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="29cb0-141">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="29cb0-141">ADO.NET Overview</span></span>](../ado-net-overview.md)
