---
title: "Postupy: Použití filtrů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 94d45537ca3edd5f31f1ed31898857f002312a0b
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-use-filters"></a><span data-ttu-id="5c209-102">Postupy: Použití filtrů</span><span class="sxs-lookup"><span data-stu-id="5c209-102">How To: Use Filters</span></span>
<span data-ttu-id="5c209-103">Toto téma popisuje základní kroky potřebné pro vytvoření konfigurace směrování, která používá více filtrů.</span><span class="sxs-lookup"><span data-stu-id="5c209-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="5c209-104">V tomto příkladu jsou dva implementace služby kalkulačky, regularCalc a roundingCalc směrovány zprávy.</span><span class="sxs-lookup"><span data-stu-id="5c209-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="5c209-105">Obě implementace podporují stejné operace; ale jedna služba zaokrouhlí na nejbližší celé číslo všech výpočtů před vrácením.</span><span class="sxs-lookup"><span data-stu-id="5c209-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="5c209-106">Klientská aplikace musí být schopen označuje, zda chcete použít zaokrouhlení verzi služby; Pokud žádné služby přání zpráva je mezi těmito dvěma službami skupinu s vyrovnáváním zatížení.</span><span class="sxs-lookup"><span data-stu-id="5c209-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="5c209-107">Operace vystavené obě služby jsou:</span><span class="sxs-lookup"><span data-stu-id="5c209-107">The operations exposed by both services are:</span></span>  
  
-   <span data-ttu-id="5c209-108">Přidejte</span><span class="sxs-lookup"><span data-stu-id="5c209-108">Add</span></span>  
  
-   <span data-ttu-id="5c209-109">Odečtena</span><span class="sxs-lookup"><span data-stu-id="5c209-109">Subtract</span></span>  
  
-   <span data-ttu-id="5c209-110">Násobení</span><span class="sxs-lookup"><span data-stu-id="5c209-110">Multiply</span></span>  
  
-   <span data-ttu-id="5c209-111">Dělení</span><span class="sxs-lookup"><span data-stu-id="5c209-111">Divide</span></span>  
  
 <span data-ttu-id="5c209-112">Protože obě služby implementovat stejné operace, nemůžete použít filtr akce, protože akci určenou ve zprávě nesmí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="5c209-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="5c209-113">Místo toho je potřeba udělat další kroky k zajištění, že zprávy jsou směrované na jednotlivé koncové body.</span><span class="sxs-lookup"><span data-stu-id="5c209-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="5c209-114">Určit jedinečné dat</span><span class="sxs-lookup"><span data-stu-id="5c209-114">Determine Unique Data</span></span>  
  
1.  <span data-ttu-id="5c209-115">Protože oba implementace služby zpracování stejné operace a jsou v podstatě stejné než data, která se vracejí, základní data obsažená v zpráv odeslaných z klientské aplikace není dostatečně jedinečný, a umožní vám určit, jak směrovat požadavek.</span><span class="sxs-lookup"><span data-stu-id="5c209-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="5c209-116">Ale pokud klientská aplikace přidá hodnotu jedinečné záhlaví zprávy, potom můžete tuto hodnotu určit, jak by měl směrovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="5c209-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="5c209-117">Například pokud klientská aplikace potřebuje zprávu, která se má zpracovat modulem zaokrouhlení kalkulačky, přidá vlastní hlavičku s použitím následující kód:</span><span class="sxs-lookup"><span data-stu-id="5c209-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="5c209-118">Teď můžete použít filtr XPath kontrola zpráv pro tuto hlavičku a směrování zpráv obsahující hlavičku ke službě roundCalc.</span><span class="sxs-lookup"><span data-stu-id="5c209-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2.  <span data-ttu-id="5c209-119">Kromě toho směrovací služby zpřístupní dva koncové body virtuální služby, které lze použít s EndpointName, EndpointAddress, nebo filtruje PrefixEndpointAddress jednoznačně směrovat příchozí zprávy pro konkrétní kalkulačky implementaci založené na koncový bod do které klientská aplikace odešle požadavek.</span><span class="sxs-lookup"><span data-stu-id="5c209-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="5c209-120">Zadejte koncové body</span><span class="sxs-lookup"><span data-stu-id="5c209-120">Define Endpoints</span></span>  
  
1.  <span data-ttu-id="5c209-121">Při definování koncových bodů použitých službou směrování, nejdřív byste měli zjistit obrazec kanál používaný klienty a služby.</span><span class="sxs-lookup"><span data-stu-id="5c209-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="5c209-122">V tomto scénáři používají cílové služby požadavku a odpovědi vzor, proto <xref:System.ServiceModel.Routing.IRequestReplyRouter> se používá.</span><span class="sxs-lookup"><span data-stu-id="5c209-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="5c209-123">V následujícím příkladu definuje koncové body služby, který je zveřejněný prostřednictvím služby směrování.</span><span class="sxs-lookup"><span data-stu-id="5c209-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     <span data-ttu-id="5c209-124">Pomocí této konfigurace služby směrování zpřístupní tři samostatné koncové body.</span><span class="sxs-lookup"><span data-stu-id="5c209-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="5c209-125">V závislosti na rozhodnutích při spuštění klientské aplikace odešle zprávy do jedné z těchto adres.</span><span class="sxs-lookup"><span data-stu-id="5c209-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="5c209-126">Pro implementaci odpovídající kalkulačky jsou předávány zpráv přicházejících na jednom z koncových bodů služby "virtuální" ("zaokrouhlení/calculator" nebo "regular/calculator").</span><span class="sxs-lookup"><span data-stu-id="5c209-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="5c209-127">Pokud klientská aplikace neodešle žádost o konkrétní koncový bod, je určena zpráva obecné koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5c209-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="5c209-128">Bez ohledu na koncový bod vybrali může klientská aplikace také vybrat možnost zahrnutí vlastní hlavičky k označení, že mají předávat zprávy zaokrouhlení kalkulačky implementace.</span><span class="sxs-lookup"><span data-stu-id="5c209-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2.  <span data-ttu-id="5c209-129">V následujícím příkladu definuje koncové body klienta (cíl), které směrovací služby směrování zpráv do.</span><span class="sxs-lookup"><span data-stu-id="5c209-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     <span data-ttu-id="5c209-130">Tyto koncové body jsou v tabulce filtru slouží k určení cílového koncového bodu, který je zpráva odeslána na při odpovídá konkrétní filtr.</span><span class="sxs-lookup"><span data-stu-id="5c209-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="5c209-131">Zadejte filtry</span><span class="sxs-lookup"><span data-stu-id="5c209-131">Define Filters</span></span>  
  
1.  <span data-ttu-id="5c209-132">Chcete-li směrovat zprávy založené na vlastní hlavičky "RoundingCalculator", který klientská aplikace přidá ke zprávě, definujte filtr, který používá dotaz XPath Pokud chcete zkontrolovat přítomnost tuto hlavičku.</span><span class="sxs-lookup"><span data-stu-id="5c209-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="5c209-133">Vzhledem k tomu, že tuto hlavičku se definuje pomocí vlastní obor názvů, také přidáte obor názvů položku, která definuje vlastní obor názvů předponu "vlastní", který se používá v dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="5c209-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="5c209-134">V následujícím příkladu definuje nezbytné směrování části, obor názvů tabulku a filtr XPath.</span><span class="sxs-lookup"><span data-stu-id="5c209-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"   
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     <span data-ttu-id="5c209-135">To **MessageFilter** hledá RoundingCalculator záhlaví zprávy, která obsahuje hodnotu "zaokrouhlení".</span><span class="sxs-lookup"><span data-stu-id="5c209-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="5c209-136">Tuto hlavičku je nastavená klientem indikující, že zpráva by měla směrované na službu roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="5c209-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5c209-137">Předpona oboru názvů s12 je definována ve výchozím nastavení v tabulce obor názvů a představuje obor názvů "http://www.w3.org/2003/05/soap-envelope".</span><span class="sxs-lookup"><span data-stu-id="5c209-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace "http://www.w3.org/2003/05/soap-envelope".</span></span>  
  
2.  <span data-ttu-id="5c209-138">Je třeba definovat filtry, které vypadají zprávy přijaté na dva virtuální koncové body.</span><span class="sxs-lookup"><span data-stu-id="5c209-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="5c209-139">První virtuální koncový bod je koncový bod "regular/calculator".</span><span class="sxs-lookup"><span data-stu-id="5c209-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="5c209-140">Klient může odesílat požadavky na tento koncový bod k označení, že zpráva by měla směrované na službu regularCalc.</span><span class="sxs-lookup"><span data-stu-id="5c209-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="5c209-141">Definuje filtr, který používá následující konfigurace <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> k určení, pokud zpráva dorazila po uplynutí přes koncový bod s názvem zadaným v fulltextových dat filtru.</span><span class="sxs-lookup"><span data-stu-id="5c209-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="5c209-142">Pokud je koncový bod služby s názvem "calculatorEndpoint" přijme zprávu, tento filtr se vyhodnocuje `true`.</span><span class="sxs-lookup"><span data-stu-id="5c209-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3.  <span data-ttu-id="5c209-143">V dalším kroku definujte filtr, který hledá zprávy odeslané na adresu roundingEndpoint.</span><span class="sxs-lookup"><span data-stu-id="5c209-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="5c209-144">Klient může odesílat požadavky na tento koncový bod k označení, že zpráva by měla směrované na službu roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="5c209-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="5c209-145">Definuje filtr, který používá následující konfigurace <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> k určení, pokud zpráva dorazila po uplynutí na koncovém bodu "zaokrouhlení/calculator".</span><span class="sxs-lookup"><span data-stu-id="5c209-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="5c209-146">Pokud je přijata zpráva na adresu, která začíná "http://localhost/routingservice/router/rounding/", pak tento filtr se vyhodnocuje **true**.</span><span class="sxs-lookup"><span data-stu-id="5c209-146">If a message is received at an address that begins with "http://localhost/routingservice/router/rounding/" then this filter evaluates to **true**.</span></span> <span data-ttu-id="5c209-147">Vzhledem k tomu je základní adresa použitá v této konfiguraci je "http://localhost/routingservice/router" a "zaokrouhlení/calculator" je zadaná adresa roundingEndpoint, úplná adresa použitá pro komunikaci se tento koncový bod je "http://localhost/ routingservice/směrovače nebo zaokrouhlení/calculator", který by odpovídal tento filtr.</span><span class="sxs-lookup"><span data-stu-id="5c209-147">Because the base address used by this configuration is "http://localhost/routingservice/router" and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is "http://localhost/routingservice/router/rounding/calculator", which matches this filter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5c209-148">Filtr PrefixEndpointAddress nevyhodnocuje název hostitele, při provádění shodu, protože je jeden hostitel lze odkazovat pomocí různých názvů hostitelů, které může všechny být platné způsoby odkazů na hostiteli z klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c209-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="5c209-149">Všechny tyto například mohou odkazovat na stejného hostitele:</span><span class="sxs-lookup"><span data-stu-id="5c209-149">For example, all of the following may refer to the same host:</span></span>  
    >   
    >  -   <span data-ttu-id="5c209-150">localhost</span><span class="sxs-lookup"><span data-stu-id="5c209-150">localhost</span></span>  
    > -   <span data-ttu-id="5c209-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="5c209-151">127.0.0.1</span></span>  
    > -   <span data-ttu-id="5c209-152">www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="5c209-152">www.contoso.com</span></span>  
    > -   <span data-ttu-id="5c209-153">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="5c209-153">ContosoWeb01</span></span>  
  
4.  <span data-ttu-id="5c209-154">Poslední filtr musí podporovat směrování zpráv, které přicházejí na obecné koncového bodu bez vlastní hlavičky.</span><span class="sxs-lookup"><span data-stu-id="5c209-154">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="5c209-155">V tomto scénáři by měl mezi službami regularCalc a roundingCalc alternativní zprávy.</span><span class="sxs-lookup"><span data-stu-id="5c209-155">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="5c209-156">Pro podporu "kruhové dotazování" směrování tyto zprávy, použijte vlastní filtr, který umožňuje jednu instanci filtru tak, aby odpovídaly pro každou zprávu zpracovat.</span><span class="sxs-lookup"><span data-stu-id="5c209-156">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="5c209-157">Následující definuje dvě instance RoundRobinMessageFilter, které jsou seskupeny dohromady indikující, že by měl alternativní mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="5c209-157">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     <span data-ttu-id="5c209-158">Za běhu tento typ filtru střídá definovaný filtr instance tohoto typu, které jsou nakonfigurované jako stejnou skupinu do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="5c209-158">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="5c209-159">To způsobí, že zpráv zpracovaných správcem tento vlastní filtr na alternativní mezi vrácení `true` RoundRobinFilter1 a RoundRobinFilter2.</span><span class="sxs-lookup"><span data-stu-id="5c209-159">This causes messages processed by this custom filter to alternate between returning `true` for RoundRobinFilter1 and RoundRobinFilter2.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="5c209-160">Definujte filtr tabulek</span><span class="sxs-lookup"><span data-stu-id="5c209-160">Define Filter Tables</span></span>  
  
1.  <span data-ttu-id="5c209-161">Přidružit filtry s koncovými body konkrétního klienta, je nutné umístit v tabulce filtru.</span><span class="sxs-lookup"><span data-stu-id="5c209-161">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="5c209-162">Tento příklad scénář také používá nastavení priority filtr, který je volitelné nastavení, která umožňuje určit pořadí, ve kterém jsou zpracovány filtry.</span><span class="sxs-lookup"><span data-stu-id="5c209-162">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="5c209-163">Pokud žádná priorita filtru není zadán, jsou všechny filtry vyhodnotí současně.</span><span class="sxs-lookup"><span data-stu-id="5c209-163">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5c209-164">Při zadávání prioritu filtr umožňuje vám umožňují řídit pořadí filtry, které se zpracovávají, může nepříznivě ovlivnit výkon služby směrování.</span><span class="sxs-lookup"><span data-stu-id="5c209-164">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="5c209-165">Pokud je to možné, vytvořte logiku filtru tak, aby použití filtru priority se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="5c209-165">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="5c209-166">Následující tabulku filtru definuje a přidá "Třída XPathFilter" definovaného dříve do tabulky s prioritou 2.</span><span class="sxs-lookup"><span data-stu-id="5c209-166">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="5c209-167">Tato položka také určuje, že pokud třída "XPathFilter" odpovídá zprávu, zpráva směrované na "roundingCalcEndpoint"</span><span class="sxs-lookup"><span data-stu-id="5c209-167">This entry also specifies that if the "XPathFilter" matches the message, the message will be routed to the "roundingCalcEndpoint"</span></span>  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          <filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="5c209-168">Při zadání priority filtru, filtry nejvyšší prioritou, se vyhodnocují jako první.</span><span class="sxs-lookup"><span data-stu-id="5c209-168">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="5c209-169">Pokud jeden nebo více filtrů na úrovni s konkrétní prioritou shodují, se vyhodnotí žádné filtry na nižších úrovních priority.</span><span class="sxs-lookup"><span data-stu-id="5c209-169">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="5c209-170">Pro tento scénář 2 je nejvyšší prioritou zadaný a toto je jediná položka filtru na této úrovni.</span><span class="sxs-lookup"><span data-stu-id="5c209-170">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2.  <span data-ttu-id="5c209-171">Chcete-li zkontrolovat, pokud je na koncový bod konkrétní přijata zpráva zkontrolováním název koncového bodu nebo předpona adresy byly definovány položky filtru.</span><span class="sxs-lookup"><span data-stu-id="5c209-171">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="5c209-172">Následující položky přidat obě tyto položky filtru do filtru tabulky a přidružit cílové koncové body, které zprávy budou směrované na.</span><span class="sxs-lookup"><span data-stu-id="5c209-172">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="5c209-173">Tyto filtry jsou nastavena priorita 1 k označení, že by měly být pouze spuštěny Pokud předchozí filtr XPath neodpovídá zprávy.</span><span class="sxs-lookup"><span data-stu-id="5c209-173">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="5c209-174">Vzhledem k tomu, že tyto filtry filtru prioritu 1, se bude vyhodnocena pouze pokud filtr úrovní priority 2 neodpovídá zprávy.</span><span class="sxs-lookup"><span data-stu-id="5c209-174">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="5c209-175">Navíc vzhledem k tomu, že oba filtry mají stejnou úrovní priority se vyhodnotí současně.</span><span class="sxs-lookup"><span data-stu-id="5c209-175">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="5c209-176">Protože oba filtry se vzájemně vylučují, je možné pouze jeden z nich tak, aby odpovídaly zprávu.</span><span class="sxs-lookup"><span data-stu-id="5c209-176">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3.  <span data-ttu-id="5c209-177">Pokud zpráva neodpovídá žádnému z předchozí filtrů, zpráva byla přijata prostřednictvím koncového bodu obecná služba a neobsahuje žádné informace hlavičky, která určuje, kam směruje.</span><span class="sxs-lookup"><span data-stu-id="5c209-177">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="5c209-178">Tyto zprávy jsou ke zpracování pomocí vlastního filtru, který zatížení je vyrovnává mezi službami dvě kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="5c209-178">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="5c209-179">Následující příklad ukazuje, jak přidat filtr položky do tabulce filtru. Každý filtr je spojen s jednou ze dvou cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="5c209-179">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="5c209-180">Protože tyto položky zadat prioritou 0, se bude vyhodnocena pouze pokud žádný filtr vyšší prioritu odpovídá zprávě.</span><span class="sxs-lookup"><span data-stu-id="5c209-180">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="5c209-181">Navíc vzhledem k tomu, jak jsou se stejnou prioritou, jsou vyhodnocovány současně.</span><span class="sxs-lookup"><span data-stu-id="5c209-181">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="5c209-182">Jak je uvedeno nahoře, vlastní filtr používá tyto definice filtru vyhodnotí pouze jednu nebo jiné jako `true` pro každý přijatá zpráva.</span><span class="sxs-lookup"><span data-stu-id="5c209-182">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="5c209-183">Protože pouze dva filtry jsou definovány pomocí stejné nastavení zadané skupiny tento filtr, efekt je, že střídá odesílání regularCalcEndpoint a RoundingCalcEndpoint směrovací služby.</span><span class="sxs-lookup"><span data-stu-id="5c209-183">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4.  <span data-ttu-id="5c209-184">Abyste mohli vyhodnotit zprávy před filtry, musí být tabulku filtru nejprve přidružený koncové body služby, které se použijí pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="5c209-184">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="5c209-185">Následující příklad ukazuje, jak přidružit do směrovací tabulky koncové body služby pomocí směrování chování:</span><span class="sxs-lookup"><span data-stu-id="5c209-185">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="5c209-186">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c209-186">Example</span></span>  
 <span data-ttu-id="5c209-187">Níže je úplný seznam všech konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5c209-187">The following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c209-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c209-188">See Also</span></span>  
 [<span data-ttu-id="5c209-189">Směrovací služby</span><span class="sxs-lookup"><span data-stu-id="5c209-189">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
