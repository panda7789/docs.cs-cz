---
title: 'Postupy: Používání filtrů'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 34ea961b0ef5db51efcae0b86f2c06171d6d756c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464105"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="483f1-102">Postupy: Používání filtrů</span><span class="sxs-lookup"><span data-stu-id="483f1-102">How To: Use Filters</span></span>
<span data-ttu-id="483f1-103">Toto téma popisuje základní kroky potřebné k vytvoření konfigurace směrování, která používá více filtrů.</span><span class="sxs-lookup"><span data-stu-id="483f1-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="483f1-104">V tomto příkladu zprávy jsou směrovány na dvě implementace kalkulačky služby, regularCalc a zaokrouhleníCalc.</span><span class="sxs-lookup"><span data-stu-id="483f1-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="483f1-105">Obě implementace podporují stejné operace; jedna služba však zaokrouhluje všechny výpočty na nejbližší celočíselnou hodnotu před vrácením.</span><span class="sxs-lookup"><span data-stu-id="483f1-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="483f1-106">Klientská aplikace musí být schopna určit, zda má být používána verze zaokrouhlení služby. Pokud není vyjádřena žádná předvolba služby, je zpráva vyrovnána zatížením mezi dvěma službami.</span><span class="sxs-lookup"><span data-stu-id="483f1-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="483f1-107">Operace vystavené oběma službami jsou:</span><span class="sxs-lookup"><span data-stu-id="483f1-107">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="483f1-108">Přidat</span><span class="sxs-lookup"><span data-stu-id="483f1-108">Add</span></span>  
  
- <span data-ttu-id="483f1-109">Odčítání</span><span class="sxs-lookup"><span data-stu-id="483f1-109">Subtract</span></span>  
  
- <span data-ttu-id="483f1-110">Násobení</span><span class="sxs-lookup"><span data-stu-id="483f1-110">Multiply</span></span>  
  
- <span data-ttu-id="483f1-111">Dělení</span><span class="sxs-lookup"><span data-stu-id="483f1-111">Divide</span></span>  
  
 <span data-ttu-id="483f1-112">Vzhledem k tomu, že obě služby implementují stejné operace, nelze použít filtr Akce, protože akce zadaná ve zprávě nebude jedinečná.</span><span class="sxs-lookup"><span data-stu-id="483f1-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="483f1-113">Místo toho je nutné provést další práci, aby zajistily, že zprávy jsou směrovány do příslušných koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="483f1-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="483f1-114">Určení jedinečných dat</span><span class="sxs-lookup"><span data-stu-id="483f1-114">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="483f1-115">Vzhledem k tomu, že obě implementace služby zpracovávají stejné operace a jsou v podstatě identické než data, která vracejí, základní data obsažená ve zprávách odeslaných z klientských aplikací nejsou dostatečně jedinečná, aby vám umožnila určit, jak směrovat požadavek.</span><span class="sxs-lookup"><span data-stu-id="483f1-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="483f1-116">Ale pokud klientská aplikace přidá jedinečnou hodnotu záhlaví zprávy, pak můžete tuto hodnotu použít k určení, jak by měla být zpráva směrována.</span><span class="sxs-lookup"><span data-stu-id="483f1-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="483f1-117">V tomto příkladu pokud klientská aplikace potřebuje zprávu, která má být zpracována kalkulačkou zaokrouhlení, přidá vlastní záhlaví pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="483f1-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="483f1-118">Nyní můžete použít filtr XPath ke kontrole zpráv pro toto záhlaví a směrovat zprávy obsahující záhlaví do služby roundCalc.</span><span class="sxs-lookup"><span data-stu-id="483f1-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="483f1-119">Navíc služba Směrování zpřístupňuje dva koncové body virtuální služby, které lze použít s filtry EndpointName, EndpointAddress nebo PrefixEndpointAddress k jedinečnému směrování příchozích zpráv do konkrétní implementace kalkulačky na základě koncového bodu, do kterého klientská aplikace odešle požadavek.</span><span class="sxs-lookup"><span data-stu-id="483f1-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="483f1-120">Definování koncových bodů</span><span class="sxs-lookup"><span data-stu-id="483f1-120">Define Endpoints</span></span>  
  
1. <span data-ttu-id="483f1-121">Při definování koncových bodů používaných službou Směrování byste měli nejprve určit tvar kanálu používaného klienty a službami.</span><span class="sxs-lookup"><span data-stu-id="483f1-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="483f1-122">V tomto scénáři obě cílové služby používají <xref:System.ServiceModel.Routing.IRequestReplyRouter> vzor požadavek odpověď, takže se používá.</span><span class="sxs-lookup"><span data-stu-id="483f1-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="483f1-123">Následující příklad definuje koncové body služby vystavené službou Směrování.</span><span class="sxs-lookup"><span data-stu-id="483f1-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
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
  
     <span data-ttu-id="483f1-124">S touto konfigurací služba Směrování zpřístupňuje tři samostatné koncové body.</span><span class="sxs-lookup"><span data-stu-id="483f1-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="483f1-125">V závislosti na volbách za běhu klientská aplikace odesílá zprávy na jednu z těchto adres.</span><span class="sxs-lookup"><span data-stu-id="483f1-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="483f1-126">Zprávy přicházející do jednoho z koncových bodů "virtuální" služby ("zaokrouhlení/kalkulačka" nebo "regular/calculator") jsou předány odpovídající implementaci kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="483f1-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="483f1-127">Pokud klientská aplikace neodesílá požadavek do určitého koncového bodu, zpráva je určena obecnému koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="483f1-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="483f1-128">Bez ohledu na zvolený koncový bod může klientská aplikace také zahrnout vlastní záhlaví označující, že zpráva by měla být předána implementaci kalkulačky zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="483f1-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="483f1-129">Následující příklad definuje koncové body klienta (cíle), ke kterým služba směrování směruje zprávy.</span><span class="sxs-lookup"><span data-stu-id="483f1-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
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
  
     <span data-ttu-id="483f1-130">Tyto koncové body se používají v tabulce filtrů k označení cílového koncového bodu, do který je zpráva odeslána, když odpovídá určitému filtru.</span><span class="sxs-lookup"><span data-stu-id="483f1-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="483f1-131">Definovat filtry</span><span class="sxs-lookup"><span data-stu-id="483f1-131">Define Filters</span></span>  
  
1. <span data-ttu-id="483f1-132">Chcete-li směrovat zprávy založené na vlastní záhlaví "ZaokrouhlováníCalculator", které klientská aplikace přidá do zprávy, definujte filtr, který používá dotaz XPath ke kontrole přítomnosti této hlavičky.</span><span class="sxs-lookup"><span data-stu-id="483f1-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="483f1-133">Vzhledem k tomu, že tato hlavička je definována pomocí vlastního oboru názvů, přidejte také položku oboru názvů, která definuje vlastní předponu oboru názvů "vlastní", která se používá v dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="483f1-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="483f1-134">Následující příklad definuje potřebný oddíl směrování, tabulku oboru názvů a filtr XPath.</span><span class="sxs-lookup"><span data-stu-id="483f1-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
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
  
     <span data-ttu-id="483f1-135">Tento **MessageFilter** hledá zaokrouhleníCalculator záhlaví ve zprávě, která obsahuje hodnotu "zaokrouhlení".</span><span class="sxs-lookup"><span data-stu-id="483f1-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="483f1-136">Tato hlavička je nastavena klientem označující, že zpráva by měla být směrována do zaokrouhleníCalc služby.</span><span class="sxs-lookup"><span data-stu-id="483f1-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="483f1-137">Předpona oboru názvů s12 je ve výchozím nastavení definována `http://www.w3.org/2003/05/soap-envelope`v tabulce oboru názvů a představuje obor názvů .</span><span class="sxs-lookup"><span data-stu-id="483f1-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="483f1-138">Musíte také definovat filtry, které hledají zprávy přijaté na dva virtuální koncové body.</span><span class="sxs-lookup"><span data-stu-id="483f1-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="483f1-139">První virtuální koncový bod je koncový bod "regular/calculator".</span><span class="sxs-lookup"><span data-stu-id="483f1-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="483f1-140">Klient může odesílat požadavky na tento koncový bod označující, že zpráva by měla být směrována do služby regularCalc.</span><span class="sxs-lookup"><span data-stu-id="483f1-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="483f1-141">Následující konfigurace definuje filtr, který <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> používá k určení, pokud zpráva dorazila prostřednictvím koncového bodu s názvem zadaným v filterData.</span><span class="sxs-lookup"><span data-stu-id="483f1-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="483f1-142">Pokud je zpráva přijata koncovým bodem služby s názvem "calculatorEndpoint", tento filtr vyhodnotí `true`.</span><span class="sxs-lookup"><span data-stu-id="483f1-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="483f1-143">Dále definujte filtr, který hledá zprávy odeslané na adresu roundingEndpoint.</span><span class="sxs-lookup"><span data-stu-id="483f1-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="483f1-144">Klient může odesílat požadavky do tohoto koncového bodu označující, že zpráva by měla být směrována do zaokrouhleníCalc služby.</span><span class="sxs-lookup"><span data-stu-id="483f1-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="483f1-145">Následující konfigurace definuje filtr, který <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> používá k určení, pokud zpráva dorazila na koncový bod "zaokrouhlení/kalkulačka".</span><span class="sxs-lookup"><span data-stu-id="483f1-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="483f1-146">Pokud je zpráva přijata na adresu, která `http://localhost/routingservice/router/rounding/` začíná, pak tento filtr vyhodnotí na **true**.</span><span class="sxs-lookup"><span data-stu-id="483f1-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="483f1-147">Vzhledem k tomu, že `http://localhost/routingservice/router` základní adresa používaná touto konfigurací je a adresa zadaná pro zaokrouhleníEndpoint je "zaokrouhlení/kalkulačka", úplná adresa používaná ke komunikaci s tímto koncovým bodem je `http://localhost/routingservice/router/rounding/calculator`, která odpovídá tomuto filtru.</span><span class="sxs-lookup"><span data-stu-id="483f1-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="483f1-148">Filtr PrefixEndpointAddress nevyhodnocuje název hostitele při provádění shody, protože jeden hostitel může být odkazován pomocí různých názvů hostitelů, které mohou být všechny platné způsoby odkazování na hostitele z klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="483f1-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="483f1-149">Například všechny následující mohou odkazovat na stejného hostitele:</span><span class="sxs-lookup"><span data-stu-id="483f1-149">For example, all of the following may refer to the same host:</span></span>  
    >
    > - <span data-ttu-id="483f1-150">localhost</span><span class="sxs-lookup"><span data-stu-id="483f1-150">localhost</span></span>  
    > - <span data-ttu-id="483f1-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="483f1-151">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="483f1-152">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="483f1-152">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="483f1-153">Konečný filtr musí podporovat směrování zpráv, které dorazí na obecný koncový bod bez vlastní hlavičky.</span><span class="sxs-lookup"><span data-stu-id="483f1-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="483f1-154">V tomto scénáři by zprávy by měly střídat mezi regularCalc a zaokrouhleníCalc služby.</span><span class="sxs-lookup"><span data-stu-id="483f1-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="483f1-155">Chcete-li podporovat směrování "kruhového dotazování" těchto zpráv, použijte vlastní filtr, který umožňuje, aby se jedna instance filtru shodovala pro každou zpracovávanou zprávu.</span><span class="sxs-lookup"><span data-stu-id="483f1-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="483f1-156">Následující definuje dvě instance RoundRobinMessageFilter, které jsou seskupeny dohromady označující, že by měly střídat mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="483f1-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
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
  
     <span data-ttu-id="483f1-157">Za běhu tento typ filtru se střídá mezi všemi definovanými instancemi filtru tohoto typu, které jsou konfigurovány jako stejná skupina, do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="483f1-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="483f1-158">To způsobí, že zprávy zpracované tímto `true` vlastním `RoundRobinFilter1` `RoundRobinFilter2`filtrem se budou střídat mezi návratem pro a .</span><span class="sxs-lookup"><span data-stu-id="483f1-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="483f1-159">Definovat tabulky filtrů</span><span class="sxs-lookup"><span data-stu-id="483f1-159">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="483f1-160">Chcete-li přidružit filtry ke konkrétním koncovým bodům klienta, musíte je umístit do tabulky filtrů.</span><span class="sxs-lookup"><span data-stu-id="483f1-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="483f1-161">Tento ukázkový scénář také používá nastavení priority filtru, což je volitelné nastavení, které umožňuje označit pořadí, ve kterém jsou filtry zpracovány.</span><span class="sxs-lookup"><span data-stu-id="483f1-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="483f1-162">Pokud není zadána žádná priorita filtru, jsou všechny filtry vyhodnocovány současně.</span><span class="sxs-lookup"><span data-stu-id="483f1-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="483f1-163">Při určení priority filtru umožňuje řídit pořadí, ve kterém jsou filtry zpracovávány, může nepříznivě ovlivnit výkon služby Směrování.</span><span class="sxs-lookup"><span data-stu-id="483f1-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="483f1-164">Pokud je to možné, vytvořte logiku filtru tak, aby nebylo vyžadováno použití priorit filtru.</span><span class="sxs-lookup"><span data-stu-id="483f1-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="483f1-165">Následující definuje tabulku filtrů a přidá "XPathFilter" definované dříve do tabulky s prioritou 2.</span><span class="sxs-lookup"><span data-stu-id="483f1-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="483f1-166">Tato položka také určuje, `XPathFilter` že pokud se zpráva shoduje, `roundingCalcEndpoint`bude zpráva směrována do .</span><span class="sxs-lookup"><span data-stu-id="483f1-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
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
          </filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="483f1-167">Při zadávání priority filtru jsou nejprve vyhodnoceny filtry s nejvyšší prioritou.</span><span class="sxs-lookup"><span data-stu-id="483f1-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="483f1-168">Pokud se jeden nebo více filtrů na určité úrovni priority shodují, nebudou vyhodnoceny žádné filtry na nižších úrovních priority.</span><span class="sxs-lookup"><span data-stu-id="483f1-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="483f1-169">V tomto scénáři 2 je nejvyšší priorita zadaná a toto je jediná položka filtru na této úrovni.</span><span class="sxs-lookup"><span data-stu-id="483f1-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="483f1-170">Položky filtru byly definovány ke kontrole, zda je zpráva přijata na konkrétní koncový bod kontrolou názvu koncového bodu nebo předpony adresy.</span><span class="sxs-lookup"><span data-stu-id="483f1-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="483f1-171">Následující položky přidají obě tyto položky filtru do tabulky filtrů a přidruží je k cílovým koncovým bodům, ke kterým bude zpráva směrována.</span><span class="sxs-lookup"><span data-stu-id="483f1-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="483f1-172">Tyto filtry jsou nastaveny na prioritu 1 označující, že by měly být spuštěny pouze v případě, že předchozí filtr XPath neodpovídá zprávě.</span><span class="sxs-lookup"><span data-stu-id="483f1-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="483f1-173">Vzhledem k tomu, že tyto filtry mají prioritu filtru 1, budou vyhodnoceny pouze v případě, že filtr na úrovni priority 2 neodpovídá zprávě.</span><span class="sxs-lookup"><span data-stu-id="483f1-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="483f1-174">Protože oba filtry mají stejnou úroveň priority, budou vyhodnoceny současně.</span><span class="sxs-lookup"><span data-stu-id="483f1-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="483f1-175">Vzhledem k tomu, že se oba filtry vzájemně vylučují, je možné, aby zprávu shodovaly pouze jeden nebo druhý filtr.</span><span class="sxs-lookup"><span data-stu-id="483f1-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="483f1-176">Pokud zpráva neodpovídá žádné z předchozích filtrů, byla zpráva přijata prostřednictvím obecného koncového bodu služby a neobsahovala žádné informace záhlaví, které by naznačovalo, kam ji směrovat.</span><span class="sxs-lookup"><span data-stu-id="483f1-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="483f1-177">Tyto zprávy mají být zpracovány vlastní filtr, který vyrovnává zatížení mezi dvěma kalkulačky služby.</span><span class="sxs-lookup"><span data-stu-id="483f1-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="483f1-178">Následující příklad ukazuje, jak přidat položky filtru do tabulky filtrů; každý filtr je přidružen k jednomu ze dvou cílových koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="483f1-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="483f1-179">Vzhledem k tomu, že tyto položky určují prioritu 0, budou vyhodnoceny pouze v případě, že zprávu neodpovídá žádnému filtru s vyšší prioritou.</span><span class="sxs-lookup"><span data-stu-id="483f1-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="483f1-180">Také, protože oba mají stejnou prioritu, jsou hodnoceny současně.</span><span class="sxs-lookup"><span data-stu-id="483f1-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="483f1-181">Jak již bylo zmíněno dříve, vlastní filtr používaný těmito definicemi filtrů vyhodnocuje pouze jednu nebo druhou jako `true` pro každou přijatou zprávu.</span><span class="sxs-lookup"><span data-stu-id="483f1-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="483f1-182">Vzhledem k tomu, že pouze dva filtry jsou definovány pomocí tohoto filtru, se stejným nastavením zadané skupiny, efekt je, že služba směrování střídá mezi odesílání do regularCalcEndpoint a ZaokrouhleníCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="483f1-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="483f1-183">Chcete-li vyhodnotit zprávy proti filtrům, musí být tabulka filtrů nejprve přidružena k koncovým bodům služby, které budou použity k příjmu zpráv.</span><span class="sxs-lookup"><span data-stu-id="483f1-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="483f1-184">Následující příklad ukazuje, jak přidružit směrovací tabulku k koncovým bodům služby pomocí chování směrování:</span><span class="sxs-lookup"><span data-stu-id="483f1-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="483f1-185">Příklad</span><span class="sxs-lookup"><span data-stu-id="483f1-185">Example</span></span>  
 <span data-ttu-id="483f1-186">Následuje úplný seznam konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="483f1-186">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="483f1-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="483f1-187">See also</span></span>

- [<span data-ttu-id="483f1-188">Směrovací služby</span><span class="sxs-lookup"><span data-stu-id="483f1-188">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
