---
title: "Rozšířené filtry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 988c41bb691d27e819710bbc2cd48bc1c844e7c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="advanced-filters"></a><span data-ttu-id="ff260-102">Rozšířené filtry</span><span class="sxs-lookup"><span data-stu-id="ff260-102">Advanced Filters</span></span>
<span data-ttu-id="ff260-103">Tento příklad znázorňuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] směrování služby.</span><span class="sxs-lookup"><span data-stu-id="ff260-103">This sample demonstrates a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="ff260-104">Služba směrování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komponenty, která usnadňuje do aplikace zahrnout směrovač podle obsahu.</span><span class="sxs-lookup"><span data-stu-id="ff260-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="ff260-105">Tato ukázka přizpůsobuje standardní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázka kalkulačku komunikovat pomocí služby směrování.</span><span class="sxs-lookup"><span data-stu-id="ff260-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator sample to communicate using the routing service.</span></span> <span data-ttu-id="ff260-106">Tento příklad ukazuje, jak definovat na základě obsahu směrování logiku prostřednictvím filtry zpráv a zpráva filtru tabulky.</span><span class="sxs-lookup"><span data-stu-id="ff260-106">This sample shows how to define content-based routing logic through the use of message filters and message filter tables.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff260-107">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="ff260-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ff260-108">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ff260-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ff260-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ff260-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff260-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ff260-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a><span data-ttu-id="ff260-111">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ff260-111">Sample Details</span></span>  
 <span data-ttu-id="ff260-112">V následující tabulce jsou filtry zpráv, které jsou přidány do tabulky filtru zpráv služby směrování.</span><span class="sxs-lookup"><span data-stu-id="ff260-112">The following table shows the message filters that are added to the message filter table of the routing service.</span></span>  
  
|<span data-ttu-id="ff260-113">Filtr</span><span class="sxs-lookup"><span data-stu-id="ff260-113">Filter</span></span>|<span data-ttu-id="ff260-114">Pravidlo</span><span class="sxs-lookup"><span data-stu-id="ff260-114">Rule</span></span>|<span data-ttu-id="ff260-115">Priorita</span><span class="sxs-lookup"><span data-stu-id="ff260-115">Priority</span></span>|  
|------------|----------|--------------|  
|<span data-ttu-id="ff260-116">Pokud (mají záhlaví)</span><span class="sxs-lookup"><span data-stu-id="ff260-116">If (has header)</span></span>|<span data-ttu-id="ff260-117">Zaokrouhlení</span><span class="sxs-lookup"><span data-stu-id="ff260-117">Rounding</span></span>|<span data-ttu-id="ff260-118">2</span><span class="sxs-lookup"><span data-stu-id="ff260-118">2</span></span>|  
|<span data-ttu-id="ff260-119">Pokud (vám ukázal, na Ep2)</span><span class="sxs-lookup"><span data-stu-id="ff260-119">If (showed up on Ep2)</span></span>|<span data-ttu-id="ff260-120">Regulární</span><span class="sxs-lookup"><span data-stu-id="ff260-120">Regular</span></span>|<span data-ttu-id="ff260-121">1</span><span class="sxs-lookup"><span data-stu-id="ff260-121">1</span></span>|  
|<span data-ttu-id="ff260-122">Pokud (vám ukázal, se Adresa2)</span><span class="sxs-lookup"><span data-stu-id="ff260-122">If (showed up with Address2)</span></span>|<span data-ttu-id="ff260-123">Zaokrouhlení</span><span class="sxs-lookup"><span data-stu-id="ff260-123">Rounding</span></span>|<span data-ttu-id="ff260-124">1</span><span class="sxs-lookup"><span data-stu-id="ff260-124">1</span></span>|  
|<span data-ttu-id="ff260-125">Pokud (RoundRobin1)</span><span class="sxs-lookup"><span data-stu-id="ff260-125">If (RoundRobin1)</span></span>|<span data-ttu-id="ff260-126">Regulární</span><span class="sxs-lookup"><span data-stu-id="ff260-126">Regular</span></span>|<span data-ttu-id="ff260-127">0</span><span class="sxs-lookup"><span data-stu-id="ff260-127">0</span></span>|  
|<span data-ttu-id="ff260-128">Pokud (RoundRobin2)</span><span class="sxs-lookup"><span data-stu-id="ff260-128">If (RoundRobin2)</span></span>|<span data-ttu-id="ff260-129">Zaokrouhlení</span><span class="sxs-lookup"><span data-stu-id="ff260-129">Rounding</span></span>|<span data-ttu-id="ff260-130">0</span><span class="sxs-lookup"><span data-stu-id="ff260-130">0</span></span>|  
  
 <span data-ttu-id="ff260-131">Filtry zpráv a zpráva filtru tabulky lze vytvořit a konfigurovat pomocí kódu nebo v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ff260-131">The message filters and message filter tables can be created and configured either through code or in the application configuration file.</span></span> <span data-ttu-id="ff260-132">Tato ukázka můžete najít filtry zpráv a zpráva filtru tabulky definované prostřednictvím kódu v souboru RoutingService\routing.cs nebo definována v konfiguračním souboru aplikace v souboru RoutingService\App.config.</span><span class="sxs-lookup"><span data-stu-id="ff260-132">For this sample, you can find the message filters and message filter tables defined through code in the RoutingService\routing.cs file, or defined in the application configuration file in the RoutingService\App.config file.</span></span> <span data-ttu-id="ff260-133">Následující odstavce popisují, jak vytváří filtry zpráv a zpráva filtru tabulky pro tato ukázka prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="ff260-133">The following paragraphs describe how the message filters and message filter tables are created for this sample through code.</span></span>  
  
 <span data-ttu-id="ff260-134">První, <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> hledá vlastní hlavičky.</span><span class="sxs-lookup"><span data-stu-id="ff260-134">First, an <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> looks for the custom header.</span></span> <span data-ttu-id="ff260-135">Všimněte si, že <xref:System.ServiceModel.WSHttpBinding> výsledků ve verzi obálky pomocí protokolu SOAP 1.2, takže příkaz jazyka XPath je definována pro používání oboru názvů SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="ff260-135">Note that <xref:System.ServiceModel.WSHttpBinding> results in an envelope version using SOAP 1.2, so the XPath statement is defined to use the SOAP 1.2 namespace.</span></span> <span data-ttu-id="ff260-136">Správce výchozí obor názvů pro <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s již definuje předponu pro obor názvů SOAP 1.2, /s12, který může být použit.</span><span class="sxs-lookup"><span data-stu-id="ff260-136">The default namespace manager for <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s already defines a prefix for the SOAP 1.2 namespace, /s12, which can be used.</span></span> <span data-ttu-id="ff260-137">Výchozí obor názvů správce nemá vlastní obor názvů, který klient používá k definování skutečné hodnoty hlavičky, takže tuto předponu musí být definován.</span><span class="sxs-lookup"><span data-stu-id="ff260-137">However, the default namespace manager does not have the custom namespace that the client uses to define the actual header value, so that prefix must be defined.</span></span> <span data-ttu-id="ff260-138">Všechny zprávy, které se zobrazí s touto hlavičkou odpovídat tomuto filtru.</span><span class="sxs-lookup"><span data-stu-id="ff260-138">Any message that shows up with this header matches this filter.</span></span>  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 <span data-ttu-id="ff260-139">Druhý filtr je <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, který odpovídá jakékoli zprávy, která byla obdržena ve `calculatorEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="ff260-139">The second filter is an <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, which matches any message that was received on the `calculatorEndpoint`.</span></span> <span data-ttu-id="ff260-140">Název koncového bodu je definován, když je vytvořen objekt koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="ff260-140">The endpoint name is defined when a service endpoint object is created.</span></span>  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 <span data-ttu-id="ff260-141">Je třetí filtr <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="ff260-141">The third filter is a <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span></span> <span data-ttu-id="ff260-142">To odpovídá všechny zprávy, které vám ukázal, na koncový bod s adresou, která odpovídá předpona adresy (nebo části front) zadaný.</span><span class="sxs-lookup"><span data-stu-id="ff260-142">This matches any message that showed up on an endpoint with an address that matches the address prefix (or the front portion) provided.</span></span> <span data-ttu-id="ff260-143">V tomto příkladu je předpona adresy definovaný jako "http://localhost/routingservice/router/rounding/".</span><span class="sxs-lookup"><span data-stu-id="ff260-143">In this example the address prefix is defined as "http://localhost/routingservice/router/rounding/".</span></span> <span data-ttu-id="ff260-144">To znamená, že tento filtr se splní všechny příchozí zprávy, které jsou určeny k "http://localhost/routingservice/router/rounding/ *".</span><span class="sxs-lookup"><span data-stu-id="ff260-144">This means that any incoming messages that are addressed to "http://localhost/routingservice/router/rounding/*" are matched by this filter.</span></span> <span data-ttu-id="ff260-145">V takovém případě je zprávy, které se zobrazí v koncovém bodě zaokrouhlení kalkulačky, který má na adresu "http://localhost/routingservice/router/rounding/calculator".</span><span class="sxs-lookup"><span data-stu-id="ff260-145">In this case, it is messages that show up on the Rounding Calculator endpoint, which has the address of "http://localhost/routingservice/router/rounding/calculator".</span></span>  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 <span data-ttu-id="ff260-146">Poslední dva filtry zpráv jsou vlastní <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span><span class="sxs-lookup"><span data-stu-id="ff260-146">The last two message filters are custom <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span></span> <span data-ttu-id="ff260-147">V tomto příkladu se používá filtr zpráv "RoundRobin".</span><span class="sxs-lookup"><span data-stu-id="ff260-147">In this example, a "RoundRobin" message filter is used.</span></span> <span data-ttu-id="ff260-148">Tento filtr zpráv se vytvoří v zadaný soubor RoutingService\RoundRobinMessageFilter.cs.</span><span class="sxs-lookup"><span data-stu-id="ff260-148">This message filter is created in the provided RoutingService\RoundRobinMessageFilter.cs file.</span></span> <span data-ttu-id="ff260-149">Tyto filtry, pokud je nastavena na stejnou skupinu alternativní mezi sestav, aby odpovídaly zprávy a, že nechcete, tak, aby pouze jeden z nich odpovídá `true` najednou.</span><span class="sxs-lookup"><span data-stu-id="ff260-149">These filters, when set to the same group, alternate between reporting that they match the message and that they do not, such that only one of them responds `true` at a time.</span></span>  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 <span data-ttu-id="ff260-150">Potom všechny tyto zprávy jsou přidány do <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span><span class="sxs-lookup"><span data-stu-id="ff260-150">Next, all of those messages are added to a <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span></span> <span data-ttu-id="ff260-151">Při tom priority zadávají k ovlivnění pořadí, ve kterém tabulku filtru zpráv provede filtry.</span><span class="sxs-lookup"><span data-stu-id="ff260-151">In doing so, priorities are specified to influence the order in which the message filter table executes the filters.</span></span> <span data-ttu-id="ff260-152">Tím vyšší je priorita, tím dříve filtr je provedeno; nižší prioritu, novější spouští filtr.</span><span class="sxs-lookup"><span data-stu-id="ff260-152">The higher the priority, the sooner the filter is executed; the lower the priority, the later a filter is executed.</span></span> <span data-ttu-id="ff260-153">Proto filtr důležitostí 2 spouští před filtrem v priority 1.</span><span class="sxs-lookup"><span data-stu-id="ff260-153">Thus a filter at priority 2 runs before a filter at priority 1.</span></span> <span data-ttu-id="ff260-154">Výchozí úroveň priority, pokud není zadaný žádný je 0.</span><span class="sxs-lookup"><span data-stu-id="ff260-154">The default priority level if none is specified is 0.</span></span> <span data-ttu-id="ff260-155">Tabulku filtru zpráv zpracuje všechny filtry na úrovni Zadaná priorita před přesunutím do další nejnižší úroveň priority.</span><span class="sxs-lookup"><span data-stu-id="ff260-155">A message filter table executes all of the filters at a given priority level before moving to the next lowest priority level.</span></span> <span data-ttu-id="ff260-156">Pokud je nalezena shoda s konkrétní prioritou, pak tabulku filtru zpráv nebude dále pokusu o vyhledání shody další nižší prioritou.</span><span class="sxs-lookup"><span data-stu-id="ff260-156">If a match is found at a particular priority, then the message filter table does not continue trying to find matches at the next lower priority.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff260-157">Když tento příklad ukazuje způsob použití priority filtru zpráv, obecně je další původce a lepší návrhu k návrhu a konfigurovat filtry tak, aby nevyžadují stanovení priorit, aby správně fungoval.</span><span class="sxs-lookup"><span data-stu-id="ff260-157">While this example shows how to use message filter priorities, in general it is more performant and better design to design and configure your filters such that they do not require prioritization to function correctly.</span></span>  
  
 <span data-ttu-id="ff260-158">První filtr, který se má přidat je filtr XPath a jeho priorita je nastavena na hodnotu 2.</span><span class="sxs-lookup"><span data-stu-id="ff260-158">The first filter to be added is the XPath filter and its priority is set to 2.</span></span> <span data-ttu-id="ff260-159">Toto je první filtr zpráv, které provádí.</span><span class="sxs-lookup"><span data-stu-id="ff260-159">This is the first message filter that executes.</span></span> <span data-ttu-id="ff260-160">Pokud najde vlastní hlavičky, bez ohledu na to, co by bylo výsledky ostatní filtry, zpráva se směruje na koncový bod zaokrouhlení kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="ff260-160">If it finds the custom header, regardless of what the results of the other filters would be, the message is routed to the Rounding Calculator endpoint.</span></span>  
  
 <span data-ttu-id="ff260-161">Priorita 1 přidá dva filtry.</span><span class="sxs-lookup"><span data-stu-id="ff260-161">At priority 1, two filters are added.</span></span> <span data-ttu-id="ff260-162">Opakujte tyto spustí jenom v případě filtr XPath důležitostí 2 neodpovídá zprávy.</span><span class="sxs-lookup"><span data-stu-id="ff260-162">Again, these only run if the XPath filter at priority 2 does not match the message.</span></span> <span data-ttu-id="ff260-163">Dva různé způsoby, jak určit, kdy byla zpráva řešit při jeho vám ukázal, se zobrazí tyto dva filtry.</span><span class="sxs-lookup"><span data-stu-id="ff260-163">These two filters show two different ways to determine where the message was addressed when it showed up.</span></span> <span data-ttu-id="ff260-164">Vzhledem k tomu, že dva filtry efektivně zkontrolujte, zda zpráva dorazila po uplynutí v některém z dva koncové body, jejich spuštěním na stejné úrovni s prioritou protože udělají ne pomocí obou vrátit `true` ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="ff260-164">Because the two filters effectively check to see whether the message arrived at one of the two endpoints, they can be run at the same priority level because they do not both return `true` at the same time.</span></span>  
  
 <span data-ttu-id="ff260-165">Nakonec s prioritou 0 (nejnižší priorita) spustit RoundRobin zpráva filtry.</span><span class="sxs-lookup"><span data-stu-id="ff260-165">Finally, at Priority 0 (the lowest priority) run the RoundRobin message filters.</span></span> <span data-ttu-id="ff260-166">Protože filtry jsou nakonfigurované se stejným názvem skupiny, pouze jedna z nich odpovídá najednou.</span><span class="sxs-lookup"><span data-stu-id="ff260-166">Because the filters are configured with the same group name, only one of them matches at a time.</span></span> <span data-ttu-id="ff260-167">Protože všechny zprávy s vlastní hlavička již byla směrován a všechny ty řešit konkrétní virtualizované koncových bodů, jsou zprávy zpracovávaných filtry zpráv RoundRobin jen zprávy, které byla provedena na výchozí koncový bod směrovač bez vlastní hlavička.</span><span class="sxs-lookup"><span data-stu-id="ff260-167">Because all messages with the custom header have been routed and all those addressed to the specific virtualized endpoints, messages handled by the RoundRobin message filters are only messages that were addressed to the default router endpoint without the custom header.</span></span> <span data-ttu-id="ff260-168">Protože tyto zprávy přepínač na zprávu pro každé volání, polovinu operace přejděte ke koncovému bodu regulární kalkulačky a druhá polovina přejděte ke koncovému bodu zaokrouhlení kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="ff260-168">Because these messages switch on a message for each call, half of the operations go to the Regular Calculator endpoint and the other half go to the Rounding Calculator endpoint.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="ff260-169">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="ff260-169">To use this sample</span></span>  
  
1.  <span data-ttu-id="ff260-170">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete AdvancedFilters.sln.</span><span class="sxs-lookup"><span data-stu-id="ff260-170">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedFilters.sln.</span></span>  
  
2.  <span data-ttu-id="ff260-171">Chcete-li otevřít **Průzkumníku řešení**, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ff260-171">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="ff260-172">Stiskněte klávesu F5 nebo CTRL + SHIFT + B v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff260-172">Press F5 or CTRL+SHIFT+B in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="ff260-173">Pokud chcete automaticky spouštěné projekty potřebné po stisknutí klávesy F5, klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ff260-173">If you would like to auto-launch the necessary projects when you press F5, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="ff260-174">Vyberte **spouštěný projekt** pod uzlem **společných vlastností** v levém podokně.</span><span class="sxs-lookup"><span data-stu-id="ff260-174">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="ff260-175">Vyberte **více projektů po spuštění** přepínač a nastavte všechny projekty, které chcete mít **spustit** akce.</span><span class="sxs-lookup"><span data-stu-id="ff260-175">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="ff260-176">Pokud vytvoříte projekt pomocí kombinace kláves CTRL + SHIFT + B, je nutné spustit následující aplikace:</span><span class="sxs-lookup"><span data-stu-id="ff260-176">If you build the project with CTRL+SHIFT+B, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="ff260-177">Klient kalkulačky (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="ff260-177">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="ff260-178">Službu kalkulačky (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="ff260-178">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="ff260-179">Směrovací služba provádí kalkulačky (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="ff260-179">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="ff260-180">RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="ff260-180">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="ff260-181">V okně konzoly klienta kalkulačky stisknutím klávesy ENTER spusťte službu klienta.</span><span class="sxs-lookup"><span data-stu-id="ff260-181">In the console window of the Calculator client, press ENTER to start the client.</span></span> <span data-ttu-id="ff260-182">Klient vrátí seznam koncových bodů cílové lze vybírat.</span><span class="sxs-lookup"><span data-stu-id="ff260-182">The client returns a list of destination endpoints to choose from.</span></span>  
  
5.  <span data-ttu-id="ff260-183">Zvolte cílový koncový bod zadáním jeho odpovídající písmeno a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="ff260-183">Choose a destination endpoint by typing its corresponding letter and press ENTER.</span></span>  
  
6.  <span data-ttu-id="ff260-184">V dalším kroku klienta zeptá, pokud chcete přidat vlastní hlavičku.</span><span class="sxs-lookup"><span data-stu-id="ff260-184">Next, the client asks you if you want to add a custom header.</span></span> <span data-ttu-id="ff260-185">Stiskněte klávesu Y Ano nebo N pro žádný, stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="ff260-185">Press Y for Yes or N for No, then press ENTER.</span></span>  
  
7.  <span data-ttu-id="ff260-186">V závislosti na vybrané možnosti, které jste nastavili měli byste vidět jiné výstupy.</span><span class="sxs-lookup"><span data-stu-id="ff260-186">Depending on the selections you made, you should see different outputs.</span></span>  
  
    1.  <span data-ttu-id="ff260-187">Toto je výstup vrácena, pokud jste přidali vlastní záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="ff260-187">The following is the output returned if you added a custom header to the messages.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="ff260-188">Toto je výstup vrácena, pokud jste si zvolili koncový bod zaokrouhlení kalkulačky bez vlastní hlavičky.</span><span class="sxs-lookup"><span data-stu-id="ff260-188">The following is the output returned if you chose the Rounding Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  <span data-ttu-id="ff260-189">Toto je výstup vrácena, pokud jste si zvolili koncový bod regulární kalkulačky bez vlastní hlavičky.</span><span class="sxs-lookup"><span data-stu-id="ff260-189">The following is the output returned if you chose the Regular Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  <span data-ttu-id="ff260-190">Toto je výstup vrácena, pokud jste si zvolili směrovače výchozí koncový bod bez vlastní hlavičky.</span><span class="sxs-lookup"><span data-stu-id="ff260-190">The following is the output returned if you chose the Default Router endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  <span data-ttu-id="ff260-191">Službu kalkulačky a službu kalkulačky zaokrouhlení vytiskne také protokolu operací vyvolat do svých příslušných konzoly windows.</span><span class="sxs-lookup"><span data-stu-id="ff260-191">The Calculator Service and the Rounding Calculator Service also prints out a log of the operations invoked to their respective console windows.</span></span>  
  
9. <span data-ttu-id="ff260-192">V okně konzoly klienta zadejte `quit` a stiskněte klávesu ENTER ukončíte.</span><span class="sxs-lookup"><span data-stu-id="ff260-192">In the client console window, type `quit` and press ENTER to exit.</span></span>  
  
10. <span data-ttu-id="ff260-193">Stisknutím klávesy ENTER v oknech konzoly služby ukončení služby.</span><span class="sxs-lookup"><span data-stu-id="ff260-193">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="ff260-194">Konfigurovat pomocí kódu nebo App.config</span><span class="sxs-lookup"><span data-stu-id="ff260-194">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="ff260-195">Ukázka lodě, umožňují použít soubor App.config k definování chování směrovače.</span><span class="sxs-lookup"><span data-stu-id="ff260-195">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="ff260-196">Můžete taky změnit název souboru RoutingService\App.config na jinou tak, aby nebyla rozpoznána a zrušte komentář u volání metody `ConfigureRouterViaCode()` v RoutingService\routing.cs.</span><span class="sxs-lookup"><span data-stu-id="ff260-196">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and uncomment the method call to `ConfigureRouterViaCode()` in RoutingService\routing.cs.</span></span> <span data-ttu-id="ff260-197">Buď metoda výsledkem stejné chování z směrovači.</span><span class="sxs-lookup"><span data-stu-id="ff260-197">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="ff260-198">Scénář</span><span class="sxs-lookup"><span data-stu-id="ff260-198">Scenario</span></span>  
 <span data-ttu-id="ff260-199">Tento příklad znázorňuje směrovač, který funguje jako směrovač založená na obsahu umožňuje více typů nebo implementace služby mají být exponovány prostřednictvím jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="ff260-199">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="ff260-200">Scénář skutečných</span><span class="sxs-lookup"><span data-stu-id="ff260-200">Real World Scenario</span></span>  
 <span data-ttu-id="ff260-201">Contoso chce k virtualizaci všech svých služeb vystavit pouze jeden koncový bod veřejně přes která nabízejí přístup k několika různých typů služeb.</span><span class="sxs-lookup"><span data-stu-id="ff260-201">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="ff260-202">V takovém případě využívají službu směrování na základě obsahu směrování možnosti k určení, kde by měly být odeslány příchozí požadavky.</span><span class="sxs-lookup"><span data-stu-id="ff260-202">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff260-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff260-203">See Also</span></span>  
 [<span data-ttu-id="ff260-204">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="ff260-204">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
