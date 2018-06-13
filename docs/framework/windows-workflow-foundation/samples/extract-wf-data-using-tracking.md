---
title: Extrahovat Data WF pomocí sledování
ms.date: 03/30/2017
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
ms.openlocfilehash: 22b147521d4ce0c72fadfb7adc81e05f10ce52b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519870"
---
# <a name="extract-wf-data-using-tracking"></a><span data-ttu-id="24ef5-102">Extrahovat Data WF pomocí sledování</span><span class="sxs-lookup"><span data-stu-id="24ef5-102">Extract WF Data using Tracking</span></span>
<span data-ttu-id="24ef5-103">Tento příklad znázorňuje způsob použití sledování extrahovat proměnné pracovního postupu a argumenty z aktivit pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="24ef5-103">This sample demonstrates how to use workflow tracking to extract workflow variables and arguments from activities.</span></span> <span data-ttu-id="24ef5-104">Také ukazuje přidání poznámky do sledování záznamů a extrahování dat datové části v rámci vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="24ef5-104">It also shows the addition of annotations to tracking records and the extraction of data payload within custom tracking records.</span></span> <span data-ttu-id="24ef5-105">Příklad používá účastník sledování trasování událostí pro Windows (ETW) extrahovat data z pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="24ef5-105">The sample uses the Event Tracing for Windows (ETW) tracking participant to extract data from the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="24ef5-106">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="24ef5-106">Sample Details</span></span>  
 <span data-ttu-id="24ef5-107">Windows Workflow Foundation (WF) poskytuje sledování, aby mohl získat přehled o provádění instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="24ef5-107">Windows Workflow Foundation (WF) provides tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="24ef5-108">Modul runtime sledování vysílá pracovní postup sledování záznamů během spouštění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="24ef5-108">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="24ef5-109">Společně s pracovním sledování záznamů můžete extrahovat data v rámci instance pracovního postupu z pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="24ef5-109">Along with the workflow tracking records, data within the workflow instance can be extracted from the workflow.</span></span> <span data-ttu-id="24ef5-110">V následujícím seznamu jsou uvedeny typy dat, které mohou být extrahovány z sledování záznamů:</span><span class="sxs-lookup"><span data-stu-id="24ef5-110">The following list details the types of data that can be extracted from tracking records:</span></span>  
  
1.  <span data-ttu-id="24ef5-111">Proměnné pracovního postupu v rámci aktivity a sledování záznamů během provádění aktivity.</span><span class="sxs-lookup"><span data-stu-id="24ef5-111">Workflow variables within an activity and tracking records during activity execution.</span></span>  
  
     <span data-ttu-id="24ef5-112">K extrakci proměnné pracovního postupu, jsou proměnné extrahovat zadán v profilu.</span><span class="sxs-lookup"><span data-stu-id="24ef5-112">To extract workflow variables, the variables to be extracted are specified in a profile.</span></span> <span data-ttu-id="24ef5-113">Proměnné extrahovat lze zadat pouze s `ActivityStateQueries`.</span><span class="sxs-lookup"><span data-stu-id="24ef5-113">Variables to be extracted can only be specified with `ActivityStateQueries`.</span></span> <span data-ttu-id="24ef5-114">Následující příklad kódu ukazuje profil sledování použitou k extrakci proměnné pracovního postupu z aktivity.</span><span class="sxs-lookup"><span data-stu-id="24ef5-114">The following code example demonstrates a tracking profile used to extract the workflow variable from an activity.</span></span>  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  <span data-ttu-id="24ef5-115">Argumenty aktivity a stav aktivity sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="24ef5-115">Activity arguments and activity state tracking records.</span></span>  
  
     <span data-ttu-id="24ef5-116">Argumenty definovat data způsob toky nebo zrušení aktivity.</span><span class="sxs-lookup"><span data-stu-id="24ef5-116">Arguments define the way data flows in or out of an activity.</span></span> <span data-ttu-id="24ef5-117">Argumenty, které mají být extrahovány jsou určeny pomocí <xref:System.Activities.Tracking.ActivityStateQuery>. Následující příklad kódu je sledování profil, který extrahuje `Value` argument.</span><span class="sxs-lookup"><span data-stu-id="24ef5-117">Arguments to be extracted are specified using an <xref:System.Activities.Tracking.ActivityStateQuery>.The following code example is a tracking profile that extracts the `Value` argument.</span></span>  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  <span data-ttu-id="24ef5-118">Poznámky jsou páry klíč/hodnota, které mohou být přidány do jakékoli sledování záznam, který je vygenerované.</span><span class="sxs-lookup"><span data-stu-id="24ef5-118">Annotations are key/value pairs that can be added to any tracking record that is emitted.</span></span>  
  
     <span data-ttu-id="24ef5-119">Poznámky sloužit jako označování mechanismus pro sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="24ef5-119">Annotations serve as a tagging mechanism for tracking records.</span></span> <span data-ttu-id="24ef5-120">Poznámky jsou přidány do sledování záznamů prostřednictvím profil sledování.</span><span class="sxs-lookup"><span data-stu-id="24ef5-120">Annotations are added to tracking records through a tracking profile.</span></span> <span data-ttu-id="24ef5-121">Poznámky můžete přidat do libovolného typu sledování dotazu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="24ef5-121">Annotations can be added to any type of a workflow tracking query.</span></span> <span data-ttu-id="24ef5-122">Následující příklad kódu je sledování profil, který ukazuje, jak lze přidat poznámky k záznamu sledování.</span><span class="sxs-lookup"><span data-stu-id="24ef5-122">The following code example is a tracking profile that shows how an annotation can be added to a tracking record.</span></span>  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  <span data-ttu-id="24ef5-123">Vlastní sledování záznamy jsou vygenerované z uživatelem definované aktivit.</span><span class="sxs-lookup"><span data-stu-id="24ef5-123">Custom tracking records are emitted from user-defined activities.</span></span>  
  
     <span data-ttu-id="24ef5-124">Vlastní sledování záznamů přenášet datové části definované v rámci této aktivity.</span><span class="sxs-lookup"><span data-stu-id="24ef5-124">Custom tracking records can carry payload data defined within this activity.</span></span> <span data-ttu-id="24ef5-125">Odběr pro vlastní sledování záznamy v profilu sledování umožňuje extrahování datové části v rámci záznamu sledování.</span><span class="sxs-lookup"><span data-stu-id="24ef5-125">Subscribing for custom tracking records in a tracking profile allows the extraction of the payload within the tracking record.</span></span> <span data-ttu-id="24ef5-126">Vlastní sledování záznamy lze extrahovat s vlastní <xref:System.Activities.Tracking.TrackingQuery>.</span><span class="sxs-lookup"><span data-stu-id="24ef5-126">The custom tracking records can be extracted with custom a <xref:System.Activities.Tracking.TrackingQuery>.</span></span> <span data-ttu-id="24ef5-127">Následující příklad kódu je sledování profil, který extrahuje záznam vlastní sledování spolu s jeho datové části.</span><span class="sxs-lookup"><span data-stu-id="24ef5-127">The following code example is a tracking profile that extracts a custom tracking record along with its payload.</span></span>  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 <span data-ttu-id="24ef5-128">Ukázka ukazuje extrahování proměnné, argumenty, vlastní záznamy a přidávat poznámky pomocí profil zadaný v souboru Web.config. Je povoleno sledování ukázkový pracovní postup služby přidáním `<etwTracking>` chování elementu.</span><span class="sxs-lookup"><span data-stu-id="24ef5-128">The sample demonstrates the extraction of a variables, arguments, custom records and adding annotations using a profile specified in a Web.config. Tracking is enabled on the sample workflow service by adding an `<etwTracking>` behavior element.</span></span> <span data-ttu-id="24ef5-129">Následující kód například umožňuje sledování `ExtractWorkflowVariables` sledovacího profilu.</span><span class="sxs-lookup"><span data-stu-id="24ef5-129">The following code example enables tracking for the `ExtractWorkflowVariables` tracking profile.</span></span>  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="24ef5-130">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="24ef5-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="24ef5-131">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WFStockPriceApplication.sln.</span><span class="sxs-lookup"><span data-stu-id="24ef5-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="24ef5-132">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="24ef5-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="24ef5-133">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="24ef5-133">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="24ef5-134">Okno Prohlížeč otevře a ukazuje výpis pro aplikaci adresáře.</span><span class="sxs-lookup"><span data-stu-id="24ef5-134">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="24ef5-135">V prohlížeči klikněte na tlačítko StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="24ef5-135">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="24ef5-136">Prohlížeč zobrazí stránku StockPriceService, který obsahuje službu místní adresu WSDL.</span><span class="sxs-lookup"><span data-stu-id="24ef5-136">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="24ef5-137">Zkopírujte tuto adresu.</span><span class="sxs-lookup"><span data-stu-id="24ef5-137">Copy this address.</span></span>  
  
     <span data-ttu-id="24ef5-138">Následující příklad ukazuje adresu WSDL místní služby.</span><span class="sxs-lookup"><span data-stu-id="24ef5-138">The following example shows a local service WSDL address.</span></span> `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  <span data-ttu-id="24ef5-139">Před vyvoláním služby, spusťte Prohlížeč událostí a zkontrolujte, zda protokol událostí naslouchá pro sledování události vygenerované ze služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="24ef5-139">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="24ef5-140">Z **spustit** nabídce vyberte možnost **nástroje pro správu** a potom **Prohlížeč událostí**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-140">From the **Start** menu, select **Administrative Tools** and then **Event Viewer**.</span></span>  
  
8.  <span data-ttu-id="24ef5-141">Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, a **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-141">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="24ef5-142">Klikněte pravým tlačítkem na **Microsoft** a vyberte **zobrazení** a potom **zobrazit protokoly pro ladění a**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-142">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="24ef5-143">Ujistěte se, že **zobrazit protokoly pro ladění a** zaškrtnutá možnost.</span><span class="sxs-lookup"><span data-stu-id="24ef5-143">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="24ef5-144">Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace serveru – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-144">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="24ef5-145">Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-145">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
10. <span data-ttu-id="24ef5-146">Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], otevřete testovacího klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="24ef5-146">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="24ef5-147">Testovacího klienta WCF (WcfTestClient.exe) se nachází v \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] instalační složka > \Common7\IDE\ složky.</span><span class="sxs-lookup"><span data-stu-id="24ef5-147">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="24ef5-148">Výchozí hodnota [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] instalační složka je C:\Program Files\Microsoft Visual Studio 10.0.</span><span class="sxs-lookup"><span data-stu-id="24ef5-148">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
11. <span data-ttu-id="24ef5-149">V testu klienta WCF, vyberte **přidat službu** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="24ef5-149">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="24ef5-150">Přidejte místní služba WSDL adresu, kterou jste zkopírovali dříve do vstupního pole.</span><span class="sxs-lookup"><span data-stu-id="24ef5-150">Add the local service WSDL address you copied earlier in the input box.</span></span>  
  
12. <span data-ttu-id="24ef5-151">V testu klienta WCF, klikněte dvakrát na `GetStockPrice`.</span><span class="sxs-lookup"><span data-stu-id="24ef5-151">In WCF test client, double-click `GetStockPrice`.</span></span>  
  
     <span data-ttu-id="24ef5-152">Tím se otevře `GetStockPrice` metoda.</span><span class="sxs-lookup"><span data-stu-id="24ef5-152">This opens the `GetStockPrice` method.</span></span> <span data-ttu-id="24ef5-153">Požadavek přijímá jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="24ef5-153">The request accepts one parameter.</span></span> <span data-ttu-id="24ef5-154">Použijte hodnotu **Contoso**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-154">Use the value **Contoso**.</span></span>  
  
13. <span data-ttu-id="24ef5-155">Klikněte na tlačítko **vyvolání**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-155">Click **Invoke**.</span></span>  
  
14. <span data-ttu-id="24ef5-156">Přepněte zpět do prohlížeče událostí a přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace serveru – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-156">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="24ef5-157">Klikněte pravým tlačítkem na **analytické** a vyberte **aktualizovat**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-157">Right-click **Analytic** and select **Refresh**.</span></span> <span data-ttu-id="24ef5-158">Pracovní postup události jsou události ID rozsahy 100 199.</span><span class="sxs-lookup"><span data-stu-id="24ef5-158">The workflow events are in the event ID ranges 100-199.</span></span>  
  
     <span data-ttu-id="24ef5-159">Události obsahovat poznámky, proměnné, argumentů a vlastní sledování záznamů, které se dají zobrazit události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="24ef5-159">The events contain the annotations, variables, arguments and custom tracking records that can be viewed in the event viewer.</span></span>  
  
## <a name="cleaning-up-in-the-event-viewer"></a><span data-ttu-id="24ef5-160">Čištění události prohlížeč</span><span class="sxs-lookup"><span data-stu-id="24ef5-160">Cleaning up in the Event Viewer</span></span>  
 <span data-ttu-id="24ef5-161">Analytické kanál v protokolu událostí může být vyčištěna události prohlížeč pomocí následujícího postupu.</span><span class="sxs-lookup"><span data-stu-id="24ef5-161">The analytic channel in the event log can be cleaned up in the Event Viewer by doing the following.</span></span>  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="24ef5-162">Vyčistěte (volitelné)</span><span class="sxs-lookup"><span data-stu-id="24ef5-162">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="24ef5-163">Otevřete Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="24ef5-163">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="24ef5-164">Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikace Aplikace serveru**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-164">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="24ef5-165">Klikněte pravým tlačítkem na **analytické** a vyberte **zakázat protokol**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-165">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="24ef5-166">Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikace Aplikace serveru**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-166">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="24ef5-167">Klikněte pravým tlačítkem na **analytické** a vyberte **vymazat protokol**.</span><span class="sxs-lookup"><span data-stu-id="24ef5-167">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
     <span data-ttu-id="24ef5-168">Vyberte **vymazat** možnost Vymazat události.</span><span class="sxs-lookup"><span data-stu-id="24ef5-168">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="24ef5-169">Známý problém</span><span class="sxs-lookup"><span data-stu-id="24ef5-169">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24ef5-170">V prohlížeči událostí, kde může dojít k selhání dekódovat události trasování událostí není známý problém.</span><span class="sxs-lookup"><span data-stu-id="24ef5-170">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="24ef5-171">Může zobrazit chybovou zprávu, která vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="24ef5-171">You may see an error message that looks like the following.</span></span>  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  <span data-ttu-id="24ef5-172">Pokud dojde k této chybě, klikněte na tlačítko **aktualizovat** v podokně Akce.</span><span class="sxs-lookup"><span data-stu-id="24ef5-172">If you encounter this error, click **Refresh** in the actions pane.</span></span> <span data-ttu-id="24ef5-173">Události by měl nyní dekódovat správně.</span><span class="sxs-lookup"><span data-stu-id="24ef5-173">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="24ef5-174">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="24ef5-174">The samples may already be installed on your computer.</span></span> <span data-ttu-id="24ef5-175">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="24ef5-175">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="24ef5-176">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="24ef5-176">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="24ef5-177">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="24ef5-177">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a><span data-ttu-id="24ef5-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="24ef5-178">See Also</span></span>  
 [<span data-ttu-id="24ef5-179">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="24ef5-179">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
