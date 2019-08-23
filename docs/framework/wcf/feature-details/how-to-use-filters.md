---
title: 'Postupy: Používání filtrů'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 6c357f2f410362d56fc931529a9fe731df0a477e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968770"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="66202-102">Postupy: Používání filtrů</span><span class="sxs-lookup"><span data-stu-id="66202-102">How To: Use Filters</span></span>
<span data-ttu-id="66202-103">Toto téma popisuje základní kroky potřebné k vytvoření konfigurace směrování, která používá více filtrů.</span><span class="sxs-lookup"><span data-stu-id="66202-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="66202-104">V tomto příkladu jsou zprávy směrovány do dvou implementací služby kalkulačky, regularCalc a roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="66202-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="66202-105">Obě implementace podporují stejné operace. Nicméně jedna služba Zaokrouhlí všechny výpočty na nejbližší celočíselnou hodnotu před vrácením.</span><span class="sxs-lookup"><span data-stu-id="66202-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="66202-106">Klientská aplikace musí být schopná určit, jestli se má použít verze zaokrouhlení služby. Pokud se nevyjádří žádné předvolby služby, vyrovnává se zatížení mezi těmito dvěma službami.</span><span class="sxs-lookup"><span data-stu-id="66202-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="66202-107">Mezi operace vystavené oběma službami patří:</span><span class="sxs-lookup"><span data-stu-id="66202-107">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="66202-108">Přidejte</span><span class="sxs-lookup"><span data-stu-id="66202-108">Add</span></span>  
  
- <span data-ttu-id="66202-109">Odečten</span><span class="sxs-lookup"><span data-stu-id="66202-109">Subtract</span></span>  
  
- <span data-ttu-id="66202-110">Hodnotou</span><span class="sxs-lookup"><span data-stu-id="66202-110">Multiply</span></span>  
  
- <span data-ttu-id="66202-111">Rozdělovací</span><span class="sxs-lookup"><span data-stu-id="66202-111">Divide</span></span>  
  
 <span data-ttu-id="66202-112">Vzhledem k tomu, že obě služby implementují stejné operace, nemůžete použít filtr akcí, protože akce zadaná ve zprávě nebude jedinečná.</span><span class="sxs-lookup"><span data-stu-id="66202-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="66202-113">Místo toho je nutné provést další práci, aby bylo zajištěno, že budou zprávy směrovány do příslušných koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="66202-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="66202-114">Určení jedinečných dat</span><span class="sxs-lookup"><span data-stu-id="66202-114">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="66202-115">Vzhledem k tomu, že obě implementace služby pracují se stejnými operacemi a jsou v podstatě totožné s daty, která vrací, nejsou základní data obsažená ve zprávách odesílaných klientskými aplikacemi dostatečně jedinečná, aby bylo možné určit, jak se má směrovat Request.</span><span class="sxs-lookup"><span data-stu-id="66202-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="66202-116">Pokud však klientská aplikace přidá do zprávy jedinečnou hodnotu záhlaví, můžete tuto hodnotu použít k určení způsobu směrování zprávy.</span><span class="sxs-lookup"><span data-stu-id="66202-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="66202-117">V tomto příkladu, Pokud klientská aplikace potřebuje zprávu zpracovat kalkulačkou zaokrouhlení, přidá vlastní hlavičku pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="66202-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="66202-118">Nyní můžete použít filtr XPath ke kontrole zpráv pro tuto hlavičku a směrování zpráv obsahujících hlavičku do služby roundCalc.</span><span class="sxs-lookup"><span data-stu-id="66202-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="66202-119">Směrovací služba navíc zveřejňuje dva koncové body virtuální služby, které se dají použít s filtry koncového bodu, EndpointAddress nebo PrefixEndpointAddress k jedinečnému směrování příchozích zpráv do konkrétní implementace kalkulačky založené na koncovém bodu. do které klientská aplikace požadavek odešle.</span><span class="sxs-lookup"><span data-stu-id="66202-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="66202-120">Definování koncových bodů</span><span class="sxs-lookup"><span data-stu-id="66202-120">Define Endpoints</span></span>  
  
1. <span data-ttu-id="66202-121">Při definování koncových bodů používaných směrovací službou byste nejdřív měli určit tvar kanálu používaného klienty a službami.</span><span class="sxs-lookup"><span data-stu-id="66202-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="66202-122">V tomto scénáři používají cílové služby vzor požadavek-odpověď, takže <xref:System.ServiceModel.Routing.IRequestReplyRouter> se použije.</span><span class="sxs-lookup"><span data-stu-id="66202-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="66202-123">Následující příklad definuje koncové body služby vystavené směrovací službou.</span><span class="sxs-lookup"><span data-stu-id="66202-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
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
  
     <span data-ttu-id="66202-124">V této konfiguraci služba Směrování zveřejňuje tři samostatné koncové body.</span><span class="sxs-lookup"><span data-stu-id="66202-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="66202-125">V závislosti na volbách za běhu odesílá klientská aplikace zprávy na jednu z těchto adres.</span><span class="sxs-lookup"><span data-stu-id="66202-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="66202-126">Zprávy přicházející v jednom z "virtuálních" koncových bodů služby ("zaokrouhlování/Kalkulačka" nebo "Regular/Kalkulačka") se předávají odpovídající implementaci kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="66202-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="66202-127">Pokud klientská aplikace neodešle požadavek do konkrétního koncového bodu, bude zpráva adresována do obecného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="66202-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="66202-128">Bez ohledu na zvolený koncový bod může klientská aplikace také zahrnout vlastní hlavičku, aby označovala, že by měla být zpráva předána implementaci kalkulačky zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="66202-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="66202-129">Následující příklad definuje koncové body klienta (cílové), na které směrovací služba směruje zprávy.</span><span class="sxs-lookup"><span data-stu-id="66202-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
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
  
     <span data-ttu-id="66202-130">Tyto koncové body se používají v tabulce filtru k označení cílového koncového bodu, na který se zpráva pošle, když odpovídá konkrétnímu filtru.</span><span class="sxs-lookup"><span data-stu-id="66202-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="66202-131">Definovat filtry</span><span class="sxs-lookup"><span data-stu-id="66202-131">Define Filters</span></span>  
  
1. <span data-ttu-id="66202-132">Chcete-li směrovat zprávy založené na vlastní hlavičce "RoundingCalculator", kterou klientská aplikace přidá do zprávy, definujte filtr, který používá dotaz XPath ke kontrole přítomnosti této hlavičky.</span><span class="sxs-lookup"><span data-stu-id="66202-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="66202-133">Vzhledem k tomu, že je tato hlavička definována pomocí vlastního oboru názvů, přidejte také položku oboru názvů definující vlastní předponu oboru názvů "Custom", která se používá v dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="66202-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="66202-134">Následující příklad definuje nezbytný oddíl směrování, tabulku oboru názvů a filtr XPath.</span><span class="sxs-lookup"><span data-stu-id="66202-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
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
  
     <span data-ttu-id="66202-135">Tento **MessageFilter** vyhledá hlavičku RoundingCalculator ve zprávě, která obsahuje hodnotu "zaokrouhlení".</span><span class="sxs-lookup"><span data-stu-id="66202-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="66202-136">Tato hlavička je nastavena klientem, aby označovala, že by měla být zpráva směrována do služby roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="66202-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="66202-137">Předpona oboru názvů S12 je ve výchozím nastavení definována v tabulce oboru názvů a představuje obor `http://www.w3.org/2003/05/soap-envelope`názvů.</span><span class="sxs-lookup"><span data-stu-id="66202-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="66202-138">Musíte také definovat filtry, které hledají zprávy přijaté ve dvou virtuálních koncových bodech.</span><span class="sxs-lookup"><span data-stu-id="66202-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="66202-139">Prvním virtuálním koncovým bodem je koncový bod Regular/kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="66202-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="66202-140">Klient může odesílat požadavky na tento koncový bod, aby označoval, že by se měla směrovat zpráva do služby regularCalc.</span><span class="sxs-lookup"><span data-stu-id="66202-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="66202-141">Následující konfigurace definuje filtr, který používá <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> k určení, zda byla zpráva doručena prostřednictvím koncového bodu s názvem zadaným v fulltextových.</span><span class="sxs-lookup"><span data-stu-id="66202-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="66202-142">Pokud koncový bod služby s názvem "calculatorEndpoint" obdrží zprávu, tento filtr se `true`vyhodnotí jako.</span><span class="sxs-lookup"><span data-stu-id="66202-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="66202-143">Dále Definujte filtr, který vyhledává zprávy odeslané na adresu roundingEndpoint.</span><span class="sxs-lookup"><span data-stu-id="66202-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="66202-144">Klient může odesílat požadavky na tento koncový bod, aby označoval, že by se měla směrovat zpráva do služby roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="66202-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="66202-145">Následující konfigurace definuje filtr, který používá <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> k určení, zda byla zpráva doručena do koncového bodu zaokrouhlení/kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="66202-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="66202-146">Pokud je zpráva přijata na adrese, která začíná `http://localhost/routingservice/router/rounding/` na, tento filtr se vyhodnotí jako **true**.</span><span class="sxs-lookup"><span data-stu-id="66202-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="66202-147">Vzhledem k tomu, že základní adresa používaná touto `http://localhost/routingservice/router` konfigurací je a adresa zadaná pro roundingEndpoint je "zaokrouhlování/Kalkulačka", úplná adresa použitá ke komunikaci s tímto koncovým `http://localhost/routingservice/router/rounding/calculator`bodem je, což odpovídá tomuto filtru.</span><span class="sxs-lookup"><span data-stu-id="66202-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="66202-148">Filtr PrefixEndpointAddress nevyhodnotí název hostitele při shodě, protože jeden hostitel může být odkazován pomocí různých názvů hostitelů, které mohou být platnými způsoby odkazu na hostitele z klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="66202-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="66202-149">Například všechny následující mohou odkazovat na stejného hostitele:</span><span class="sxs-lookup"><span data-stu-id="66202-149">For example, all of the following may refer to the same host:</span></span>  
    >   
    > - <span data-ttu-id="66202-150">místního</span><span class="sxs-lookup"><span data-stu-id="66202-150">localhost</span></span>  
    > - <span data-ttu-id="66202-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="66202-151">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="66202-152">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="66202-152">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="66202-153">Konečný filtr musí podporovat směrování zpráv, které přicházejí do obecného koncového bodu bez vlastní hlavičky.</span><span class="sxs-lookup"><span data-stu-id="66202-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="66202-154">V tomto scénáři by se zprávy měly střídat mezi službami regularCalc a roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="66202-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="66202-155">Aby bylo možné podporovat "kruhové dotazování" těchto zpráv, použijte vlastní filtr, který umožňuje, aby jedna instance filtru odpovídala každé zpracovávané zprávě.</span><span class="sxs-lookup"><span data-stu-id="66202-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="66202-156">Níže jsou definovány dvě instance RoundRobinMessageFilter, které jsou seskupeny tak, aby označovaly, že by měly být mezi sebou vzájemně jiné.</span><span class="sxs-lookup"><span data-stu-id="66202-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
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
  
     <span data-ttu-id="66202-157">Za běhu tento typ filtru střídavě mezi všemi definovanými instancemi filtru tohoto typu, které jsou nakonfigurované jako stejné skupiny, do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="66202-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="66202-158">To způsobí, že se zprávy zpracovávané tímto vlastním filtrem `true` střídají `RoundRobinFilter1` mezi `RoundRobinFilter2`vrácením pro a.</span><span class="sxs-lookup"><span data-stu-id="66202-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="66202-159">Definice tabulek filtru</span><span class="sxs-lookup"><span data-stu-id="66202-159">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="66202-160">Chcete-li přidružit filtry ke konkrétním koncovým bodům klienta, je nutné je umístit do tabulky filtru.</span><span class="sxs-lookup"><span data-stu-id="66202-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="66202-161">Tento ukázkový scénář také používá nastavení priority filtru, což je volitelné nastavení, které umožňuje určit pořadí, ve kterém jsou filtry zpracovávány.</span><span class="sxs-lookup"><span data-stu-id="66202-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="66202-162">Pokud není zadána žádná priorita filtru, všechny filtry budou vyhodnocovány současně.</span><span class="sxs-lookup"><span data-stu-id="66202-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="66202-163">Když zadáte prioritu filtru, můžete řídit pořadí, ve kterém se filtry zpracovávají, což může negativně ovlivnit výkon směrovací služby.</span><span class="sxs-lookup"><span data-stu-id="66202-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="66202-164">Pokud je to možné, sestavte logiku filtru tak, aby se použití priorit filtru nevyžadovalo.</span><span class="sxs-lookup"><span data-stu-id="66202-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="66202-165">Následující definice tabulky filtru a přidá "Třída XPathFilter" definované dříve v tabulce s prioritou 2.</span><span class="sxs-lookup"><span data-stu-id="66202-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="66202-166">Tato položka také určuje, že pokud `XPathFilter` zpráva odpovídá, bude zpráva směrována `roundingCalcEndpoint`do.</span><span class="sxs-lookup"><span data-stu-id="66202-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
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
  
     <span data-ttu-id="66202-167">Při zadávání priority filtru jsou nejprve vyhodnocovány filtry s nejvyšší prioritou.</span><span class="sxs-lookup"><span data-stu-id="66202-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="66202-168">Pokud jeden nebo více filtrů na určité úrovni priority odpovídá, nebudou vyhodnoceny žádné filtry na úrovních s nižší prioritou.</span><span class="sxs-lookup"><span data-stu-id="66202-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="66202-169">V tomto scénáři je 2 zadaná nejvyšší priorita a jedná se o jedinou položku filtru na této úrovni.</span><span class="sxs-lookup"><span data-stu-id="66202-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="66202-170">Byly definovány položky filtru, aby bylo možné zjistit, zda je zpráva přijata v určitém koncovém bodu, a to kontrolou názvu koncového bodu nebo předpony adresy.</span><span class="sxs-lookup"><span data-stu-id="66202-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="66202-171">Následující záznamy tyto položky filtru přidejte do tabulky filtru a přidružte je k cílovým koncovým bodům, na které bude zpráva směrována.</span><span class="sxs-lookup"><span data-stu-id="66202-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="66202-172">U těchto filtrů je nastavena priorita 1, což označuje, že by měly být spuštěny pouze v případě, že předchozí filtr XPath neodpovídá zprávě.</span><span class="sxs-lookup"><span data-stu-id="66202-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="66202-173">Vzhledem k tomu, že tyto filtry mají prioritu filtru 1, budou vyhodnoceny pouze v případě, že filtr s úrovní priority 2 neodpovídá zprávě.</span><span class="sxs-lookup"><span data-stu-id="66202-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="66202-174">Vzhledem k tomu, že oba filtry mají stejnou úroveň priority, budou vyhodnocovány současně.</span><span class="sxs-lookup"><span data-stu-id="66202-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="66202-175">Vzhledem k tomu, že oba filtry se vzájemně vylučují, je možné, že pouze jedna nebo druhá bude odpovídat zprávě.</span><span class="sxs-lookup"><span data-stu-id="66202-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="66202-176">Pokud se zpráva neshoduje s žádným z předchozích filtrů, pak byla zpráva přijata prostřednictvím obecného koncového bodu služby a neobsahuje žádné informace v hlavičce, které určují, kam se má směrovat.</span><span class="sxs-lookup"><span data-stu-id="66202-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="66202-177">Tyto zprávy mají být zpracovány vlastním filtrem, který vyrovnává jejich zatížení mezi dvěma službami kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="66202-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="66202-178">Následující příklad ukazuje, jak přidat položky filtru do tabulky filtru; Každý filtr je přidružen k jednomu ze dvou cílových koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="66202-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="66202-179">Vzhledem k tomu, že tyto položky určují prioritu 0, budou vyhodnoceny pouze v případě, že se zpráva neshoduje s žádným filtrem s vyšší prioritou.</span><span class="sxs-lookup"><span data-stu-id="66202-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="66202-180">Kromě toho, vzhledem k tomu, že oba mají stejnou prioritu, jsou vyhodnocovány současně.</span><span class="sxs-lookup"><span data-stu-id="66202-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="66202-181">Jak již bylo zmíněno dříve, vlastní filtr používaný těmito definicemi filtru vyhodnocuje pouze jeden nebo druhý `true` jako pro každou přijatou zprávu.</span><span class="sxs-lookup"><span data-stu-id="66202-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="66202-182">Vzhledem k tomu, že jsou pomocí tohoto filtru definované jenom dva filtry se stejným nastavením skupiny, použije se tento efekt jako služba Směrování mezi odesláním do regularCalcEndpoint a RoundingCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="66202-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="66202-183">Aby bylo možné vyhodnotit zprávy proti filtrům, musí být nejprve přidružena k koncovým bodům služby, které budou použity pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="66202-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="66202-184">Následující příklad ukazuje, jak přidružit směrovací tabulku k koncovým bodům služby pomocí chování směrování:</span><span class="sxs-lookup"><span data-stu-id="66202-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="66202-185">Příklad</span><span class="sxs-lookup"><span data-stu-id="66202-185">Example</span></span>  
 <span data-ttu-id="66202-186">Následuje úplný seznam konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="66202-186">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66202-187">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66202-187">See also</span></span>

- [<span data-ttu-id="66202-188">Směrovací služby</span><span class="sxs-lookup"><span data-stu-id="66202-188">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
