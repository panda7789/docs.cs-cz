---
title: Sledování pomocí textového souboru
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: 19b4d544bc1d1c5bc9ebfa51b4ba28eb82c525d0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773344"
---
# <a name="tracking-using-a-text-file"></a><span data-ttu-id="22e46-102">Sledování pomocí textového souboru</span><span class="sxs-lookup"><span data-stu-id="22e46-102">Tracking Using a Text File</span></span>
<span data-ttu-id="22e46-103">Tato ukázka předvádí, jak rozšířit tak, že vytvoříte vlastní sledování účastník sledování ve Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="22e46-103">This sample demonstrates how to extend tracking in Windows Workflow Foundation (WF) by creating a custom tracking participant.</span></span> <span data-ttu-id="22e46-104">Sledování účastníci se tříd rozhraní .NET Framework, které přijímají sledování záznamů z modulu runtime, jako jsou emitovány.</span><span class="sxs-lookup"><span data-stu-id="22e46-104">Tracking participants are .NET Framework classes that receive tracking records from the runtime as they are emitted.</span></span> <span data-ttu-id="22e46-105">Můžete vytvořit sledování účastník přenést událostí sledování k libovolným cíl je povinné pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="22e46-105">You can create a tracking participant to transport the tracking events to whichever destination is required for your scenario.</span></span> <span data-ttu-id="22e46-106">Například je účastník sledování ETW (událost trasování pro Windows) poskytuje jako součást [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22e46-106">For example, ETW (Event Tracing for Windows) Tracking Participant is provided as part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="22e46-107">Účastník sledování v této ukázce zapíše záznamy ve formátu XML do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="22e46-107">The tracking participant in this sample writes the records in XML format to a text file.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="22e46-108">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="22e46-108">Sample details</span></span>  
 <span data-ttu-id="22e46-109">K optimalizaci užitečnost a odolnosti sledování účastník, je třeba provést některé další kroky správně propojí účastník sledování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="22e46-109">To optimize the usefulness and robustness of your tracking participant, some additional steps must be completed to properly wire the tracking participant to the runtime.</span></span> <span data-ttu-id="22e46-110">Následující tabulka popisuje třídy používané k vytvoření účastníkem sledování, která je v souladu s osvědčenými postupy v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="22e46-110">The following table describes the classes used in this sample to create a tracking participant that complies with best practices.</span></span>  
  
|<span data-ttu-id="22e46-111">Třída</span><span class="sxs-lookup"><span data-stu-id="22e46-111">Class</span></span>|<span data-ttu-id="22e46-112">Popis</span><span class="sxs-lookup"><span data-stu-id="22e46-112">Description</span></span>|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<span data-ttu-id="22e46-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> se používá k definování konfiguračního oddílu použít ke konfiguraci sledování účastník textového souboru.</span><span class="sxs-lookup"><span data-stu-id="22e46-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> is used to define the configuration section used to configure the text file tracking participant.</span></span> <span data-ttu-id="22e46-114">To umožňuje uživatelům zadat cíl protokolu pomocí standardní konfigurační soubory rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22e46-114">This allows users to specify the destination of the log file using standard .NET Framework configuration files.</span></span>|  
|`TextFileTrackingBehavior`|<span data-ttu-id="22e46-115">Chování ve službě WCF umožňují uživatelům vložení rozšíření do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="22e46-115">Behaviors in WCF allow users to inject extensions into the runtime.</span></span> <span data-ttu-id="22e46-116">Toto chování přidá účastník sledování ve službě při spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="22e46-116">This behavior adds the tracking participant to the service when the service starts.</span></span>|  
|`TextFileTrackingParticipant`|<span data-ttu-id="22e46-117">Účastník sledování, který přijímá sledování účastníci za běhu a uloží je do souboru protokolu ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="22e46-117">The tracking participant that receives tracking participants at runtime and stores them to a log file as XML.</span></span>|  
  
## <a name="behavior-extension-elements-configuration"></a><span data-ttu-id="22e46-118">Chování rozšíření elementy konfigurace</span><span class="sxs-lookup"><span data-stu-id="22e46-118">Behavior Extension Elements Configuration</span></span>  
 <span data-ttu-id="22e46-119">Dalším krokem je nutné použít rozšíření elementu chování výše popsaný pomocí konfiguračních souborů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22e46-119">One more step is required to make use of the behavior extension element previously described using .NET Framework configuration files.</span></span> <span data-ttu-id="22e46-120">Následující konfigurace musí být umístěn v konfiguračních souborech, ve kterém se má použít rozšíření.</span><span class="sxs-lookup"><span data-stu-id="22e46-120">The following configuration must be placed in configuration files where the extension is to be used.</span></span>  
  
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
>  <span data-ttu-id="22e46-121">Naleznete v souboru Web.config v ukázce Úplný příklad použití chování rozšíření elementů konfigurace.</span><span class="sxs-lookup"><span data-stu-id="22e46-121">See the Web.config file in the sample for a complete example usage of behavior extension elements configuration.</span></span>  
  
## <a name="custom-tracking-records"></a><span data-ttu-id="22e46-122">Vlastní sledování záznamů</span><span class="sxs-lookup"><span data-stu-id="22e46-122">Custom Tracking Records</span></span>  
 <span data-ttu-id="22e46-123">Soubor GetStockPrices.cs ukazuje, jak vytvořit vlastní záznamy sledování v rámci <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="22e46-123">The GetStockPrices.cs file demonstrates how to create custom tracking records from within a <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="22e46-124">Vyhledejte tento záznam při spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="22e46-124">Look for this record when running the sample.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="22e46-125">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="22e46-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="22e46-126">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WFStockPriceApplication.sln.</span><span class="sxs-lookup"><span data-stu-id="22e46-126">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="22e46-127">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="22e46-127">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="22e46-128">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="22e46-128">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="22e46-129">Okno prohlížeče se otevře a zobrazí výpisu adresáře pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="22e46-129">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="22e46-130">V prohlížeči klikněte na tlačítko StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="22e46-130">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="22e46-131">Prohlížeč zobrazí **StockPriceService** stránky, který obsahuje adresu místní služby wsdl.</span><span class="sxs-lookup"><span data-stu-id="22e46-131">The browser displays the **StockPriceService** page, which contains the local service wsdl address.</span></span> <span data-ttu-id="22e46-132">Zkopírujte tuto adresu.</span><span class="sxs-lookup"><span data-stu-id="22e46-132">Copy this address.</span></span>  
  
     <span data-ttu-id="22e46-133">Příkladem adresy místní služby wsdl je http://localhost:53797/StockPriceService.xamlx?wsdl.</span><span class="sxs-lookup"><span data-stu-id="22e46-133">An example of the local service wsdl address is http://localhost:53797/StockPriceService.xamlx?wsdl.</span></span>  
  
6.  <span data-ttu-id="22e46-134">Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], přejděte na stránku vaší [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] složky (výchozí instalační složka je %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span><span class="sxs-lookup"><span data-stu-id="22e46-134">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], go to your [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (the default installation folder is %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span></span> <span data-ttu-id="22e46-135">Vyhledejte podsložku Common7\IDE\.</span><span class="sxs-lookup"><span data-stu-id="22e46-135">Then locate the Common7\IDE\ subfolder.</span></span>  
  
7.  <span data-ttu-id="22e46-136">Poklikejte na soubor WcfTestClient.exe a spustit klienta testu WCF.</span><span class="sxs-lookup"><span data-stu-id="22e46-136">Double-click the WcfTestClient.exe file to launch the WCF Test Client.</span></span>  
  
8.  <span data-ttu-id="22e46-137">Testovací klient WCF, vyberte **přidat službu...**</span><span class="sxs-lookup"><span data-stu-id="22e46-137">In the WCF Test Client, select **Add Service…**</span></span> <span data-ttu-id="22e46-138">z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="22e46-138">from the **File** menu.</span></span>  
  
9. <span data-ttu-id="22e46-139">Vložte adresu URL, které jste zkopírovali do textového pole.</span><span class="sxs-lookup"><span data-stu-id="22e46-139">Paste the URL you just copied into the text box.</span></span>  
  
10. <span data-ttu-id="22e46-140">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="22e46-140">Click **OK** to close the dialog.</span></span>  
  
11. <span data-ttu-id="22e46-141">Test pomocí testovacího klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="22e46-141">Test the service using the WCF Test Client.</span></span>  
  
    1.  <span data-ttu-id="22e46-142">Testovací klient WCF, dvakrát klikněte na panel **GetStockPrice()** pod **IStockPriceService** uzlu.</span><span class="sxs-lookup"><span data-stu-id="22e46-142">In the WCF Test Client, double-click **GetStockPrice()** under the **IStockPriceService** node.</span></span>  
  
         <span data-ttu-id="22e46-143">**GetStockPrice()** metoda se zobrazí v pravém podokně s jedním parametrem.</span><span class="sxs-lookup"><span data-stu-id="22e46-143">The **GetStockPrice()** method appears in the right pane, with one parameter.</span></span>  
  
    2.  <span data-ttu-id="22e46-144">Zadejte ve společnosti Contoso jako hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="22e46-144">Type in Contoso as the value for the parameter.</span></span>  
  
    3.  <span data-ttu-id="22e46-145">Klikněte na tlačítko **vyvolat**.</span><span class="sxs-lookup"><span data-stu-id="22e46-145">Click **Invoke**.</span></span>  
  
12. <span data-ttu-id="22e46-146">Zobrazte sledované události do souboru protokolu, který je umístěný v adresáři data vaší aplikace v umístění % APPDATA%\trackingRecords.log.</span><span class="sxs-lookup"><span data-stu-id="22e46-146">See the tracked events in the log file located in your application data directory at %APPDATA%\trackingRecords.log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="22e46-147">% APPDATA % je proměnná prostředí, který se přeloží %SystemDrive%\Users\\< uživatelské jméno\>\AppData\Roaming v [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nebo Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="22e46-147">The %APPDATA% is an environment variable that resolves to %SystemDrive%\Users\\<username\>\AppData\Roaming in [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], or Windows Server 2008.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="22e46-148">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="22e46-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="22e46-149">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="22e46-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="22e46-150">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="22e46-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="22e46-151">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="22e46-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a><span data-ttu-id="22e46-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="22e46-152">See Also</span></span>  
 [<span data-ttu-id="22e46-153">Ukázky AppFabric monitorování</span><span class="sxs-lookup"><span data-stu-id="22e46-153">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
