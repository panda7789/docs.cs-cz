---
title: Sledování pomocí textového souboru
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: aa59ab8304c68873c938f42fc585be883b234ecc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805795"
---
# <a name="tracking-using-a-text-file"></a><span data-ttu-id="6e5d9-102">Sledování pomocí textového souboru</span><span class="sxs-lookup"><span data-stu-id="6e5d9-102">Tracking Using a Text File</span></span>
<span data-ttu-id="6e5d9-103">Tato ukázka ukazuje, jak rozšířit tak, že vytvoříte vlastní sledování účastník sledování v systému Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="6e5d9-103">This sample demonstrates how to extend tracking in Windows Workflow Foundation (WF) by creating a custom tracking participant.</span></span> <span data-ttu-id="6e5d9-104">Sledování členové jsou třídy rozhraní .NET Framework, které dostanou záznamy sledování z modulu runtime, jak budou vygenerované.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-104">Tracking participants are .NET Framework classes that receive tracking records from the runtime as they are emitted.</span></span> <span data-ttu-id="6e5d9-105">Můžete vytvořit účastník sledování přenos sledování události, které chcete podle toho, která je vyžadována pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-105">You can create a tracking participant to transport the tracking events to whichever destination is required for your scenario.</span></span> <span data-ttu-id="6e5d9-106">Například účastník sledování ETW (trasování událostí pro Windows) k dispozici jako součást [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e5d9-106">For example, ETW (Event Tracing for Windows) Tracking Participant is provided as part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="6e5d9-107">Sledování účastník v této ukázce zapíše záznamy ve formátu XML do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-107">The tracking participant in this sample writes the records in XML format to a text file.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="6e5d9-108">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6e5d9-108">Sample details</span></span>  
 <span data-ttu-id="6e5d9-109">K optimalizaci užitečnost a odolnost vaší sledování účastník, musí být vyplněna některé další kroky k správně propojit účastník sledování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-109">To optimize the usefulness and robustness of your tracking participant, some additional steps must be completed to properly wire the tracking participant to the runtime.</span></span> <span data-ttu-id="6e5d9-110">Následující tabulka popisuje třídy používané v této ukázce vytvoření sledování člena, který je v souladu s osvědčenými postupy.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-110">The following table describes the classes used in this sample to create a tracking participant that complies with best practices.</span></span>  
  
|<span data-ttu-id="6e5d9-111">Třída</span><span class="sxs-lookup"><span data-stu-id="6e5d9-111">Class</span></span>|<span data-ttu-id="6e5d9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6e5d9-112">Description</span></span>|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<span data-ttu-id="6e5d9-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> se používá k definování konfigurační oddíl slouží ke konfiguraci sledování účastník textového souboru.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> is used to define the configuration section used to configure the text file tracking participant.</span></span> <span data-ttu-id="6e5d9-114">To umožňuje uživatelům zadat cílové umístění souboru protokolu pomocí standardní soubory konfigurace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-114">This allows users to specify the destination of the log file using standard .NET Framework configuration files.</span></span>|  
|`TextFileTrackingBehavior`|<span data-ttu-id="6e5d9-115">Chování ve WCF umožňují uživatelům vložit rozšíření do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-115">Behaviors in WCF allow users to inject extensions into the runtime.</span></span> <span data-ttu-id="6e5d9-116">Toto chování účastník sledování přidá do služby při spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-116">This behavior adds the tracking participant to the service when the service starts.</span></span>|  
|`TextFileTrackingParticipant`|<span data-ttu-id="6e5d9-117">Sledování člena, který přijímá sledování účastníky v době běhu a ukládá je do souboru protokolu ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-117">The tracking participant that receives tracking participants at runtime and stores them to a log file as XML.</span></span>|  
  
## <a name="behavior-extension-elements-configuration"></a><span data-ttu-id="6e5d9-118">Konfigurace chování rozšíření elementy</span><span class="sxs-lookup"><span data-stu-id="6e5d9-118">Behavior Extension Elements Configuration</span></span>  
 <span data-ttu-id="6e5d9-119">Jeden krok je potřebný k použití elementu rozšíření chování výše popsané pomocí rozhraní .NET Framework konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-119">One more step is required to make use of the behavior extension element previously described using .NET Framework configuration files.</span></span> <span data-ttu-id="6e5d9-120">Následující konfigurace musí být umístěny v konfiguračních souborech, kde má být použita rozšíření.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-120">The following configuration must be placed in configuration files where the extension is to be used.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="6e5d9-121">Naleznete v souboru Web.config v ukázce použití kompletní příklad konfigurace elementů rozšíření chování.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-121">See the Web.config file in the sample for a complete example usage of behavior extension elements configuration.</span></span>  
  
## <a name="custom-tracking-records"></a><span data-ttu-id="6e5d9-122">Vlastní sledování záznamů</span><span class="sxs-lookup"><span data-stu-id="6e5d9-122">Custom Tracking Records</span></span>  
 <span data-ttu-id="6e5d9-123">Soubor GetStockPrices.cs ukazuje, jak vytvořit vlastní sledování záznamy uvnitř <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-123">The GetStockPrices.cs file demonstrates how to create custom tracking records from within a <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="6e5d9-124">Při spuštění ukázky, vyhledejte tento záznam.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-124">Look for this record when running the sample.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6e5d9-125">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="6e5d9-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="6e5d9-126">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WFStockPriceApplication.sln.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-126">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="6e5d9-127">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-127">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6e5d9-128">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-128">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="6e5d9-129">Okno Prohlížeč otevře a ukazuje výpis pro aplikaci adresáře.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-129">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="6e5d9-130">V prohlížeči klikněte na tlačítko StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-130">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="6e5d9-131">Prohlížeč zobrazí **StockPriceService** stránky, který obsahuje adresu wsdl místní služby.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-131">The browser displays the **StockPriceService** page, which contains the local service wsdl address.</span></span> <span data-ttu-id="6e5d9-132">Zkopírujte tuto adresu.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-132">Copy this address.</span></span>  
  
     <span data-ttu-id="6e5d9-133">Je například adresa wsdl místní služby http://localhost:53797/StockPriceService.xamlx?wsdl.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-133">An example of the local service wsdl address is http://localhost:53797/StockPriceService.xamlx?wsdl.</span></span>  
  
6.  <span data-ttu-id="6e5d9-134">Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], přejděte na vaše [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] složky (%SystemDrive%\Program Files\Microsoft Visual Studio 10.0 je výchozí instalační složku).</span><span class="sxs-lookup"><span data-stu-id="6e5d9-134">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], go to your [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (the default installation folder is %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span></span> <span data-ttu-id="6e5d9-135">Vyhledejte Common7\IDE\ podsložky.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-135">Then locate the Common7\IDE\ subfolder.</span></span>  
  
7.  <span data-ttu-id="6e5d9-136">Poklikejte na soubor WcfTestClient.exe ke spuštění testovacího klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-136">Double-click the WcfTestClient.exe file to launch the WCF Test Client.</span></span>  
  
8.  <span data-ttu-id="6e5d9-137">V testu klienta WCF, vyberte **přidat služby...**</span><span class="sxs-lookup"><span data-stu-id="6e5d9-137">In the WCF Test Client, select **Add Service…**</span></span> <span data-ttu-id="6e5d9-138">z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-138">from the **File** menu.</span></span>  
  
9. <span data-ttu-id="6e5d9-139">Vložte adresu URL, které jste právě zkopírovali, do textového pole.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-139">Paste the URL you just copied into the text box.</span></span>  
  
10. <span data-ttu-id="6e5d9-140">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-140">Click **OK** to close the dialog.</span></span>  
  
11. <span data-ttu-id="6e5d9-141">Testování služby pomocí testovacího klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-141">Test the service using the WCF Test Client.</span></span>  
  
    1.  <span data-ttu-id="6e5d9-142">V testu klienta WCF, klikněte dvakrát na **GetStockPrice()** pod **IStockPriceService** uzlu.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-142">In the WCF Test Client, double-click **GetStockPrice()** under the **IStockPriceService** node.</span></span>  
  
         <span data-ttu-id="6e5d9-143">**GetStockPrice()** metoda se zobrazí v pravém podokně se jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-143">The **GetStockPrice()** method appears in the right pane, with one parameter.</span></span>  
  
    2.  <span data-ttu-id="6e5d9-144">Zadejte ve společnosti Contoso jako hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-144">Type in Contoso as the value for the parameter.</span></span>  
  
    3.  <span data-ttu-id="6e5d9-145">Klikněte na tlačítko **vyvolání**.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-145">Click **Invoke**.</span></span>  
  
12. <span data-ttu-id="6e5d9-146">Viz sledovaných události do souboru protokolu, který je umístěný v adresáři data aplikací v umístění % APPDATA%\trackingRecords.log.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-146">See the tracked events in the log file located in your application data directory at %APPDATA%\trackingRecords.log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e5d9-147">Data aplikací % je proměnná prostředí, který se přeloží na %SystemDrive%\Users\\< uživatelské jméno\>\AppData\Roaming v [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nebo Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-147">The %APPDATA% is an environment variable that resolves to %SystemDrive%\Users\\<username\>\AppData\Roaming in [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], or Windows Server 2008.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6e5d9-148">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6e5d9-149">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6e5d9-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6e5d9-150">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6e5d9-151">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6e5d9-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a><span data-ttu-id="6e5d9-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e5d9-152">See Also</span></span>  
 [<span data-ttu-id="6e5d9-153">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="6e5d9-153">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
