---
title: SqlDependency v aplikaci ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 51df8ad695b3e59b368499d35ac76cc7ac0cd6e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363361"
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="7327e-102">SqlDependency v aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7327e-102">SqlDependency in an ASP.NET Application</span></span>
<span data-ttu-id="7327e-103">Příklad v této části ukazuje, jak používat <xref:System.Data.SqlClient.SqlDependency> nepřímo s využitím technologie ASP.NET <xref:System.Web.Caching.SqlCacheDependency> objektu.</span><span class="sxs-lookup"><span data-stu-id="7327e-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="7327e-104"><xref:System.Web.Caching.SqlCacheDependency> Objektu používá <xref:System.Data.SqlClient.SqlDependency> čekat na oznámení a správně aktualizace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="7327e-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7327e-105">Ukázkový kód předpokládá, že je povoleno oznámení dotazů spuštěním skriptů v [povolení oznámení dotazů](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="7327e-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="7327e-106">O ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="7327e-106">About the Sample Application</span></span>  
 <span data-ttu-id="7327e-107">Ukázková aplikace používá k zobrazení informací o produktu z jediné stránce rozhraní ASP.NET Web **AdventureWorks** databáze systému SQL Server v <xref:System.Web.UI.WebControls.GridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7327e-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="7327e-108">Když se stránka načte, kód zapíše aktuální čas <xref:System.Web.UI.WebControls.Label> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7327e-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="7327e-109">Pak definuje <xref:System.Web.Caching.SqlCacheDependency> objektu a nastaví vlastnosti pro <xref:System.Web.Caching.Cache> objekt pro uložení dat mezipaměti pro až tři minuty.</span><span class="sxs-lookup"><span data-stu-id="7327e-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="7327e-110">Kód pak připojí k databázi a načte data.</span><span class="sxs-lookup"><span data-stu-id="7327e-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="7327e-111">Při načtení stránky a aplikace běží ASP.NET načte data z mezipaměti, který lze ověřit poznamenat, že čas na stránce nezmění.</span><span class="sxs-lookup"><span data-stu-id="7327e-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="7327e-112">Pokud monitorovaných změny dat, technologie ASP.NET zruší platnost mezipaměti a znovu vytvořit `GridView` ovládacího prvku pomocí čerstvá data, času zobrazeného v aktualizaci `Label` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7327e-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="7327e-113">Vytvoření ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="7327e-113">Creating the Sample Application</span></span>  
 <span data-ttu-id="7327e-114">Postupujte podle těchto kroků vytvořte a spusťte ukázkovou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="7327e-114">Follow these steps to create and run the sample application:</span></span>  
  
1.  <span data-ttu-id="7327e-115">Vytvoření nového webu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7327e-115">Create a new ASP.NET Web site.</span></span>  
  
2.  <span data-ttu-id="7327e-116">Přidat <xref:System.Web.UI.WebControls.Label> a <xref:System.Web.UI.WebControls.GridView> ovládacího prvku na stránku Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="7327e-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3.  <span data-ttu-id="7327e-117">Otevřete modul třídy stránky a přidejte následující direktivy:</span><span class="sxs-lookup"><span data-stu-id="7327e-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  <span data-ttu-id="7327e-118">Přidejte následující kód na stránce `Page_Load` událostí:</span><span class="sxs-lookup"><span data-stu-id="7327e-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  <span data-ttu-id="7327e-119">Přidat dvě metody helper, `GetConnectionString` a `GetSQL`.</span><span class="sxs-lookup"><span data-stu-id="7327e-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="7327e-120">Připojovací řetězec, který je definován používá integrované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7327e-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="7327e-121">Budete muset ověřte, že používáte účet má oprávnění potřebná databáze a že ukázkové databáze **AdventureWorks**, má oznámení povolena.</span><span class="sxs-lookup"><span data-stu-id="7327e-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span> <span data-ttu-id="7327e-122">Další informace najdete v tématu [zvláštní aspekty při používání oznámení dotazů](http://msdn.microsoft.com/library/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).</span><span class="sxs-lookup"><span data-stu-id="7327e-122">For more information, see [Special Considerations When Using Query Notifications](http://msdn.microsoft.com/library/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="7327e-123">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="7327e-123">Testing the Application</span></span>  
 <span data-ttu-id="7327e-124">Aplikace ukládá data zobrazí ve webovém formuláři do mezipaměti a aktualizuje ji každé tři minuty, pokud nebude žádná aktivita.</span><span class="sxs-lookup"><span data-stu-id="7327e-124">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="7327e-125">Pokud dojde ke změně do databáze, je mezipaměť aktualizovat okamžitě.</span><span class="sxs-lookup"><span data-stu-id="7327e-125">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="7327e-126">Spusťte aplikaci v sadě Visual Studio, který načte stránku do prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="7327e-126">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="7327e-127">Doba aktualizace mezipaměti, který se zobrazí označuje při poslední aktualizaci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="7327e-127">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="7327e-128">Počkejte tři minut a pak aktualizujte stránku, způsobuje na událost zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7327e-128">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="7327e-129">Všimněte si, že došlo ke změně času zobrazený na stránce.</span><span class="sxs-lookup"><span data-stu-id="7327e-129">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="7327e-130">Pokud obnovíte stránku za méně než tři minuty, zůstane stejný čas na stránku.</span><span class="sxs-lookup"><span data-stu-id="7327e-130">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="7327e-131">Teď umožňuje aktualizovat data v databázi, pomocí příkazu Transact-SQL, aktualizovat a aktualizujte stránku.</span><span class="sxs-lookup"><span data-stu-id="7327e-131">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="7327e-132">Zobrazuje nyní označuje, že do mezipaměti byly aktualizovány s nová data z databáze.</span><span class="sxs-lookup"><span data-stu-id="7327e-132">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="7327e-133">Všimněte si, že i když se aktualizuje mezipaměť, času zobrazený na stránce se nezmění, dokud nedojde k události postback.</span><span class="sxs-lookup"><span data-stu-id="7327e-133">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7327e-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="7327e-134">See Also</span></span>  
 [<span data-ttu-id="7327e-135">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="7327e-135">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="7327e-136">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="7327e-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
