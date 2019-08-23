---
title: SqlDependency v aplikaci ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: a93cb9da44985fa29a4975875564b384117ce76f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938457"
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="8f8b8-102">SqlDependency v aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8f8b8-102">SqlDependency in an ASP.NET Application</span></span>
<span data-ttu-id="8f8b8-103">Příklad v této části ukazuje, jak nepřímo použít <xref:System.Data.SqlClient.SqlDependency> objekt ASP.NET. <xref:System.Web.Caching.SqlCacheDependency></span><span class="sxs-lookup"><span data-stu-id="8f8b8-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="8f8b8-104"><xref:System.Web.Caching.SqlCacheDependency> Objekt<xref:System.Data.SqlClient.SqlDependency> používá k naslouchání oznámení a k správné aktualizaci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f8b8-105">Vzorový kód předpokládá, že jste povolili oznámení dotazů spuštěním skriptů v části [Povolení oznámení dotazů](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="8f8b8-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="8f8b8-106">O ukázkové aplikaci</span><span class="sxs-lookup"><span data-stu-id="8f8b8-106">About the Sample Application</span></span>  
 <span data-ttu-id="8f8b8-107">Ukázková aplikace používá jednu webovou stránku ASP.NET k zobrazení informací o produktu z databáze **AdventureWorks** SQL Server v <xref:System.Web.UI.WebControls.GridView> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="8f8b8-108">Při načtení stránky kód zapíše aktuální čas do <xref:System.Web.UI.WebControls.Label> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="8f8b8-109">Pak definuje <xref:System.Web.Caching.SqlCacheDependency> objekt a nastaví vlastnosti <xref:System.Web.Caching.Cache> objektu pro uložení dat mezipaměti až po dobu tří minut.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="8f8b8-110">Kód se pak připojí k databázi a načte data.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="8f8b8-111">Po načtení stránky a spuštění aplikace ASP.NET se načtou data z mezipaměti, kterou můžete ověřit tak, že si myslíte, že se čas na stránce nemění.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="8f8b8-112">Pokud se data monitorují, ASP.NET zruší platnost mezipaměti a znovu naplní `GridView` ovládací prvek novými daty a aktualizuje čas zobrazený `Label` v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="8f8b8-113">Vytvoření ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="8f8b8-113">Creating the Sample Application</span></span>  
 <span data-ttu-id="8f8b8-114">Pomocí těchto kroků vytvořte a spusťte ukázkovou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="8f8b8-114">Follow these steps to create and run the sample application:</span></span>  
  
1. <span data-ttu-id="8f8b8-115">Vytvořte nový web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-115">Create a new ASP.NET Web site.</span></span>  
  
2. <span data-ttu-id="8f8b8-116">Přidejte ovládací<xref:System.Web.UI.WebControls.GridView> prvek aanastránkuDefault.aspx.<xref:System.Web.UI.WebControls.Label></span><span class="sxs-lookup"><span data-stu-id="8f8b8-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3. <span data-ttu-id="8f8b8-117">Otevřete modul třídy stránky a přidejte následující direktivy:</span><span class="sxs-lookup"><span data-stu-id="8f8b8-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. <span data-ttu-id="8f8b8-118">Do `Page_Load` události stránky přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="8f8b8-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. <span data-ttu-id="8f8b8-119">Přidejte dvě pomocné metody `GetConnectionString` a. `GetSQL`</span><span class="sxs-lookup"><span data-stu-id="8f8b8-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="8f8b8-120">Připojovací řetězec definovaný pomocí integrovaného zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="8f8b8-121">Musíte ověřit, že účet, který používáte, má potřebná databázová oprávnění a že má ukázková databáze **AdventureWorks**povolená oznámení.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span>
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="8f8b8-122">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="8f8b8-122">Testing the Application</span></span>  
 <span data-ttu-id="8f8b8-123">Aplikace ukládá do mezipaměti data zobrazená ve webovém formuláři a aktualizuje je každé tři minuty, pokud neexistuje žádná aktivita.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-123">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="8f8b8-124">Pokud dojde ke změně v databázi, mezipaměť se okamžitě aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-124">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="8f8b8-125">Spusťte aplikaci ze sady Visual Studio, která načte stránku do prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-125">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="8f8b8-126">Zobrazený čas aktualizace mezipaměti indikuje, kdy se mezipaměť naposledy aktualizovala.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-126">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="8f8b8-127">Počkejte tři minuty a pak aktualizujte stránku, což způsobí, že dojde k události zpětného odeslání.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-127">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="8f8b8-128">Všimněte si, že se čas zobrazený na stránce změnil.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-128">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="8f8b8-129">Pokud stránku aktualizujete za méně než tři minuty, čas zobrazený na stránce zůstane stejný.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-129">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="8f8b8-130">Teď aktualizujte data v databázi pomocí příkazu Transact-SQL UPDATE a aktualizujte stránku.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-130">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="8f8b8-131">Čas zobrazený nyní indikuje, že se mezipaměť aktualizovala novými daty z databáze.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-131">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="8f8b8-132">Všimněte si, že i když je mezipaměť aktualizována, čas zobrazený na stránce se nemění, dokud nedojde k události zpětného odeslání.</span><span class="sxs-lookup"><span data-stu-id="8f8b8-132">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f8b8-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f8b8-133">See also</span></span>

- [<span data-ttu-id="8f8b8-134">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="8f8b8-134">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [<span data-ttu-id="8f8b8-135">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="8f8b8-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
