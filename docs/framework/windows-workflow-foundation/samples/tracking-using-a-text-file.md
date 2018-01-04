---
title: "Sledování pomocí textového souboru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1d4b3f319d86dd463dabc8b71be7c76c7fef41f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="tracking-using-a-text-file"></a><span data-ttu-id="1a741-102">Sledování pomocí textového souboru</span><span class="sxs-lookup"><span data-stu-id="1a741-102">Tracking Using a Text File</span></span>
<span data-ttu-id="1a741-103">Tento příklad ukazuje, jak rozšířit sledování v [!INCLUDE[wf](../../../../includes/wf-md.md)] tak, že vytvoříte vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="1a741-103">This sample demonstrates how to extend tracking in [!INCLUDE[wf](../../../../includes/wf-md.md)] by creating a custom tracking participant.</span></span> <span data-ttu-id="1a741-104">Sledování členové jsou třídy rozhraní .NET Framework, které dostanou záznamy sledování z modulu runtime, jak budou vygenerované.</span><span class="sxs-lookup"><span data-stu-id="1a741-104">Tracking participants are .NET Framework classes that receive tracking records from the runtime as they are emitted.</span></span> <span data-ttu-id="1a741-105">Můžete vytvořit účastník sledování přenos sledování události, které chcete podle toho, která je vyžadována pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="1a741-105">You can create a tracking participant to transport the tracking events to whichever destination is required for your scenario.</span></span> <span data-ttu-id="1a741-106">Například účastník sledování ETW (trasování událostí pro Windows) k dispozici jako součást [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a741-106">For example, ETW (Event Tracing for Windows) Tracking Participant is provided as part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="1a741-107">Sledování účastník v této ukázce zapíše záznamy ve formátu XML do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="1a741-107">The tracking participant in this sample writes the records in XML format to a text file.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="1a741-108">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1a741-108">Sample details</span></span>  
 <span data-ttu-id="1a741-109">K optimalizaci užitečnost a odolnost vaší sledování účastník, musí být vyplněna některé další kroky k správně propojit účastník sledování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1a741-109">To optimize the usefulness and robustness of your tracking participant, some additional steps must be completed to properly wire the tracking participant to the runtime.</span></span> <span data-ttu-id="1a741-110">Následující tabulka popisuje třídy používané v této ukázce vytvoření sledování člena, který je v souladu s osvědčenými postupy.</span><span class="sxs-lookup"><span data-stu-id="1a741-110">The following table describes the classes used in this sample to create a tracking participant that complies with best practices.</span></span>  
  
|<span data-ttu-id="1a741-111">Třída</span><span class="sxs-lookup"><span data-stu-id="1a741-111">Class</span></span>|<span data-ttu-id="1a741-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1a741-112">Description</span></span>|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<span data-ttu-id="1a741-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> se používá k definování konfigurační oddíl slouží ke konfiguraci sledování účastník textového souboru.</span><span class="sxs-lookup"><span data-stu-id="1a741-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> is used to define the configuration section used to configure the text file tracking participant.</span></span> <span data-ttu-id="1a741-114">To umožňuje uživatelům zadat cílové umístění souboru protokolu pomocí standardní soubory konfigurace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1a741-114">This allows users to specify the destination of the log file using standard .NET Framework configuration files.</span></span>|  
|`TextFileTrackingBehavior`|<span data-ttu-id="1a741-115">Chování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] povolit uživatelům vložit rozšíření do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1a741-115">Behaviors in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allow users to inject extensions into the runtime.</span></span> <span data-ttu-id="1a741-116">Toto chování účastník sledování přidá do služby při spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="1a741-116">This behavior adds the tracking participant to the service when the service starts.</span></span>|  
|`TextFileTrackingParticipant`|<span data-ttu-id="1a741-117">Sledování člena, který přijímá sledování účastníky v době běhu a ukládá je do souboru protokolu ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="1a741-117">The tracking participant that receives tracking participants at runtime and stores them to a log file as XML.</span></span>|  
  
## <a name="behavior-extension-elements-configuration"></a><span data-ttu-id="1a741-118">Konfigurace chování rozšíření elementy</span><span class="sxs-lookup"><span data-stu-id="1a741-118">Behavior Extension Elements Configuration</span></span>  
 <span data-ttu-id="1a741-119">Jeden krok je potřebný k použití elementu rozšíření chování výše popsané pomocí rozhraní .NET Framework konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="1a741-119">One more step is required to make use of the behavior extension element previously described using .NET Framework configuration files.</span></span> <span data-ttu-id="1a741-120">Následující konfigurace musí být umístěny v konfiguračních souborech, kde má být použita rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1a741-120">The following configuration must be placed in configuration files where the extension is to be used.</span></span>  
  
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
>  <span data-ttu-id="1a741-121">Naleznete v souboru Web.config v ukázce použití kompletní příklad konfigurace elementů rozšíření chování.</span><span class="sxs-lookup"><span data-stu-id="1a741-121">See the Web.config file in the sample for a complete example usage of behavior extension elements configuration.</span></span>  
  
## <a name="custom-tracking-records"></a><span data-ttu-id="1a741-122">Vlastní sledování záznamů</span><span class="sxs-lookup"><span data-stu-id="1a741-122">Custom Tracking Records</span></span>  
 <span data-ttu-id="1a741-123">Soubor GetStockPrices.cs ukazuje, jak vytvořit vlastní sledování záznamy uvnitř <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="1a741-123">The GetStockPrices.cs file demonstrates how to create custom tracking records from within a <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="1a741-124">Při spuštění ukázky, vyhledejte tento záznam.</span><span class="sxs-lookup"><span data-stu-id="1a741-124">Look for this record when running the sample.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1a741-125">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="1a741-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="1a741-126">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WFStockPriceApplication.sln.</span><span class="sxs-lookup"><span data-stu-id="1a741-126">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="1a741-127">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="1a741-127">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1a741-128">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="1a741-128">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="1a741-129">Okno Prohlížeč otevře a ukazuje výpis pro aplikaci adresáře.</span><span class="sxs-lookup"><span data-stu-id="1a741-129">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="1a741-130">V prohlížeči klikněte na tlačítko StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="1a741-130">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="1a741-131">Prohlížeč zobrazí **StockPriceService** stránky, který obsahuje adresu wsdl místní služby.</span><span class="sxs-lookup"><span data-stu-id="1a741-131">The browser displays the **StockPriceService** page, which contains the local service wsdl address.</span></span> <span data-ttu-id="1a741-132">Zkopírujte tuto adresu.</span><span class="sxs-lookup"><span data-stu-id="1a741-132">Copy this address.</span></span>  
  
     <span data-ttu-id="1a741-133">Příkladem adresu wsdl místní služby je http://localhost:53797/StockPriceService.xamlx?wsdl.</span><span class="sxs-lookup"><span data-stu-id="1a741-133">An example of the local service wsdl address is http://localhost:53797/StockPriceService.xamlx?wsdl.</span></span>  
  
6.  <span data-ttu-id="1a741-134">Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], přejděte na vaše [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] složky (%SystemDrive%\Program Files\Microsoft Visual Studio 10.0 je výchozí instalační složku).</span><span class="sxs-lookup"><span data-stu-id="1a741-134">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], go to your [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (the default installation folder is %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span></span> <span data-ttu-id="1a741-135">Vyhledejte Common7\IDE\ podsložky.</span><span class="sxs-lookup"><span data-stu-id="1a741-135">Then locate the Common7\IDE\ subfolder.</span></span>  
  
7.  <span data-ttu-id="1a741-136">Poklikejte na soubor WcfTestClient.exe ke spuštění testovacího klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="1a741-136">Double-click the WcfTestClient.exe file to launch the WCF Test Client.</span></span>  
  
8.  <span data-ttu-id="1a741-137">V testu klienta WCF, vyberte **přidat služby...**</span><span class="sxs-lookup"><span data-stu-id="1a741-137">In the WCF Test Client, select **Add Service…**</span></span> <span data-ttu-id="1a741-138">z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="1a741-138">from the **File** menu.</span></span>  
  
9. <span data-ttu-id="1a741-139">Vložte adresu URL, které jste právě zkopírovali, do textového pole.</span><span class="sxs-lookup"><span data-stu-id="1a741-139">Paste the URL you just copied into the text box.</span></span>  
  
10. <span data-ttu-id="1a741-140">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="1a741-140">Click **OK** to close the dialog.</span></span>  
  
11. <span data-ttu-id="1a741-141">Testování služby pomocí testovacího klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="1a741-141">Test the service using the WCF Test Client.</span></span>  
  
    1.  <span data-ttu-id="1a741-142">V testu klienta WCF, klikněte dvakrát na **GetStockPrice()** pod **IStockPriceService** uzlu.</span><span class="sxs-lookup"><span data-stu-id="1a741-142">In the WCF Test Client, double-click **GetStockPrice()** under the **IStockPriceService** node.</span></span>  
  
         <span data-ttu-id="1a741-143">**GetStockPrice()** metoda se zobrazí v pravém podokně se jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="1a741-143">The **GetStockPrice()** method appears in the right pane, with one parameter.</span></span>  
  
    2.  <span data-ttu-id="1a741-144">Zadejte ve společnosti Contoso jako hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="1a741-144">Type in Contoso as the value for the parameter.</span></span>  
  
    3.  <span data-ttu-id="1a741-145">Klikněte na tlačítko **vyvolání**.</span><span class="sxs-lookup"><span data-stu-id="1a741-145">Click **Invoke**.</span></span>  
  
12. <span data-ttu-id="1a741-146">Viz sledovaných události do souboru protokolu, který je umístěný v adresáři data aplikací v umístění % APPDATA%\trackingRecords.log.</span><span class="sxs-lookup"><span data-stu-id="1a741-146">See the tracked events in the log file located in your application data directory at %APPDATA%\trackingRecords.log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1a741-147">Data aplikací % je proměnná prostředí, který se přeloží na %SystemDrive%\Users\\< uživatelské jméno\>\AppData\Roaming v [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nebo Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="1a741-147">The %APPDATA% is an environment variable that resolves to %SystemDrive%\Users\\<username\>\AppData\Roaming in [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], or Windows Server 2008.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1a741-148">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="1a741-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1a741-149">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="1a741-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1a741-150">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="1a741-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1a741-151">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1a741-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a><span data-ttu-id="1a741-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a741-152">See Also</span></span>  
 [<span data-ttu-id="1a741-153">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="1a741-153">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
