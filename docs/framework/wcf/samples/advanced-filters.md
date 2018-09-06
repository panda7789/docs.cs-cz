---
title: Rozšířené filtry
ms.date: 03/30/2017
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
ms.openlocfilehash: 7022384e8abe93f4276eec48785b3243ed926438
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042592"
---
# <a name="advanced-filters"></a><span data-ttu-id="24995-102">Rozšířené filtry</span><span class="sxs-lookup"><span data-stu-id="24995-102">Advanced Filters</span></span>
<span data-ttu-id="24995-103">Tato ukázka předvádí, směrovací služba Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="24995-103">This sample demonstrates a Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="24995-104">Směrovací služba je komponenta WCF, který umožňuje snadno do aplikace zahrnout směrovač založené na obsahu.</span><span class="sxs-lookup"><span data-stu-id="24995-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="24995-105">Tato ukázka se přizpůsobí standardní vzorek Kalkulačka WCF na komunikaci pomocí směrovací službou.</span><span class="sxs-lookup"><span data-stu-id="24995-105">This sample adapts the standard WCF Calculator sample to communicate using the routing service.</span></span> <span data-ttu-id="24995-106">Tento příklad ukazuje, jak definovat směrování logiky založené na obsahu prostřednictvím filtry zpráv a tabulky filtru zpráv.</span><span class="sxs-lookup"><span data-stu-id="24995-106">This sample shows how to define content-based routing logic through the use of message filters and message filter tables.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="24995-107">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="24995-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="24995-108">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="24995-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="24995-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="24995-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="24995-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="24995-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a><span data-ttu-id="24995-111">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="24995-111">Sample Details</span></span>  
 <span data-ttu-id="24995-112">V následující tabulce jsou uvedeny filtry zpráv, které jsou přidány do tabulky filtru zpráva směrovací služby.</span><span class="sxs-lookup"><span data-stu-id="24995-112">The following table shows the message filters that are added to the message filter table of the routing service.</span></span>  
  
|<span data-ttu-id="24995-113">Filtr</span><span class="sxs-lookup"><span data-stu-id="24995-113">Filter</span></span>|<span data-ttu-id="24995-114">Pravidlo</span><span class="sxs-lookup"><span data-stu-id="24995-114">Rule</span></span>|<span data-ttu-id="24995-115">Priorita</span><span class="sxs-lookup"><span data-stu-id="24995-115">Priority</span></span>|  
|------------|----------|--------------|  
|<span data-ttu-id="24995-116">Pokud (má hlavičky)</span><span class="sxs-lookup"><span data-stu-id="24995-116">If (has header)</span></span>|<span data-ttu-id="24995-117">Zaokrouhlení</span><span class="sxs-lookup"><span data-stu-id="24995-117">Rounding</span></span>|<span data-ttu-id="24995-118">2</span><span class="sxs-lookup"><span data-stu-id="24995-118">2</span></span>|  
|<span data-ttu-id="24995-119">Pokud (se zobrazila na Ep2)</span><span class="sxs-lookup"><span data-stu-id="24995-119">If (showed up on Ep2)</span></span>|<span data-ttu-id="24995-120">Pravidelné</span><span class="sxs-lookup"><span data-stu-id="24995-120">Regular</span></span>|<span data-ttu-id="24995-121">1</span><span class="sxs-lookup"><span data-stu-id="24995-121">1</span></span>|  
|<span data-ttu-id="24995-122">Pokud (zobrazila s Adresa2)</span><span class="sxs-lookup"><span data-stu-id="24995-122">If (showed up with Address2)</span></span>|<span data-ttu-id="24995-123">Zaokrouhlení</span><span class="sxs-lookup"><span data-stu-id="24995-123">Rounding</span></span>|<span data-ttu-id="24995-124">1</span><span class="sxs-lookup"><span data-stu-id="24995-124">1</span></span>|  
|<span data-ttu-id="24995-125">Pokud (RoundRobin1)</span><span class="sxs-lookup"><span data-stu-id="24995-125">If (RoundRobin1)</span></span>|<span data-ttu-id="24995-126">Pravidelné</span><span class="sxs-lookup"><span data-stu-id="24995-126">Regular</span></span>|<span data-ttu-id="24995-127">0</span><span class="sxs-lookup"><span data-stu-id="24995-127">0</span></span>|  
|<span data-ttu-id="24995-128">Pokud (RoundRobin2)</span><span class="sxs-lookup"><span data-stu-id="24995-128">If (RoundRobin2)</span></span>|<span data-ttu-id="24995-129">Zaokrouhlení</span><span class="sxs-lookup"><span data-stu-id="24995-129">Rounding</span></span>|<span data-ttu-id="24995-130">0</span><span class="sxs-lookup"><span data-stu-id="24995-130">0</span></span>|  
  
 <span data-ttu-id="24995-131">Filtry zpráv a zpráva filtru tabulky lze vytvořit a nakonfigurovat prostřednictvím kódu nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="24995-131">The message filters and message filter tables can be created and configured either through code or in the application configuration file.</span></span> <span data-ttu-id="24995-132">Pro tuto ukázku můžete najít filtry zpráv a tabulky filtru zprávy prostřednictvím kódu v souboru RoutingService\routing.cs definované nebo definované v konfiguračním souboru aplikace v souboru RoutingService\App.config.</span><span class="sxs-lookup"><span data-stu-id="24995-132">For this sample, you can find the message filters and message filter tables defined through code in the RoutingService\routing.cs file, or defined in the application configuration file in the RoutingService\App.config file.</span></span> <span data-ttu-id="24995-133">Následující odstavce popisují způsob vytvoření filtry zpráv a zpráva filtr tabulky pro tuto ukázku prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="24995-133">The following paragraphs describe how the message filters and message filter tables are created for this sample through code.</span></span>  
  
 <span data-ttu-id="24995-134">Nejprve je potřeba <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> hledá vlastní hlavičce.</span><span class="sxs-lookup"><span data-stu-id="24995-134">First, an <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> looks for the custom header.</span></span> <span data-ttu-id="24995-135">Všimněte si, že <xref:System.ServiceModel.WSHttpBinding> výsledků ve verzi obálky pomocí protokolu SOAP 1.2, takže příkaz jazyka XPath je definována používání oboru názvů SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="24995-135">Note that <xref:System.ServiceModel.WSHttpBinding> results in an envelope version using SOAP 1.2, so the XPath statement is defined to use the SOAP 1.2 namespace.</span></span> <span data-ttu-id="24995-136">Výchozí obor názvů správce pro <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s již definuje předponu pro obor názvů SOAP 1.2, /s12, který můžete použít.</span><span class="sxs-lookup"><span data-stu-id="24995-136">The default namespace manager for <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s already defines a prefix for the SOAP 1.2 namespace, /s12, which can be used.</span></span> <span data-ttu-id="24995-137">Výchozí obor názvů Správce však nemá vlastní obor názvů, který klient používá k definování skutečné hodnoty hlavičky, aby tuto předponu musí být definovaný.</span><span class="sxs-lookup"><span data-stu-id="24995-137">However, the default namespace manager does not have the custom namespace that the client uses to define the actual header value, so that prefix must be defined.</span></span> <span data-ttu-id="24995-138">Všechny zprávy, které se zobrazí s touto hlavičkou odpovídat tomuto filtru.</span><span class="sxs-lookup"><span data-stu-id="24995-138">Any message that shows up with this header matches this filter.</span></span>  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 <span data-ttu-id="24995-139">Je druhý filtr <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, který odpovídá jakékoli zprávy, který uživateli přišel na `calculatorEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="24995-139">The second filter is an <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, which matches any message that was received on the `calculatorEndpoint`.</span></span> <span data-ttu-id="24995-140">Název koncového bodu je definován, když je vytvořen objekt koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="24995-140">The endpoint name is defined when a service endpoint object is created.</span></span>  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 <span data-ttu-id="24995-141">Je třetí filtr <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="24995-141">The third filter is a <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span></span> <span data-ttu-id="24995-142">To odpovídá jakékoli zprávy, která se zobrazila v koncovém bodu s adresou, která odpovídá předponu adresy (nebo přední části), za předpokladu.</span><span class="sxs-lookup"><span data-stu-id="24995-142">This matches any message that showed up on an endpoint with an address that matches the address prefix (or the front portion) provided.</span></span> <span data-ttu-id="24995-143">V tomto příkladu je definována předpona adresy jako "http://localhost/routingservice/router/rounding/".</span><span class="sxs-lookup"><span data-stu-id="24995-143">In this example the address prefix is defined as "http://localhost/routingservice/router/rounding/".</span></span> <span data-ttu-id="24995-144">To znamená, že příchozí zprávy, které jsou určeny k "http://localhost/routingservice/router/rounding/\*" odpovídajících tomuto filtru.</span><span class="sxs-lookup"><span data-stu-id="24995-144">This means that any incoming messages that are addressed to "http://localhost/routingservice/router/rounding/\*" are matched by this filter.</span></span> <span data-ttu-id="24995-145">V takovém případě je zprávy, které se zobrazí v koncovém bodě zaokrouhlení kalkulačky, který má na adresu "http://localhost/routingservice/router/rounding/calculator".</span><span class="sxs-lookup"><span data-stu-id="24995-145">In this case, it is messages that show up on the Rounding Calculator endpoint, which has the address of "http://localhost/routingservice/router/rounding/calculator".</span></span>  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 <span data-ttu-id="24995-146">Poslední dva filtry zpráv jsou vlastní <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span><span class="sxs-lookup"><span data-stu-id="24995-146">The last two message filters are custom <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span></span> <span data-ttu-id="24995-147">V tomto příkladu se používá filtr zpráv "RoundRobin".</span><span class="sxs-lookup"><span data-stu-id="24995-147">In this example, a "RoundRobin" message filter is used.</span></span> <span data-ttu-id="24995-148">Tomuto filtru zprávy se vytvoří v zadané RoutingService\RoundRobinMessageFilter.cs souboru.</span><span class="sxs-lookup"><span data-stu-id="24995-148">This message filter is created in the provided RoutingService\RoundRobinMessageFilter.cs file.</span></span> <span data-ttu-id="24995-149">Tyto filtry, pokud je nastavena na stejnou skupinu střídavě vytváření sestav, které musí odpovídat zprávy a že tomu tak není, tak, aby pouze jeden z nich odpovídá `true` najednou.</span><span class="sxs-lookup"><span data-stu-id="24995-149">These filters, when set to the same group, alternate between reporting that they match the message and that they do not, such that only one of them responds `true` at a time.</span></span>  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 <span data-ttu-id="24995-150">Potom všechny tyto zprávy jsou přidány do <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span><span class="sxs-lookup"><span data-stu-id="24995-150">Next, all of those messages are added to a <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span></span> <span data-ttu-id="24995-151">Přitom priority jsou určeny k ovlivnění pořadí, ve kterém tabulky filtru zprávy spustí filtry.</span><span class="sxs-lookup"><span data-stu-id="24995-151">In doing so, priorities are specified to influence the order in which the message filter table executes the filters.</span></span> <span data-ttu-id="24995-152">Vyšší je priorita, tím dříve filtru je spuštěn; Čím nižší prioritu, pozdější spuštění filtru.</span><span class="sxs-lookup"><span data-stu-id="24995-152">The higher the priority, the sooner the filter is executed; the lower the priority, the later a filter is executed.</span></span> <span data-ttu-id="24995-153">Proto filtr s prioritou 2 spouští před filtrem s prioritou 1.</span><span class="sxs-lookup"><span data-stu-id="24995-153">Thus a filter at priority 2 runs before a filter at priority 1.</span></span> <span data-ttu-id="24995-154">Výchozí úroveň priority, pokud není zadaný žádný je 0.</span><span class="sxs-lookup"><span data-stu-id="24995-154">The default priority level if none is specified is 0.</span></span> <span data-ttu-id="24995-155">Tabulka Filtr zpráv spustí všechny filtry na úrovni uvedenou prioritou daný před přechodem na další úroveň nejnižší prioritu.</span><span class="sxs-lookup"><span data-stu-id="24995-155">A message filter table executes all of the filters at a given priority level before moving to the next lowest priority level.</span></span> <span data-ttu-id="24995-156">Pokud je nalezena shoda s konkrétní prioritou, pak tabulky filtru zprávy nepokračuje pokusu o nalezení shody další nižší prioritou.</span><span class="sxs-lookup"><span data-stu-id="24995-156">If a match is found at a particular priority, then the message filter table does not continue trying to find matches at the next lower priority.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24995-157">Přestože tento příklad ukazuje způsob použití priority filtru zpráv, obecně je výkonnější a lepší návrh na návrhu a konfigurace filtry tak, aby nevyžadují stanovení priority správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="24995-157">While this example shows how to use message filter priorities, in general it is more performant and better design to design and configure your filters such that they do not require prioritization to function correctly.</span></span>  
  
 <span data-ttu-id="24995-158">Filtr XPath je první filtr, aby se přidají a jeho priorita nastavena na 2.</span><span class="sxs-lookup"><span data-stu-id="24995-158">The first filter to be added is the XPath filter and its priority is set to 2.</span></span> <span data-ttu-id="24995-159">Toto je první filtr zpráv, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="24995-159">This is the first message filter that executes.</span></span> <span data-ttu-id="24995-160">Pokud najde vlastní hlavičky, bez ohledu na to, co by být výsledky další filtry, zpráva se směruje do koncového bodu zaokrouhlení kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="24995-160">If it finds the custom header, regardless of what the results of the other filters would be, the message is routed to the Rounding Calculator endpoint.</span></span>  
  
 <span data-ttu-id="24995-161">S prioritou 1 jsou přidány dva filtry.</span><span class="sxs-lookup"><span data-stu-id="24995-161">At priority 1, two filters are added.</span></span> <span data-ttu-id="24995-162">Znovu tyto spustí jenom v případě filtr XPath s prioritou 2 neodpovídá zprávu.</span><span class="sxs-lookup"><span data-stu-id="24995-162">Again, these only run if the XPath filter at priority 2 does not match the message.</span></span> <span data-ttu-id="24995-163">Zobrazit tyto dva filtry k určení, kde byl vyřešen zprávy, když jsme si ukázali, a dvěma různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="24995-163">These two filters show two different ways to determine where the message was addressed when it showed up.</span></span> <span data-ttu-id="24995-164">Protože dva filtry efektivně zkontrolujte, zda byla zpráva doručena dva koncové body, bylo možné spouštět na stejné úrovni priority protože ne obě možnosti současně vrátit `true` ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="24995-164">Because the two filters effectively check to see whether the message arrived at one of the two endpoints, they can be run at the same priority level because they do not both return `true` at the same time.</span></span>  
  
 <span data-ttu-id="24995-165">A konečně s prioritou 0 (nejnižší prioritu), spusťte RoundRobin zprávy filtry.</span><span class="sxs-lookup"><span data-stu-id="24995-165">Finally, at Priority 0 (the lowest priority) run the RoundRobin message filters.</span></span> <span data-ttu-id="24995-166">Protože jsou nakonfigurované filtry se stejným názvem skupiny, pouze jeden z nich odpovídá najednou.</span><span class="sxs-lookup"><span data-stu-id="24995-166">Because the filters are configured with the same group name, only one of them matches at a time.</span></span> <span data-ttu-id="24995-167">Protože byl směrovány všechny zprávy s vlastní hlavičky, všechny ty řešit ke konkrétním koncovým bodům virtualizované, zprávy zpracovává filtry RoundRobin zpráv jsou jen zprávy, které byly určena výchozí koncový bod směrovače bez vlastní záhlaví.</span><span class="sxs-lookup"><span data-stu-id="24995-167">Because all messages with the custom header have been routed and all those addressed to the specific virtualized endpoints, messages handled by the RoundRobin message filters are only messages that were addressed to the default router endpoint without the custom header.</span></span> <span data-ttu-id="24995-168">Protože tyto zprávy se přepnout na zprávu pro každé volání, polovinu operací přejděte ke koncovému bodu regulární kalkulačky a ta druhá půlka přejděte ke koncovému bodu zaokrouhlení kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="24995-168">Because these messages switch on a message for each call, half of the operations go to the Regular Calculator endpoint and the other half go to the Rounding Calculator endpoint.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="24995-169">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="24995-169">To use this sample</span></span>  
  
1.  <span data-ttu-id="24995-170">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete AdvancedFilters.sln.</span><span class="sxs-lookup"><span data-stu-id="24995-170">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedFilters.sln.</span></span>  
  
2.  <span data-ttu-id="24995-171">Chcete-li otevřít **Průzkumníku řešení**vyberte **Průzkumníku řešení** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="24995-171">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="24995-172">V sadě Visual Studio stiskněte klávesu F5 nebo CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="24995-172">Press F5 or CTRL+SHIFT+B in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="24995-173">Pokud chcete automaticky spouštět nezbytné projektů při stisknutí klávesy F5, klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="24995-173">If you would like to auto-launch the necessary projects when you press F5, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="24995-174">Vyberte **spouštěný projekt** pod uzlem **společné vlastnosti** v levém podokně.</span><span class="sxs-lookup"><span data-stu-id="24995-174">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="24995-175">Vyberte **více projektů po spuštění** přepínač a nastavte všechny projekty, které mají mít **Start** akce.</span><span class="sxs-lookup"><span data-stu-id="24995-175">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="24995-176">Pokud při vytváření projektu pomocí kombinace kláves CTRL + SHIFT + B, je nutné spustit v následujících aplikacích:</span><span class="sxs-lookup"><span data-stu-id="24995-176">If you build the project with CTRL+SHIFT+B, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="24995-177">Kalkulačka klienta (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="24995-177">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="24995-178">Kalkulačka služby (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="24995-178">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="24995-179">Směrovací služba kalkulačky (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="24995-179">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="24995-180">Službu RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="24995-180">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="24995-181">V okně konzoly klienta Kalkulačka stisknutím klávesy ENTER klienta.</span><span class="sxs-lookup"><span data-stu-id="24995-181">In the console window of the Calculator client, press ENTER to start the client.</span></span> <span data-ttu-id="24995-182">Klient vrátí seznam hodnot cílové koncové body lze vybírat.</span><span class="sxs-lookup"><span data-stu-id="24995-182">The client returns a list of destination endpoints to choose from.</span></span>  
  
5.  <span data-ttu-id="24995-183">Zvolte cílový koncový bod tak, že zadáte jeho odpovídající písmeno a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="24995-183">Choose a destination endpoint by typing its corresponding letter and press ENTER.</span></span>  
  
6.  <span data-ttu-id="24995-184">V dalším kroku klienta vás zeptá, zda chcete přidat vlastní hlavičku.</span><span class="sxs-lookup"><span data-stu-id="24995-184">Next, the client asks you if you want to add a custom header.</span></span> <span data-ttu-id="24995-185">Stiskněte klávesu A Ano nebo Ne, N stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="24995-185">Press Y for Yes or N for No, then press ENTER.</span></span>  
  
7.  <span data-ttu-id="24995-186">V závislosti na výběrech, které jste provedli měli byste vidět jiné výstupy.</span><span class="sxs-lookup"><span data-stu-id="24995-186">Depending on the selections you made, you should see different outputs.</span></span>  
  
    1.  <span data-ttu-id="24995-187">Zde je, že výstup vrátí, pokud jste přidali vlastní hlavičky zprávy.</span><span class="sxs-lookup"><span data-stu-id="24995-187">The following is the output returned if you added a custom header to the messages.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="24995-188">Zde je, že výstup vrátí, pokud jste zvolili koncový bod zaokrouhlení Kalkulačka bez vlastní hlavičku.</span><span class="sxs-lookup"><span data-stu-id="24995-188">The following is the output returned if you chose the Rounding Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  <span data-ttu-id="24995-189">Zde je, že výstup vrátí, pokud jste zvolili koncový bod regulární Kalkulačka bez vlastní hlavičku.</span><span class="sxs-lookup"><span data-stu-id="24995-189">The following is the output returned if you chose the Regular Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  <span data-ttu-id="24995-190">Zde je, že výstup vrátí, pokud jste zvolili směrovač výchozí koncový bod bez vlastní hlavičku.</span><span class="sxs-lookup"><span data-stu-id="24995-190">The following is the output returned if you chose the Default Router endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  <span data-ttu-id="24995-191">Kalkulačka služba a služba zaokrouhlení Kalkulačka také vytiskne protokolu operací vyvolat a jejich odpovídajících konzoly windows.</span><span class="sxs-lookup"><span data-stu-id="24995-191">The Calculator Service and the Rounding Calculator Service also prints out a log of the operations invoked to their respective console windows.</span></span>  
  
9. <span data-ttu-id="24995-192">V okně konzoly klienta zadejte `quit` a stisknutím klávesy ENTER ukončete.</span><span class="sxs-lookup"><span data-stu-id="24995-192">In the client console window, type `quit` and press ENTER to exit.</span></span>  
  
10. <span data-ttu-id="24995-193">Stisknutím klávesy ENTER v oknech konzoly služby k ukončení služby.</span><span class="sxs-lookup"><span data-stu-id="24995-193">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="24995-194">Konfigurovat pomocí kódu nebo souboru App.config</span><span class="sxs-lookup"><span data-stu-id="24995-194">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="24995-195">Ukázka lodí umožňují definovat chování ve směrovači použít soubor App.config.</span><span class="sxs-lookup"><span data-stu-id="24995-195">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="24995-196">Můžete také změnit název souboru RoutingService\App.config na jiný tak, aby nebyl rozpoznán a zrušte komentář u volání metod, které `ConfigureRouterViaCode()` v RoutingService\routing.cs.</span><span class="sxs-lookup"><span data-stu-id="24995-196">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and uncomment the method call to `ConfigureRouterViaCode()` in RoutingService\routing.cs.</span></span> <span data-ttu-id="24995-197">Některé z metod má za následek stejné chování směrovače.</span><span class="sxs-lookup"><span data-stu-id="24995-197">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="24995-198">Scénář</span><span class="sxs-lookup"><span data-stu-id="24995-198">Scenario</span></span>  
 <span data-ttu-id="24995-199">Tato ukázka předvádí, směrovač fungujícího jako směrovač založené na obsahu umožňuje více typů nebo implementaci služeb zpřístupní prostřednictvím jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="24995-199">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="24995-200">Reálné scénáře</span><span class="sxs-lookup"><span data-stu-id="24995-200">Real World Scenario</span></span>  
 <span data-ttu-id="24995-201">Contoso chce, aby se k virtualizaci všech svých služeb vystavit pouze jeden koncový bod veřejně přes který nabízejí přístup k více různých typů služeb.</span><span class="sxs-lookup"><span data-stu-id="24995-201">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="24995-202">V tomto případě využívat Služba směrování založené na obsahu směrování schopnosti určit, které by měla být odeslána příchozí požadavky.</span><span class="sxs-lookup"><span data-stu-id="24995-202">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24995-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="24995-203">See Also</span></span>  
 [<span data-ttu-id="24995-204">Hostování AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="24995-204">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
