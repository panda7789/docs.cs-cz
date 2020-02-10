---
title: Sledování SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 88f44e5362684f755695aab154842fad2274134d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094589"
---
# <a name="sql-tracking"></a><span data-ttu-id="db913-102">Sledování SQL</span><span class="sxs-lookup"><span data-stu-id="db913-102">SQL Tracking</span></span>
<span data-ttu-id="db913-103">Tato ukázka předvádí, jak napsat vlastního účastníka sledování SQL, který zapisuje záznamy sledování do databáze SQL.</span><span class="sxs-lookup"><span data-stu-id="db913-103">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="db913-104">Programovací model Windows Workflow Foundation (WF) poskytuje sledování pracovního postupu, které vám umožní získat přehled o spuštění instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="db913-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="db913-105">Sledovací modul Sledování generuje záznamy sledování pracovních postupů během provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="db913-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="db913-106">Další informace o sledování pracovního postupu najdete v tématu [sledování a trasování pracovních postupů](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="db913-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="db913-107">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="db913-107">To use this sample</span></span>

1. <span data-ttu-id="db913-108">Ověřte, že máte nainstalované SQL Server 2008 SQL Server 2008 Express nebo novější.</span><span class="sxs-lookup"><span data-stu-id="db913-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="db913-109">Skripty, které jsou součástí ukázky, předpokládají použití instance SQL Express na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="db913-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="db913-110">Pokud máte jinou instanci, před spuštěním ukázky prosím upravte skripty související s databází.</span><span class="sxs-lookup"><span data-stu-id="db913-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="db913-111">Vytvořte databázi sledování SQL Server spuštěním Trackingsetup. cmd v adresáři Scripts (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span><span class="sxs-lookup"><span data-stu-id="db913-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="db913-112">Tím se vytvoří databáze s názvem TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="db913-112">This creates a database called TrackingSample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="db913-113">Skript vytvoří databázi ve výchozí instanci serveru SQL Express.</span><span class="sxs-lookup"><span data-stu-id="db913-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="db913-114">Pokud ho chcete nainstalovat do jiné instance databáze, upravte skript Trackingsetup. cmd.</span><span class="sxs-lookup"><span data-stu-id="db913-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="db913-115">Otevřete SqlTrackingSample. sln v aplikaci Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="db913-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="db913-116">Stisknutím kláves CTRL+SHIFT+B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="db913-116">Press CTRL+SHIFT+B to build the solution.</span></span>

5. <span data-ttu-id="db913-117">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="db913-117">Press F5 to run the application.</span></span>

     <span data-ttu-id="db913-118">Otevře se okno prohlížeče a zobrazí se výpis adresáře pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="db913-118">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="db913-119">V prohlížeči klikněte na StockPriceService. xamlx.</span><span class="sxs-lookup"><span data-stu-id="db913-119">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="db913-120">Prohlížeč zobrazí stránku StockPriceService, která obsahuje adresu WSDL místní služby.</span><span class="sxs-lookup"><span data-stu-id="db913-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="db913-121">Zkopírujte tuto adresu.</span><span class="sxs-lookup"><span data-stu-id="db913-121">Copy this address.</span></span>

     <span data-ttu-id="db913-122">Příklad adresy WSDL místní služby je `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="db913-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="db913-123">Pomocí Průzkumníka souborů spusťte testovacího klienta WCF (WcfTestClient. exe).</span><span class="sxs-lookup"><span data-stu-id="db913-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="db913-124">Je umístěn v adresáři Microsoft Visual Studio 10.0 \ Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="db913-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>

9. <span data-ttu-id="db913-125">V testovacím klientovi WCF klikněte na nabídku **soubor** a vyberte **Přidat službu**.</span><span class="sxs-lookup"><span data-stu-id="db913-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="db913-126">Do textového pole vložte adresu místní služby.</span><span class="sxs-lookup"><span data-stu-id="db913-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="db913-127">Kliknutím na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="db913-127">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="db913-128">V testovacím klientovi WCF poklikejte na **GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="db913-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="db913-129">Tím se otevře operace `GetStockPrice`, která přijímá jeden parametr, zadáte hodnotu `Contoso` a kliknete na **vyvolat**.</span><span class="sxs-lookup"><span data-stu-id="db913-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="db913-130">Vypouštěné záznamy sledování se zapisují do SQL Database.</span><span class="sxs-lookup"><span data-stu-id="db913-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="db913-131">Chcete-li zobrazit záznamy sledování, otevřete databázi TrackingSample ve službě SQL Management Studio a přejděte do tabulky.</span><span class="sxs-lookup"><span data-stu-id="db913-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="db913-132">Další informace o SQL Server Management Studio najdete v tématu [Úvod do SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span><span class="sxs-lookup"><span data-stu-id="db913-132">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="db913-133">SQL Server 2008 Management Studio Express si můžete stáhnout [tady](https://www.microsoft.com/download/details.aspx?id=7593).</span><span class="sxs-lookup"><span data-stu-id="db913-133">SQL Server 2008 Management Studio Express can be downloaded [here](https://www.microsoft.com/download/details.aspx?id=7593).</span></span> <span data-ttu-id="db913-134">Spuštění dotazu SELECT v tabulkách zobrazuje data v záznamech sledování uložených v příslušných tabulkách.</span><span class="sxs-lookup"><span data-stu-id="db913-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="db913-135">Odinstalace ukázky</span><span class="sxs-lookup"><span data-stu-id="db913-135">To uninstall the sample</span></span>

1. <span data-ttu-id="db913-136">Spusťte skript theTrackingcleanup. cmd v ukázkovém adresáři (\WF\Basic\Tracking\SqlTracking).</span><span class="sxs-lookup"><span data-stu-id="db913-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>

    > [!NOTE]
    > <span data-ttu-id="db913-137">Trackingcleanup. cmd se pokusí odstranit databázi v místním počítači SQL Express.</span><span class="sxs-lookup"><span data-stu-id="db913-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="db913-138">Pokud používáte jinou instanci systému SQL Server, upravte Trackingcleanup. cmd.</span><span class="sxs-lookup"><span data-stu-id="db913-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db913-139">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="db913-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="db913-140">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="db913-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="db913-141">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="db913-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="db913-142">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="db913-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="db913-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="db913-143">See also</span></span>

- <span data-ttu-id="db913-144">[Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="db913-144">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
