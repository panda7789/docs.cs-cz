---
title: SqlDependency v aplikaci ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 5465238e4b9deaa13c76cb35122fcaded7acd7f7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736656"
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="675f3-102">SqlDependency v aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="675f3-102">SqlDependency in an ASP.NET Application</span></span>
<span data-ttu-id="675f3-103">Příklad v této části ukazuje, jak používat <xref:System.Data.SqlClient.SqlDependency> nepřímo s využitím technologie ASP.NET <xref:System.Web.Caching.SqlCacheDependency> objektu.</span><span class="sxs-lookup"><span data-stu-id="675f3-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="675f3-104"><xref:System.Web.Caching.SqlCacheDependency> Objektu používá <xref:System.Data.SqlClient.SqlDependency> naslouchat oznámením a správně aktualizovat mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="675f3-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="675f3-105">Vzorový kód předpokládá, že jste povolili oznámení dotazů spuštěním skriptů v [povolení oznámení dotazů](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="675f3-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="675f3-106">O ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="675f3-106">About the Sample Application</span></span>  
 <span data-ttu-id="675f3-107">Ukázková aplikace používá k zobrazení informací o produktu z jediné stránce technologie ASP.NET **AdventureWorks** databázi SQL serveru <xref:System.Web.UI.WebControls.GridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="675f3-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="675f3-108">Když se stránka načte, zapíše kód aktuální čas <xref:System.Web.UI.WebControls.Label> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="675f3-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="675f3-109">Potom definuje <xref:System.Web.Caching.SqlCacheDependency> objekt a nastaví vlastnosti pro <xref:System.Web.Caching.Cache> objekt pro uložení data v mezipaměti pro až 3 minuty.</span><span class="sxs-lookup"><span data-stu-id="675f3-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="675f3-110">Kód poté se připojí k databázi a načítá data.</span><span class="sxs-lookup"><span data-stu-id="675f3-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="675f3-111">Při načtení stránky a je spuštěná aplikace ASP.NET se načtou data z mezipaměti, což můžete ověřit tak poznamenat, že čas na stránce nemění.</span><span class="sxs-lookup"><span data-stu-id="675f3-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="675f3-112">Pokud data monitoruje změní, ASP.NET zruší platnost mezipaměti a znovu vytvořit `GridView` ovládací prvek s čerstvá data, času zobrazeného v aktualizaci `Label` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="675f3-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="675f3-113">Vytvoření ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="675f3-113">Creating the Sample Application</span></span>  
 <span data-ttu-id="675f3-114">Postupujte podle těchto kroků k vytvoření a spuštění ukázkové aplikace:</span><span class="sxs-lookup"><span data-stu-id="675f3-114">Follow these steps to create and run the sample application:</span></span>  
  
1.  <span data-ttu-id="675f3-115">Vytvoření nového webu technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="675f3-115">Create a new ASP.NET Web site.</span></span>  
  
2.  <span data-ttu-id="675f3-116">Přidat <xref:System.Web.UI.WebControls.Label> a <xref:System.Web.UI.WebControls.GridView> ovládacího prvku na stránku Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="675f3-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3.  <span data-ttu-id="675f3-117">Otevřete modul třídy stránky a přidejte následující direktivy:</span><span class="sxs-lookup"><span data-stu-id="675f3-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  <span data-ttu-id="675f3-118">Přidejte následující kód na stránce `Page_Load` události:</span><span class="sxs-lookup"><span data-stu-id="675f3-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  <span data-ttu-id="675f3-119">Přidat dvě metody helper `GetConnectionString` a `GetSQL`.</span><span class="sxs-lookup"><span data-stu-id="675f3-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="675f3-120">Připojovací řetězec, který je definován používá integrované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="675f3-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="675f3-121">Budete muset ověřit, že používáte účet nemá oprávnění potřebné databáze a že ukázkovou databázi **AdventureWorks**, je oznámení jsou povolená.</span><span class="sxs-lookup"><span data-stu-id="675f3-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span> <span data-ttu-id="675f3-122">Další informace najdete v tématu [zvláštní aspekty při používání oznámení dotazů](https://msdn.microsoft.com/library/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).</span><span class="sxs-lookup"><span data-stu-id="675f3-122">For more information, see [Special Considerations When Using Query Notifications](https://msdn.microsoft.com/library/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="675f3-123">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="675f3-123">Testing the Application</span></span>  
 <span data-ttu-id="675f3-124">Aplikace ukládá do mezipaměti, data zobrazená ve webovém formuláři a aktualizuje se každé 3 minuty, pokud neexistuje žádná aktivita.</span><span class="sxs-lookup"><span data-stu-id="675f3-124">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="675f3-125">Pokud dojde ke změně k databázi, do mezipaměti se aktualizují okamžitě.</span><span class="sxs-lookup"><span data-stu-id="675f3-125">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="675f3-126">Spuštění aplikace ze sady Visual Studio, který načte stránku do prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="675f3-126">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="675f3-127">Čas aktualizace mezipaměti zobrazí označuje při poslední aktualizaci do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="675f3-127">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="675f3-128">Počkejte tři minuty a potom aktualizujte stránku, příčinou událost zpětného odeslání dojde k.</span><span class="sxs-lookup"><span data-stu-id="675f3-128">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="675f3-129">Všimněte si, že došlo ke změně času zobrazeného na stránce.</span><span class="sxs-lookup"><span data-stu-id="675f3-129">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="675f3-130">Pokud stránku aktualizujete za méně než tři minuty, času zobrazeného na stránce zůstanou stejné.</span><span class="sxs-lookup"><span data-stu-id="675f3-130">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="675f3-131">Nyní aktualizovat data v databázi, pomocí příkazu jazyka Transact-SQL, aktualizovat a aktualizujte stránku.</span><span class="sxs-lookup"><span data-stu-id="675f3-131">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="675f3-132">Času zobrazeného teď označuje, že mezipaměť byl aktualizován novými daty z databáze.</span><span class="sxs-lookup"><span data-stu-id="675f3-132">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="675f3-133">Všimněte si, že i když se aktualizuje mezipaměť, času zobrazeného na stránce se nezmění, dokud dojde k události postback.</span><span class="sxs-lookup"><span data-stu-id="675f3-133">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="675f3-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="675f3-134">See Also</span></span>  
 [<span data-ttu-id="675f3-135">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="675f3-135">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="675f3-136">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="675f3-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
