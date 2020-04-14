---
title: Sledování SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 72bfcaac2903b3e7fa5679422ad4feaa79e93211
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243177"
---
# <a name="sql-tracking"></a><span data-ttu-id="4fb1f-102">Sledování SQL</span><span class="sxs-lookup"><span data-stu-id="4fb1f-102">SQL tracking</span></span>

<span data-ttu-id="4fb1f-103">Tato ukázka ukazuje, jak napsat vlastní SQL sledování účastníka, který zapisuje záznamy sledování do databáze SQL.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-103">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="4fb1f-104">Windows Workflow Foundation (WF) poskytuje sledování pracovního postupu pro získání přehledu o provádění instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="4fb1f-105">Doba sledování runtime vyzařuje záznamy sledování pracovního postupu během provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="4fb1f-106">Další informace o sledování pracovního postupu naleznete v [tématu Sledování pracovního postupu a trasování](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="4fb1f-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

## <a name="use-the-sample"></a><span data-ttu-id="4fb1f-107">Použijte vzorek</span><span class="sxs-lookup"><span data-stu-id="4fb1f-107">Use the sample</span></span>

1. <span data-ttu-id="4fb1f-108">Ověřte, zda máte nainstalován server SQL Server 2008, SQL Server 2008 Express nebo novější.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="4fb1f-109">Skripty zabalené s ukázkou předpokládají použití instance SQL Express v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="4fb1f-110">Pokud máte jinou instanci, upravte před spuštěním ukázky skripty související s databází.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="4fb1f-111">Databázi sledování serveru SQL Server vytvořte spuštěním souboru Trackingsetup.cmd v adresáři skriptů (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span><span class="sxs-lookup"><span data-stu-id="4fb1f-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="4fb1f-112">Tím se vytvoří databáze s názvem TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-112">This creates a database called TrackingSample.</span></span>

   > [!NOTE]
   > <span data-ttu-id="4fb1f-113">Skript vytvoří databázi na výchozí instanci SQL Express.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="4fb1f-114">Pokud ji chcete nainstalovat do jiné instance databáze, upravte skript Trackingsetup.cmd.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="4fb1f-115">Otevřete sqltrackingsample.sln v sadě Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="4fb1f-116">Řešení sestavte stisknutím **klávesy Ctrl**+**Shift**+**B.**</span><span class="sxs-lookup"><span data-stu-id="4fb1f-116">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

5. <span data-ttu-id="4fb1f-117">Stisknutím **klávesy F5** spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-117">Press **F5** to run the application.</span></span>

   <span data-ttu-id="4fb1f-118">Otevře se okno prohlížeče a zobrazí výpis adresáře pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-118">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="4fb1f-119">V prohlížeči klikněte na Soubor StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-119">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="4fb1f-120">Prohlížeč zobrazí stránku StockPriceService, která obsahuje adresu WSDL místní služby.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="4fb1f-121">Zkopírujte tuto adresu.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-121">Copy this address.</span></span>

   <span data-ttu-id="4fb1f-122">Příkladem adresy WSDL místní služby je `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="4fb1f-123">Pomocí Průzkumníka souborů spusťte testovacího klienta WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="4fb1f-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="4fb1f-124">Je umístěn v *adresáři Microsoft Visual Studio 10.0\Common7\IDE*.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-124">It's located in the *Microsoft Visual Studio 10.0\Common7\IDE directory*.</span></span>

9. <span data-ttu-id="4fb1f-125">V testovacím klientovi WCF klepněte na **nabídku Soubor** a vyberte **Přidat službu**.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="4fb1f-126">Vložte adresu místní služby do textového pole.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="4fb1f-127">Klepnutím na **tlačítko OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-127">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="4fb1f-128">V testovacím klientovi WCF poklepejte na **příkaz GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="4fb1f-129">Tím se `GetStockPrice` otevře operace, která přebírá `Contoso` jeden parametr, zadejte hodnotu a klepněte na tlačítko **Vyvolat**.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="4fb1f-130">Vyzařované záznamy sledování jsou zapsány do databáze SQL.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="4fb1f-131">Chcete-li zobrazit záznamy sledování, otevřete databázi TrackingSample v aplikaci SQL Management Studio a přejděte do tabulek.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="4fb1f-132">Spuštěním výběrového dotazu v tabulkách se zobrazí data v rámci záznamů sledování uložených v příslušných tabulkách.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-132">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

   <span data-ttu-id="4fb1f-133">Další informace o aplikaci SQL Server Management Studio naleznete [v tématu Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span><span class="sxs-lookup"><span data-stu-id="4fb1f-133">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="4fb1f-134">Stáhněte si SQL Server Management Studio [zde](https://aka.ms/ssmsfullsetup).</span><span class="sxs-lookup"><span data-stu-id="4fb1f-134">Download SQL Server Management Studio [here](https://aka.ms/ssmsfullsetup).</span></span>

## <a name="uninstall-the-sample"></a><span data-ttu-id="4fb1f-135">Odinstalace ukázky</span><span class="sxs-lookup"><span data-stu-id="4fb1f-135">Uninstall the sample</span></span>

1. <span data-ttu-id="4fb1f-136">Spusťte skript Trackingcleanup.cmd v ukázkovém adresáři (*\WF\Basic\Tracking\SqlTracking*).</span><span class="sxs-lookup"><span data-stu-id="4fb1f-136">Run theTrackingcleanup.cmd script in the sample directory (*\WF\Basic\Tracking\SqlTracking*).</span></span>

    > [!NOTE]
    > <span data-ttu-id="4fb1f-137">Trackingcleanup.cmd pokusí odstranit databázi v místním počítači SQL Express.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="4fb1f-138">Pokud používáte jinou instanci serveru SQL, upravte Trackingcleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4fb1f-139">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4fb1f-140">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="4fb1f-141">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4fb1f-142">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4fb1f-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="4fb1f-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fb1f-143">See also</span></span>

- <span data-ttu-id="4fb1f-144">[Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="4fb1f-144">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
