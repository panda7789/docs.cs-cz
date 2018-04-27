---
title: Sledování SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2eeb5cf57e6efac77de4a76fe8131189273d5438
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="sql-tracking"></a><span data-ttu-id="90464-102">Sledování SQL</span><span class="sxs-lookup"><span data-stu-id="90464-102">SQL Tracking</span></span>
<span data-ttu-id="90464-103">Tento příklad znázorňuje, jak psát vlastní účastník sledování SQL, který zapíše sledování záznamů do databáze SQL.</span><span class="sxs-lookup"><span data-stu-id="90464-103">This sample demonstrates how to write a custom SQL tracking participant, that writes tracking records to a SQL database.</span></span> <span data-ttu-id="90464-104">Windows Workflow Foundation (WF) poskytuje pracovní postup, chcete-li získat přehled o provádění instanci pracovního postupu pro sledování.</span><span class="sxs-lookup"><span data-stu-id="90464-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="90464-105">Modul runtime sledování vysílá pracovní postup sledování záznamů během spouštění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="90464-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="90464-106"> pracovní postup sledování, najdete v části [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="90464-106"> workflow tracking, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="90464-107">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="90464-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="90464-108">Ověřte, máte systému SQL Server 2008, SQL Server 2008 Express nebo novější nainstalována.</span><span class="sxs-lookup"><span data-stu-id="90464-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="90464-109">Skriptů spojených s ukázkou předpokládá použití instance SQL Express na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="90464-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="90464-110">Pokud máte jinou instanci před spuštěním ukázky upravte skripty vztahující se k databázi.</span><span class="sxs-lookup"><span data-stu-id="90464-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>  
  
2.  <span data-ttu-id="90464-111">Vytvořte databázi systému SQL Server sledování spuštěním Trackingsetup.cmd v adresáři skripty (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span><span class="sxs-lookup"><span data-stu-id="90464-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="90464-112">Tím se vytvoří databáze názvem TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="90464-112">This creates a database called TrackingSample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="90464-113">Tento skript vytvoří databázi na výchozí instanci systému SQL Express.</span><span class="sxs-lookup"><span data-stu-id="90464-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="90464-114">Pokud chcete nainstalovat na jinou instanci databáze, upravte skript Trackingsetup.cmd.</span><span class="sxs-lookup"><span data-stu-id="90464-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>  
  
3.  <span data-ttu-id="90464-115">Otevřete SqlTrackingSample.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="90464-115">Open SqlTrackingSample.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="90464-116">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="90464-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="90464-117">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="90464-117">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="90464-118">Okno Prohlížeč otevře a ukazuje výpis pro aplikaci adresáře.</span><span class="sxs-lookup"><span data-stu-id="90464-118">The browser window opens and shows the directory listing for the application.</span></span>  
  
6.  <span data-ttu-id="90464-119">V prohlížeči klikněte na tlačítko StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="90464-119">In the browser, click StockPriceService.xamlx.</span></span>  
  
7.  <span data-ttu-id="90464-120">Prohlížeč zobrazí stránku StockPriceService, který obsahuje službu místní adresu WSDL.</span><span class="sxs-lookup"><span data-stu-id="90464-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="90464-121">Zkopírujte tuto adresu.</span><span class="sxs-lookup"><span data-stu-id="90464-121">Copy this address.</span></span>  
  
     <span data-ttu-id="90464-122">Je například adresa WSDL místní služby http://localhost:65193/StockPriceService.xamlx?wsdl.</span><span class="sxs-lookup"><span data-stu-id="90464-122">An example of the local service WSDL address is http://localhost:65193/StockPriceService.xamlx?wsdl.</span></span>  
  
8.  <span data-ttu-id="90464-123">Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], spuštění testovacího klienta WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="90464-123">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="90464-124">Je umístěn v adresáři 10.0\Common7\IDE Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90464-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>  
  
9. <span data-ttu-id="90464-125">V testu klienta WCF, klikněte na tlačítko **soubor** nabídku a vyberte **přidat službu**.</span><span class="sxs-lookup"><span data-stu-id="90464-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="90464-126">Vložte adresu místní služby do textového pole.</span><span class="sxs-lookup"><span data-stu-id="90464-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="90464-127">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="90464-127">Click **OK** to close the dialog.</span></span>  
  
10. <span data-ttu-id="90464-128">V testu klienta WCF, poklikejte na **GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="90464-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="90464-129">Tím se otevře `GetStockPrice` operace, které přijímá jeden parametr, zadejte hodnotu `Contoso` a klikněte na tlačítko **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="90464-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>  
  
11. <span data-ttu-id="90464-130">Záznamy emitovaného sledování se zapisují do databáze SQL.</span><span class="sxs-lookup"><span data-stu-id="90464-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="90464-131">Pokud chcete zobrazit záznamy sledování, otevřete databázi TrackingSample v SQL Management Studio a přejděte do tabulky.</span><span class="sxs-lookup"><span data-stu-id="90464-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="90464-132"> SQL Server Management Studio, najdete v části [představení SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645).</span><span class="sxs-lookup"><span data-stu-id="90464-132"> SQL Server Management Studio, see [Introducing SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645).</span></span> <span data-ttu-id="90464-133">SQL Server 2008 Management Studio Express si můžete stáhnout [zde](http://go.microsoft.com/fwlink/?LinkId=180520).</span><span class="sxs-lookup"><span data-stu-id="90464-133">SQL Server 2008 Management Studio Express can be downloaded [here](http://go.microsoft.com/fwlink/?LinkId=180520).</span></span> <span data-ttu-id="90464-134">Spuštění vyberte možnost dotazu na tabulky zobrazí data v rámci sledování záznamů uložených v obou tabulkách.</span><span class="sxs-lookup"><span data-stu-id="90464-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="90464-135">Chcete-li odinstalovat vzorku</span><span class="sxs-lookup"><span data-stu-id="90464-135">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="90464-136">Spusťte skript theTrackingcleanup.cmd v adresáři ukázkové (\WF\Basic\Tracking\SqlTracking).</span><span class="sxs-lookup"><span data-stu-id="90464-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="90464-137">Trackingcleanup.cmd pokusí o odstranění databáze v místním počítači SQL Express.</span><span class="sxs-lookup"><span data-stu-id="90464-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="90464-138">Pokud používáte jiné instance systému SQL server, upravte Trackingcleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="90464-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="90464-139">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="90464-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="90464-140">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="90464-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="90464-141">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="90464-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="90464-142">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="90464-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a><span data-ttu-id="90464-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="90464-143">See Also</span></span>  
 [<span data-ttu-id="90464-144">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="90464-144">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
