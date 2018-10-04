---
title: 'Postupy: Použití filtrů'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: aee0f2e4fbf3b4e0802803b76aa557f2dec668bb
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48245189"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="a98df-102">Postupy: Použití filtrů</span><span class="sxs-lookup"><span data-stu-id="a98df-102">How To: Use Filters</span></span>
<span data-ttu-id="a98df-103">Toto téma popisuje základní kroky potřebné k vytvoření konfigurace směrování, která používá více filtrů.</span><span class="sxs-lookup"><span data-stu-id="a98df-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="a98df-104">V tomto příkladu jsou směrovány dvě implementace službu kalkulačky, regularCalc a roundingCalc zprávy.</span><span class="sxs-lookup"><span data-stu-id="a98df-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="a98df-105">Obou implementacích podporují stejné operace; jedna služba ale Zaokrouhlí všechny výpočty na nejbližší celočíselnou hodnotu před vrácením.</span><span class="sxs-lookup"><span data-stu-id="a98df-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="a98df-106">Klientská aplikace musí být schopen určit, jestli se má použít zaokrouhlení verze služby; Pokud je vyjádřená žádná předvolba služby zpráva je mezi těmito dvěma službami s vyrovnáváním zatížení.</span><span class="sxs-lookup"><span data-stu-id="a98df-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="a98df-107">Operace vystavené obě služby jsou:</span><span class="sxs-lookup"><span data-stu-id="a98df-107">The operations exposed by both services are:</span></span>  
  
-   <span data-ttu-id="a98df-108">Přidejte</span><span class="sxs-lookup"><span data-stu-id="a98df-108">Add</span></span>  
  
-   <span data-ttu-id="a98df-109">Odečíst</span><span class="sxs-lookup"><span data-stu-id="a98df-109">Subtract</span></span>  
  
-   <span data-ttu-id="a98df-110">Násobení</span><span class="sxs-lookup"><span data-stu-id="a98df-110">Multiply</span></span>  
  
-   <span data-ttu-id="a98df-111">Dělení</span><span class="sxs-lookup"><span data-stu-id="a98df-111">Divide</span></span>  
  
 <span data-ttu-id="a98df-112">Vzhledem k tomu, že obě služby implementovat stejné operace, nemůžete použít filtr akce, protože akce určená ve zprávě nesmí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="a98df-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="a98df-113">Místo toho je nutné provést další práce k zajištění, že zprávy jsou směrovány na jednotlivé koncové body.</span><span class="sxs-lookup"><span data-stu-id="a98df-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="a98df-114">Určení jedinečných dat</span><span class="sxs-lookup"><span data-stu-id="a98df-114">Determine Unique Data</span></span>  
  
1.  <span data-ttu-id="a98df-115">Protože obou implementacích služby zpracování stejné operace a jsou v podstatě totožné než data, která vrátí, základní data obsažená ve zprávách odesílaných z klientských aplikací není dostatečně jedinečných, aby bylo možné určit, jak se směrují požadavek.</span><span class="sxs-lookup"><span data-stu-id="a98df-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="a98df-116">Ale pokud klientská aplikace přidá hodnotu záhlaví ke zprávě, pak můžete použít tuto hodnotu k určení, jak se mají směrovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="a98df-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="a98df-117">Například pokud klientská aplikace potřebuje zpráva, která má být zpracována zaokrouhlení kalkulačky, přidá vlastní hlavičku s použitím následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="a98df-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="a98df-118">Teď můžete použít filtr XPath ke kontrole zpráv pro toto záhlaví a směrovat zprávy obsahující hlavičku do roundCalc služby.</span><span class="sxs-lookup"><span data-stu-id="a98df-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2.  <span data-ttu-id="a98df-119">Kromě toho služba Směrování poskytuje dva koncové body služby virtuální, které lze použít s Název_koncového_bodu EndpointAddress, nebo filtruje PrefixEndpointAddress jednoznačně směrovat příchozí zprávy pro konkrétní Kalkulačka implementaci založené na koncový bod do které klientská aplikace odešle požadavek.</span><span class="sxs-lookup"><span data-stu-id="a98df-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="a98df-120">Definujte koncové body</span><span class="sxs-lookup"><span data-stu-id="a98df-120">Define Endpoints</span></span>  
  
1.  <span data-ttu-id="a98df-121">Při definování koncových bodů použitých službou směrování, byste měli určit tvar kanálu používat klientů a služeb.</span><span class="sxs-lookup"><span data-stu-id="a98df-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="a98df-122">V tomto scénáři cílové služby použít model požadavek odpověď, proto <xref:System.ServiceModel.Routing.IRequestReplyRouter> se používá.</span><span class="sxs-lookup"><span data-stu-id="a98df-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="a98df-123">Následující příklad definuje koncové body služby, vystavený službou směrování.</span><span class="sxs-lookup"><span data-stu-id="a98df-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
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
  
     <span data-ttu-id="a98df-124">S touto konfigurací směrovací služba poskytuje tři samostatné koncové body.</span><span class="sxs-lookup"><span data-stu-id="a98df-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="a98df-125">V závislosti na možnosti běhu klientská aplikace odešle zprávy do jedné z těchto adres.</span><span class="sxs-lookup"><span data-stu-id="a98df-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="a98df-126">Zprávy odeslané na jednom z koncových bodů služby "virtuální" ("zaokrouhlení/Kalkulačka" nebo "normální/Kalkulačka") se předávají do odpovídající implementace kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="a98df-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="a98df-127">Pokud klientská aplikace nebude odeslat žádost o konkrétní koncový bod, zpráva zaslána obecné koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a98df-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="a98df-128">Bez ohledu na zvolené koncový bod klientská aplikace si také obsahovat vlastní hlavičky k označení, že mají zprávy předávat zaokrouhlení implementace kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="a98df-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2.  <span data-ttu-id="a98df-129">Následující příklad definuje, které směrovací služba provádí směrování zpráv do koncových bodů klienta (cíl).</span><span class="sxs-lookup"><span data-stu-id="a98df-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
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
  
     <span data-ttu-id="a98df-130">Tyto koncové body jsou v tabulce filtrů slouží k označení cílový koncový bod, který je zpráva odeslána případě, že odpovídá konkrétní filtr.</span><span class="sxs-lookup"><span data-stu-id="a98df-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="a98df-131">Definování filtrů</span><span class="sxs-lookup"><span data-stu-id="a98df-131">Define Filters</span></span>  
  
1.  <span data-ttu-id="a98df-132">Chcete-li směrovat zprávy založené na vlastní hlavičky "RoundingCalculator", který klientská aplikace přidá do zprávy, definujte filtr, který se použije dotaz XPath ke kontrole přítomnosti této hlavičky.</span><span class="sxs-lookup"><span data-stu-id="a98df-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="a98df-133">Protože tato hlavička se definuje pomocí vlastního oboru názvů, přidejte také zadání oboru názvů, který definuje předponu vlastního oboru názvů "vlastní", který se používá v dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="a98df-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="a98df-134">Následující příklad definuje oddíl nezbytné směrování, obor názvů tabulku a filtr XPath.</span><span class="sxs-lookup"><span data-stu-id="a98df-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
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
  
     <span data-ttu-id="a98df-135">To **MessageFilter** hledá RoundingCalculator záhlaví ve zprávě, která obsahuje hodnotu "zaokrouhlení".</span><span class="sxs-lookup"><span data-stu-id="a98df-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="a98df-136">Tato hlavička nastavená klientem k označení, že se mají směrovat zprávy do služby roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="a98df-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a98df-137">Předpona oboru názvů S12 na úrovni Standard je definované ve výchozím nastavení v tabulce obor názvů a představuje obor názvů `http://www.w3.org/2003/05/soap-envelope`.</span><span class="sxs-lookup"><span data-stu-id="a98df-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2.  <span data-ttu-id="a98df-138">Musíte také definovat filtry, které vyhledávají zprávy přijaté na dva virtuální koncové body.</span><span class="sxs-lookup"><span data-stu-id="a98df-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="a98df-139">První virtuální koncový bod je koncový bod "normální/Kalkulačka".</span><span class="sxs-lookup"><span data-stu-id="a98df-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="a98df-140">K tomuto koncovému bodu k označení, že se mají směrovat zprávy do služby regularCalc může klient odeslat požadavky.</span><span class="sxs-lookup"><span data-stu-id="a98df-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="a98df-141">Definuje filtr, který používá následující konfiguraci <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> k určení, pokud byla zpráva doručena prostřednictvím koncového bodu s názvem zadaným v fulltextových dat filtru.</span><span class="sxs-lookup"><span data-stu-id="a98df-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="a98df-142">Pokud zprávu neobdrží koncový bod služby s názvem "calculatorEndpoint", tento filtr se vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="a98df-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3.  <span data-ttu-id="a98df-143">Dále definujte filtr, který hledá zprávy odeslané na adresu roundingEndpoint.</span><span class="sxs-lookup"><span data-stu-id="a98df-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="a98df-144">K tomuto koncovému bodu k označení, že se mají směrovat zprávy do služby roundingCalc může klient odeslat požadavky.</span><span class="sxs-lookup"><span data-stu-id="a98df-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="a98df-145">Definuje filtr, který používá následující konfiguraci <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> k určení, pokud byly přijaty zprávy v koncovém bodě "zaokrouhlení/Kalkulačka".</span><span class="sxs-lookup"><span data-stu-id="a98df-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="a98df-146">Pokud je přijata zpráva na adresu, která začíná `http://localhost/routingservice/router/rounding/` pak vyhodnotí jako tento filtr **true**.</span><span class="sxs-lookup"><span data-stu-id="a98df-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="a98df-147">Protože je základní adresu použitou touto konfigurací `http://localhost/routingservice/router` a je úplná adresa slouží ke komunikaci s tímto koncovým bodem adresa zadaná pro roundingEndpoint je "zaokrouhlení/Kalkulačka" `http://localhost/routingservice/router/rounding/calculator`, který odpovídá tomuto filtru.</span><span class="sxs-lookup"><span data-stu-id="a98df-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a98df-148">Filtr PrefixEndpointAddress nevyhodnocuje název hostitele při provádění shodu, protože je jeden hostitel lze odkazovat pomocí různých názvů hostitelů, které mohou všechny být platné způsoby odkazující na hostitele z klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="a98df-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="a98df-149">Všechny tyto například může odkazovat na stejného hostitele:</span><span class="sxs-lookup"><span data-stu-id="a98df-149">For example, all of the following may refer to the same host:</span></span>  
    >   
    > -   <span data-ttu-id="a98df-150">localhost</span><span class="sxs-lookup"><span data-stu-id="a98df-150">localhost</span></span>  
    > -   <span data-ttu-id="a98df-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="a98df-151">127.0.0.1</span></span>  
    > -   `www.contoso.com`  
    > -   <span data-ttu-id="a98df-152">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="a98df-152">ContosoWeb01</span></span>  
  
4.  <span data-ttu-id="a98df-153">Konečné filtr musí podporovat směrování zpráv, které přicházejí na obecné koncový bod bez vlastní hlavičce.</span><span class="sxs-lookup"><span data-stu-id="a98df-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="a98df-154">V tomto scénáři by měl alternativní zpráv mezi službami regularCalc a roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="a98df-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="a98df-155">Pro podporu "kruhové dotazování" směrování tyto zprávy, použijte vlastní filtr, který umožňuje jedna instance filtru tak, aby odpovídaly pro každou zprávu zpracovat.</span><span class="sxs-lookup"><span data-stu-id="a98df-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="a98df-156">Následující informace definují dvě instance RoundRobinMessageFilter, které jsou seskupeny k označení, že by měl alternativní mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="a98df-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
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
  
     <span data-ttu-id="a98df-157">Za běhu tento typ filtru střídá všechny definovaný filtr instance tohoto typu, které jsou nakonfigurované jako stejnou skupinu do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="a98df-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="a98df-158">To způsobí, že zprávy zpracované tento vlastní filtr do alternativní mezi vrácení `true` pro `RoundRobinFilter1` a `RoundRobinFilter2`.</span><span class="sxs-lookup"><span data-stu-id="a98df-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="a98df-159">Definujte filtr tabulky</span><span class="sxs-lookup"><span data-stu-id="a98df-159">Define Filter Tables</span></span>  
  
1.  <span data-ttu-id="a98df-160">Filtry přidružit s koncovými body konkrétního klienta, je nutné je umístit v tabulce filtrů.</span><span class="sxs-lookup"><span data-stu-id="a98df-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="a98df-161">Tento ukázkový scénář také používá nastavení priority filtr, což je volitelné nastavení, která umožňuje určit pořadí, ve kterém jsou zpracovány filtry.</span><span class="sxs-lookup"><span data-stu-id="a98df-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="a98df-162">Pokud není zadána žádná priorita filtru, všechny filtry jsou vyhodnocovány současně.</span><span class="sxs-lookup"><span data-stu-id="a98df-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a98df-163">Při zadávání prioritu filtr umožňuje řídit pořadí, ve které filtry se zpracovávají, může nepříznivě ovlivnit výkon služby směrování.</span><span class="sxs-lookup"><span data-stu-id="a98df-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="a98df-164">Pokud je to možné, vytvořte filtr logiky tak, aby se nevyžaduje použití filtru priority.</span><span class="sxs-lookup"><span data-stu-id="a98df-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="a98df-165">Následující tabulka filtr definuje a přidá "Třída XPathFilter" definovali dříve do tabulky s prioritou 2.</span><span class="sxs-lookup"><span data-stu-id="a98df-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="a98df-166">Tato položka také určuje, že pokud `XPathFilter` odpovídá zprávu, zpráva se budou směrovat do `roundingCalcEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="a98df-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
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
  
     <span data-ttu-id="a98df-167">Při určování priority filtr, filtry nejvyšší prioritou, je vyhodnocen jako první.</span><span class="sxs-lookup"><span data-stu-id="a98df-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="a98df-168">Pokud jeden nebo více filtrů na úrovni s konkrétní prioritou shodují, se vyhodnotí na nižších úrovních priority se žádné filtry.</span><span class="sxs-lookup"><span data-stu-id="a98df-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="a98df-169">V tomto scénáři 2 je nejvyšší pořadí podle priority a jde o jediný záznam filtr na této úrovni.</span><span class="sxs-lookup"><span data-stu-id="a98df-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2.  <span data-ttu-id="a98df-170">Chcete-li zkontrolovat, pokud je přijata zpráva na určitý koncový bod zkontrolováním název koncového bodu nebo předpona adresy byly definovány položky filtru.</span><span class="sxs-lookup"><span data-stu-id="a98df-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="a98df-171">Následující položky přidat obě tyto položky filtru tabulky filtru a přidružit je k cílové koncové body, které zprávy se budou směrovat do.</span><span class="sxs-lookup"><span data-stu-id="a98df-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="a98df-172">Tyto filtry nastavené s prioritou 1 označuje, že jejich by měl spustí jenom v případě předchozího filtr XPath neodpovídá zprávu.</span><span class="sxs-lookup"><span data-stu-id="a98df-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="a98df-173">Vzhledem k tomu, že tyto filtry filtr priority 1, že bude vyhodnocena pouze pokud filtr na úrovni priority 2 neodpovídá zprávu.</span><span class="sxs-lookup"><span data-stu-id="a98df-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="a98df-174">Navíc vzhledem k tomu, že oba filtry mají stejnou prioritu, se vyhodnotí současně.</span><span class="sxs-lookup"><span data-stu-id="a98df-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="a98df-175">Protože oba filtry se vzájemně vylučují, je možné pouze jeden z nich tak, aby odpovídaly zprávu.</span><span class="sxs-lookup"><span data-stu-id="a98df-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3.  <span data-ttu-id="a98df-176">Pokud zpráva neodpovídá žádnému z předchozí filtrů, zpráva byla přijata prostřednictvím koncového bodu obecná služba a neobsahuje žádné informace hlavičky, která označuje, kde ho směrovat.</span><span class="sxs-lookup"><span data-stu-id="a98df-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="a98df-177">Tyto zprávy jsou zpracovávat vlastní filtr vyrovnává které zatížení mezi dvěma Kalkulačka služby.</span><span class="sxs-lookup"><span data-stu-id="a98df-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="a98df-178">Následující příklad ukazuje, jak přidat filtr položky do tabulce filtru. Každý filtr je přidružený nejméně k jednomu ze dvou cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="a98df-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="a98df-179">Protože tyto položky určit prioritu 0, že bude vyhodnocena pouze pokud žádný filtr s vyšší prioritou odpovídá zprávu.</span><span class="sxs-lookup"><span data-stu-id="a98df-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="a98df-180">Také protože obě mají stejnou prioritu, jsou vyhodnocovány současně.</span><span class="sxs-lookup"><span data-stu-id="a98df-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="a98df-181">Jak už bylo zmíněno dříve, vlastní filtr používá tyto definice filtru vyhodnotí pouze jednu nebo jiných jako `true` u každé zprávy přijaté.</span><span class="sxs-lookup"><span data-stu-id="a98df-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="a98df-182">Protože pouze dva filtry jsou definovány pomocí tohoto filtru, stejné nastavení zadané skupiny, efekt je, že směrovací služba střídá odesílání regularCalcEndpoint a RoundingCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="a98df-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4.  <span data-ttu-id="a98df-183">K vyhodnocení zpráv filtry, musí být filtr tabulky nejprve přidružené koncové body služby, které se použijí pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="a98df-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="a98df-184">Následující příklad ukazuje, jak přidružit směrovací tabulce koncových bodů služby pomocí směrování chování:</span><span class="sxs-lookup"><span data-stu-id="a98df-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="a98df-185">Příklad</span><span class="sxs-lookup"><span data-stu-id="a98df-185">Example</span></span>  
 <span data-ttu-id="a98df-186">Tady je úplný seznam všech konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a98df-186">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a98df-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="a98df-187">See Also</span></span>  
 [<span data-ttu-id="a98df-188">Směrovací služby</span><span class="sxs-lookup"><span data-stu-id="a98df-188">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
