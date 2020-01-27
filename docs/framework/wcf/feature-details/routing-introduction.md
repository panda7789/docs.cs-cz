---
title: Směrování – úvod
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 8ce98aab2ed14401fa7c2cbf43eb92a633fa96b0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746463"
---
# <a name="routing-introduction"></a><span data-ttu-id="8f66f-102">Směrování – úvod</span><span class="sxs-lookup"><span data-stu-id="8f66f-102">Routing Introduction</span></span>

<span data-ttu-id="8f66f-103">Směrovací služba poskytuje obecného zprostředkujícího zprostředkovatele SOAP, který dokáže směrovat zprávy na základě obsahu zprávy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-103">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="8f66f-104">Pomocí směrovací služby můžete vytvořit složitou logiku směrování, která vám umožní implementovat scénáře, jako je například agregace služeb, Správa verzí služeb, směrování priorit a směrování vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="8f66f-104">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="8f66f-105">Směrovací služba také poskytuje zpracování chyb, které umožňuje nastavit seznam koncových bodů zálohy, na které se odesílají zprávy, pokud dojde k selhání při posílání do primárního cílového koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-105">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>

<span data-ttu-id="8f66f-106">Toto téma je určené pro nové služby Směrování a pokrývá základní konfiguraci a hostování směrovací služby.</span><span class="sxs-lookup"><span data-stu-id="8f66f-106">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>

## <a name="configuration"></a><span data-ttu-id="8f66f-107">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8f66f-107">Configuration</span></span>

<span data-ttu-id="8f66f-108">Směrovací služba je implementována jako služba WCF, která zveřejňuje jeden nebo více koncových bodů služby, které přijímají zprávy z klientských aplikací a směrují zprávy do jednoho nebo více cílových koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="8f66f-108">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="8f66f-109">Služba poskytuje <xref:System.ServiceModel.Routing.RoutingBehavior>, který se použije pro koncové body služby vystavené službou.</span><span class="sxs-lookup"><span data-stu-id="8f66f-109">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="8f66f-110">Toto chování se používá ke konfiguraci různých aspektů toho, jak služba funguje.</span><span class="sxs-lookup"><span data-stu-id="8f66f-110">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="8f66f-111">Pro usnadnění konfigurace při použití konfiguračního souboru jsou parametry zadány na **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="8f66f-111">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="8f66f-112">Ve scénářích založených na kódu by byly tyto parametry zadány jako součást objektu <xref:System.ServiceModel.Routing.RoutingConfiguration>, který lze následně předat do **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="8f66f-112">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>

<span data-ttu-id="8f66f-113">Při spuštění tento problém přidá <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, který se používá k provádění zpracování protokolu SOAP zpráv, do koncových bodů klienta.</span><span class="sxs-lookup"><span data-stu-id="8f66f-113">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="8f66f-114">Tato možnost umožňuje směrovací službě přenášet zprávy do koncových bodů, které vyžadují jinou **třídu MessageVersion** , než je koncový bod, který byla zpráva přijata.</span><span class="sxs-lookup"><span data-stu-id="8f66f-114">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="8f66f-115">**RoutingBehavior** také zaregistruje rozšíření služby, <xref:System.ServiceModel.Routing.RoutingExtension>, což poskytuje bod přístupnosti pro úpravu konfigurace směrovací služby v době běhu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-115">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>

<span data-ttu-id="8f66f-116">Třída **Konfigurace RoutingConfiguration** poskytuje konzistentní způsob konfigurace a aktualizace konfigurace směrovací služby.</span><span class="sxs-lookup"><span data-stu-id="8f66f-116">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="8f66f-117">Obsahuje parametry, které fungují jako nastavení pro směrovací službu a slouží ke konfiguraci **RoutingBehavior** při spuštění služby, nebo je předána do **RoutingExtension** za účelem změny konfigurace směrování v době běhu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-117">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>

<span data-ttu-id="8f66f-118">Logika směrování, která se používá k provádění směrování zpráv na základě obsahu, je definována seskupením více <xref:System.ServiceModel.Dispatcher.MessageFilter> objektů dohromady do tabulek filtrů (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objektů).</span><span class="sxs-lookup"><span data-stu-id="8f66f-118">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="8f66f-119">Příchozí zprávy jsou vyhodnocovány proti filtrům zpráv obsaženým v tabulce filtru a pro každý **MessageFilter** , který odpovídá zprávě, předané do cílového koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-119">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="8f66f-120">Tabulka filtru, která se má použít ke směrování zpráv, je určena buď pomocí **RoutingBehavior** v konfiguraci, nebo prostřednictvím kódu pomocí objektu **Konfigurace RoutingConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="8f66f-120">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>

### <a name="defining-endpoints"></a><span data-ttu-id="8f66f-121">Definování koncových bodů</span><span class="sxs-lookup"><span data-stu-id="8f66f-121">Defining Endpoints</span></span>

<span data-ttu-id="8f66f-122">I když se může zdát, že byste měli zahájit konfiguraci definováním logiky směrování, kterou použijete, měl by váš první krok být skutečně určující tvar koncových bodů, do kterých budete směrovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-122">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="8f66f-123">Směrovací služba používá kontrakty, které definují tvar kanálů používaných k přijímání a posílání zpráv, a proto musí tvar vstupního kanálu odpovídat výstupnímu kanálu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-123">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="8f66f-124">Pokud například provádíte směrování do koncových bodů, které používají obrazec kanálu požadavek-odpověď, je nutné použít kompatibilní kontrakt na příchozích koncových bodech, například <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span><span class="sxs-lookup"><span data-stu-id="8f66f-124">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>

<span data-ttu-id="8f66f-125">To znamená, že pokud vaše cílové koncové body používají smlouvy s více způsoby komunikace (například kombinováním jednosměrných a obousměrných operací), nemůžete vytvořit jeden koncový bod služby, který může přijímat zprávy a směrovat je na všechny.</span><span class="sxs-lookup"><span data-stu-id="8f66f-125">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="8f66f-126">Je nutné určit, které koncové body mají kompatibilní tvary, a definovat jeden nebo více koncových bodů služby, které budou použity pro příjem zpráv, které mají být směrovány do cílových koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="8f66f-126">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>

> [!NOTE]
> <span data-ttu-id="8f66f-127">Při práci se smlouvami, které určují více vzorů komunikace (například kombinace jednosměrných a obousměrných operací), je alternativním řešením použití duplexního kontraktu ve směrovací službě, jako je například <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span><span class="sxs-lookup"><span data-stu-id="8f66f-127">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="8f66f-128">To však znamená, že vazba musí umožňovat duplexní komunikaci, což nemusí být možné pro všechny scénáře.</span><span class="sxs-lookup"><span data-stu-id="8f66f-128">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="8f66f-129">V případech, kdy to není možné, může být komunikace na více koncových bodech nebo v případě změny aplikace nutná.</span><span class="sxs-lookup"><span data-stu-id="8f66f-129">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>

<span data-ttu-id="8f66f-130">Další informace o kontraktech směrování najdete v tématu [kontrakty směrování](routing-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="8f66f-130">For more information about routing contracts, see [Routing Contracts](routing-contracts.md).</span></span>

<span data-ttu-id="8f66f-131">Po definování koncového bodu služby můžete pomocí **RoutingBehavior** přidružit ke koncovému bodu konkrétní **Konfigurace RoutingConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="8f66f-131">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="8f66f-132">Při konfiguraci směrovací služby pomocí konfiguračního souboru **RoutingBehavior** slouží k určení tabulky filtru, která obsahuje logiku směrování používanou ke zpracování zpráv přijatých v tomto koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="8f66f-132">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="8f66f-133">Pokud konfigurujete směrovací službu programově, můžete zadat tabulku filtru pomocí **Konfigurace RoutingConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="8f66f-133">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>

<span data-ttu-id="8f66f-134">Následující příklad definuje koncové body služby a klienta, které služba Směrování používá programově a pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="8f66f-134">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>

```xml
<services>
  <!--ROUTING SERVICE -->
  <service behaviorConfiguration="routingData"
            name="System.ServiceModel.Routing.RoutingService">
    <host>
      <baseAddresses>
        <add baseAddress="http://localhost:8000/routingservice/router"/>
      </baseAddresses>
    </host>
    <!-- Define the service endpoints that are receive messages -->
    <endpoint address=""
              binding="wsHttpBinding"
              name="reqReplyEndpoint"
              contract="System.ServiceModel.Routing.IRequestReplyRouter" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="routingData">
      <serviceMetadata httpGetEnabled="True"/>
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->
      <routing filterTableName="routingTable1" />
    </behavior>
  </serviceBehaviors>
</behaviors>
<client>
<!-- Define the client endpoint(s) to route messages to -->
  <endpoint name="CalculatorService"
            address="http://localhost:8000/servicemodelsamples/service"
            binding="wsHttpBinding" contract="*" />
</client>
```

```csharp
//set up some communication defaults
string clientAddress = "http://localhost:8000/servicemodelsamples/service";
string routerAddress = "http://localhost:8000/routingservice/router";
Binding routerBinding = new WSHttpBinding();
Binding clientBinding = new WSHttpBinding();
//add the endpoint the router uses to receive messages
serviceHost.AddServiceEndpoint(
     typeof(IRequestReplyRouter),
     routerBinding,
     routerAddress);
//create the client endpoint the router routes messages to
ContractDescription contract = ContractDescription.GetContract(
     typeof(IRequestReplyRouter));
ServiceEndpoint client = new ServiceEndpoint(
     contract,
     clientBinding,
     new EndpointAddress(clientAddress));
//create a new routing configuration object
RoutingConfiguration rc = new RoutingConfiguration();
….
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
//attach the behavior to the service host
serviceHost.Description.Behaviors.Add(
     new RoutingBehavior(rc));
```

<span data-ttu-id="8f66f-135">Tento příklad nakonfiguruje směrovací službu tak, aby zveřejnila jediný koncový bod s adresou `http://localhost:8000/routingservice/router`, která se používá k přijímání zpráv, které se mají směrovat.</span><span class="sxs-lookup"><span data-stu-id="8f66f-135">This example configures the Routing Service to expose a single endpoint with an address of `http://localhost:8000/routingservice/router`, which is used to receive messages to be routed.</span></span> <span data-ttu-id="8f66f-136">Vzhledem k tomu, že se zprávy směrují do koncových bodů požadavek-odpověď, koncový bod služby používá kontrakt <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span><span class="sxs-lookup"><span data-stu-id="8f66f-136">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="8f66f-137">Tato konfigurace také definuje jeden koncový bod klienta `http://localhost:8000/servicemodelsample/service`, na který jsou zprávy směrovány.</span><span class="sxs-lookup"><span data-stu-id="8f66f-137">This configuration also defines a single client endpoint of `http://localhost:8000/servicemodelsample/service` that messages are routed to.</span></span> <span data-ttu-id="8f66f-138">Tabulka filtru (není zobrazená) s názvem "routingTable1" obsahuje logiku směrování používanou ke směrování zpráv a je přidružená k koncovému bodu služby pomocí **RoutingBehavior** (pro konfigurační soubor) nebo **Konfigurace RoutingConfiguration** (pro programovou konfiguraci).</span><span class="sxs-lookup"><span data-stu-id="8f66f-138">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>

### <a name="routing-logic"></a><span data-ttu-id="8f66f-139">Logika směrování</span><span class="sxs-lookup"><span data-stu-id="8f66f-139">Routing Logic</span></span>

<span data-ttu-id="8f66f-140">Pro definování logiky směrování, která se používá ke směrování zpráv, je nutné určit, která data obsažená v příchozích zprávách se mají jedinečně zpracovávat.</span><span class="sxs-lookup"><span data-stu-id="8f66f-140">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="8f66f-141">Pokud například všechny cílové koncové body, které chcete směrovat, sdílí stejné akce SOAP, hodnota akce obsažená ve zprávě není dobrý indikátor, na který konkrétní koncový bod má být zpráva směrována.</span><span class="sxs-lookup"><span data-stu-id="8f66f-141">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="8f66f-142">Pokud je nutné zprávy jednoznačně směrovat do jednoho konkrétního koncového bodu, měli byste filtrovat data, která jednoznačně identifikují cílový koncový bod, na který je zpráva směrována.</span><span class="sxs-lookup"><span data-stu-id="8f66f-142">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>

<span data-ttu-id="8f66f-143">Směrovací služba poskytuje několik implementací **MessageFilter** , které kontrolují konkrétní hodnoty v rámci zprávy, jako je adresa, akce, název koncového bodu nebo dokonce dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="8f66f-143">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="8f66f-144">Pokud žádná z těchto implementací nevyhovuje vašim potřebám, můžete vytvořit vlastní **MessageFilter** implementaci.</span><span class="sxs-lookup"><span data-stu-id="8f66f-144">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="8f66f-145">Další informace o filtrech zpráv a porovnání implementací používaných směrovací službou najdete v tématu [filtry zpráv](message-filters.md) a [Výběr filtru](choosing-a-filter.md).</span><span class="sxs-lookup"><span data-stu-id="8f66f-145">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](message-filters.md) and [Choosing a Filter](choosing-a-filter.md).</span></span>

<span data-ttu-id="8f66f-146">Více filtrů zpráv je uspořádáno společně do tabulek filtrů, které přiřadí jednotlivé **MessageFilter** k cílovému koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-146">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="8f66f-147">V případě potřeby můžete také použít tabulku filtru k určení seznamu záložních koncových bodů, ke kterým se služba Směrování pokusí odeslat zprávu v případě selhání přenosu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-147">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>

<span data-ttu-id="8f66f-148">Ve výchozím nastavení jsou všechny filtry zpráv v tabulce filtru vyhodnocovány současně. Můžete však zadat <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A>, který způsobí vyhodnocení filtru zprávy v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="8f66f-148">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="8f66f-149">Nejprve se vyhodnotí všechny položky s nejvyšší prioritou a filtry zpráv s nižšími prioritami se nevyhodnotí, pokud se shoda najde na vyšší úrovni priority.</span><span class="sxs-lookup"><span data-stu-id="8f66f-149">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="8f66f-150">Další informace o tabulkách filtru najdete v tématu [filtry zpráv](message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="8f66f-150">For more information about filter tables, see [Message Filters](message-filters.md).</span></span>

<span data-ttu-id="8f66f-151">V následujících příkladech je použit <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, který se vyhodnotí jako `true` pro všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-151">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="8f66f-152">Tento **MessageFilter** se přidá do tabulky filtru "routingTable1", která přidružuje **MessageFilter** k koncovému bodu klienta s názvem "CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="8f66f-152">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="8f66f-153">**RoutingBehavior** pak určí, že se má tato tabulka používat ke směrování zpráv zpracovávaných koncovým bodem služby.</span><span class="sxs-lookup"><span data-stu-id="8f66f-153">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="routingData">
      <serviceMetadata httpGetEnabled="True"/>
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->
      <routing filterTableName="routingTable1" />
    </behavior>
  </serviceBehaviors>
</behaviors>
<!--ROUTING SECTION -->
<routing>
  <filters>
    <filter name="MatchAllFilter1" filterType="MatchAll" />
  </filters>
  <filterTables>
    <table name="routingTable1">
      <filters>
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />
      </filters>
    </table>
  </filterTables>
</routing>
```

```csharp
//create a new routing configuration object
RoutingConfiguration rc = new RoutingConfiguration();
//create the endpoint list that contains the endpoints to route to
//in this case we have only one
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();
endpointList.Add(client);
//add a MatchAll filter to the Router's filter table
//map it to the endpoint list defined earlier
//when a message matches this filter, it is sent to the endpoint contained in the list
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
```

> [!NOTE]
> <span data-ttu-id="8f66f-154">Ve výchozím nastavení služba Směrování vyhodnocuje pouze záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-154">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="8f66f-155">Chcete-li povoleným filtrům přístup k textu zprávy, je nutné nastavit <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> na `false`.</span><span class="sxs-lookup"><span data-stu-id="8f66f-155">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>

<span data-ttu-id="8f66f-156">**Odesílání**</span><span class="sxs-lookup"><span data-stu-id="8f66f-156">**Multicast**</span></span>

<span data-ttu-id="8f66f-157">I když řada konfigurací směrovací služby používá výhradní logiku filtru, která směruje zprávy pouze na jeden konkrétní koncový bod, může být nutné směrovat danou zprávu na více cílových koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="8f66f-157">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="8f66f-158">Pro vícesměrové vysílání zprávy na více cílů musí platit následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="8f66f-158">To multicast a message to multiple destinations, the following conditions must be true:</span></span>

- <span data-ttu-id="8f66f-159">Obrazec kanálu nesmí být Request-response (přestože může být jednosměrný nebo duplexní), protože klientská aplikace může v reakci na požadavek přijmout jenom jednu odpověď.</span><span class="sxs-lookup"><span data-stu-id="8f66f-159">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>

- <span data-ttu-id="8f66f-160">Při vyhodnocování zprávy musí `true` vracet více filtrů.</span><span class="sxs-lookup"><span data-stu-id="8f66f-160">Multiple filters must return `true` when evaluating the message.</span></span>

<span data-ttu-id="8f66f-161">Pokud jsou tyto podmínky splněny, zpráva bude směrována do všech koncových bodů všech filtrů, které jsou vyhodnoceny jako `true`.</span><span class="sxs-lookup"><span data-stu-id="8f66f-161">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="8f66f-162">Následující příklad definuje konfiguraci směrování, která má za následek směrování zpráv do obou koncových bodů, pokud je adresa koncového bodu ve zprávě `http://localhost:8000/routingservice/router/rounding`.</span><span class="sxs-lookup"><span data-stu-id="8f66f-162">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is `http://localhost:8000/routingservice/router/rounding`.</span></span>

```xml
<!--ROUTING SECTION -->
<routing>
  <filters>
    <filter name="MatchAllFilter1" filterType="MatchAll" />
    <filter name="RoundingFilter1" filterType="EndpointAddress"
            filterData="http://localhost:8000/routingservice/router/rounding" />
  </filters>
  <filterTables>
    <table name="routingTable1">
      <filters>
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />
      </filters>
    </table>
  </filterTables>
</routing>
```

```csharp
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(
    "http://localhost:8000/routingservice/router/rounding")),
    roundingCalcEndpointList);
```

### <a name="soap-processing"></a><span data-ttu-id="8f66f-163">Zpracování SOAP</span><span class="sxs-lookup"><span data-stu-id="8f66f-163">SOAP Processing</span></span>

<span data-ttu-id="8f66f-164">Aby bylo možné podporovat směrování zpráv mezi odlišnými protokoly, **RoutingBehavior** ve výchozím nastavení přidá <xref:System.ServiceModel.Routing.SoapProcessingBehavior> do všech koncových bodů klienta, na které jsou zprávy směrovány.</span><span class="sxs-lookup"><span data-stu-id="8f66f-164">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="8f66f-165">Toto chování automaticky vytvoří novou **třídu MessageVersion** před směrováním zprávy do koncového bodu, stejně jako vytvoření kompatibilního souboru **MessageVersion** pro libovolný dokument odpovědi před jeho vrácením do žádající klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="8f66f-165">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>

<span data-ttu-id="8f66f-166">Kroky pro vytvoření nové sady **MessageVersion** pro odchozí zprávy jsou následující:</span><span class="sxs-lookup"><span data-stu-id="8f66f-166">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>

<span data-ttu-id="8f66f-167">**Zpracování žádosti**</span><span class="sxs-lookup"><span data-stu-id="8f66f-167">**Request processing**</span></span>

- <span data-ttu-id="8f66f-168">Získejte **třídu MessageVersion** odchozí vazby nebo kanálu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-168">Get the **MessageVersion** of the outbound binding/channel.</span></span>

- <span data-ttu-id="8f66f-169">Získá čtečku textu pro původní zprávu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-169">Get the body reader for the original message.</span></span>

- <span data-ttu-id="8f66f-170">Vytvoří novou zprávu se stejnou akcí, čtečkou textu a novou **verzí MessageVersion**.</span><span class="sxs-lookup"><span data-stu-id="8f66f-170">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>

- <span data-ttu-id="8f66f-171">Pokud <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>! = **Addressing. None**, zkopírujte do nové zprávy záhlaví do, z, FaultTo a RelatesTo.</span><span class="sxs-lookup"><span data-stu-id="8f66f-171">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>

- <span data-ttu-id="8f66f-172">Kopírovat všechny vlastnosti zprávy do nové zprávy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-172">Copy all message properties to the new message.</span></span>

- <span data-ttu-id="8f66f-173">Uloží původní zprávu požadavku, která se má použít při zpracování odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8f66f-173">Store the original request message to use when processing the response.</span></span>

- <span data-ttu-id="8f66f-174">Vrátí novou zprávu požadavku.</span><span class="sxs-lookup"><span data-stu-id="8f66f-174">Return the new request message.</span></span>

<span data-ttu-id="8f66f-175">**Zpracování odpovědí**</span><span class="sxs-lookup"><span data-stu-id="8f66f-175">**Response processing**</span></span>

- <span data-ttu-id="8f66f-176">Získejte **třídu MessageVersion** původní zprávy s požadavkem.</span><span class="sxs-lookup"><span data-stu-id="8f66f-176">Get the **MessageVersion** of the original request message.</span></span>

- <span data-ttu-id="8f66f-177">Získejte čtečku textu pro přijatou zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8f66f-177">Get the body reader for the received response message.</span></span>

- <span data-ttu-id="8f66f-178">Vytvoří novou zprávu odpovědi se stejnou akcí, čtečkou textu a **verzí** původní zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="8f66f-178">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>

- <span data-ttu-id="8f66f-179">Pokud <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>! = **Addressing. None**, zkopírujte do nové zprávy záhlaví do, z, FaultTo a RelatesTo.</span><span class="sxs-lookup"><span data-stu-id="8f66f-179">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>

- <span data-ttu-id="8f66f-180">Zkopírujte vlastnosti zprávy do nové zprávy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-180">Copy the message properties to the new message.</span></span>

- <span data-ttu-id="8f66f-181">Vrátí novou zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8f66f-181">Return the new response message.</span></span>

<span data-ttu-id="8f66f-182">Ve výchozím nastavení je **SoapProcessingBehavior** automaticky přidán do koncových bodů klienta <xref:System.ServiceModel.Routing.RoutingBehavior> při spuštění služby; Můžete však určit, zda bude zpracování protokolu SOAP přidáno do všech koncových bodů klienta pomocí vlastnosti <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="8f66f-182">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="8f66f-183">Můžete také přidat chování přímo do konkrétního koncového bodu a povolit nebo zakázat toto chování na úrovni koncového bodu, pokud je potřeba podrobnější řízení zpracování protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8f66f-183">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>

> [!NOTE]
> <span data-ttu-id="8f66f-184">Je-li zpracování protokolu SOAP zakázáno pro koncový bod, který vyžaduje jinou třídu MessageVersion než původní zpráva požadavku, je nutné zadat vlastní mechanismus pro provedení všech úprav protokolu SOAP, které jsou požadovány před odesláním zprávy do cílový koncový bod.</span><span class="sxs-lookup"><span data-stu-id="8f66f-184">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>

<span data-ttu-id="8f66f-185">V následujících příkladech slouží vlastnost **soapProcessingEnabled** k tomu, aby se zabránilo automatickému přidání **SoapProcessingBehavior** do všech koncových bodů klienta.</span><span class="sxs-lookup"><span data-stu-id="8f66f-185">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>

```xml
<behaviors>
  <!--default routing service behavior definition-->
  <serviceBehaviors>
    <behavior name="routingConfiguration">
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

```csharp
//create the default RoutingConfiguration
RoutingConfiguration rc = new RoutingConfiguration();
rc.SoapProcessingEnabled = false;
```

### <a name="dynamic-configuration"></a><span data-ttu-id="8f66f-186">Dynamická konfigurace</span><span class="sxs-lookup"><span data-stu-id="8f66f-186">Dynamic Configuration</span></span>

<span data-ttu-id="8f66f-187">Když přidáte další koncové body klienta nebo potřebujete upravit filtry, které se používají ke směrování zpráv, musíte mít způsob, jak dynamicky aktualizovat konfiguraci v době běhu, aby se zabránilo přerušení služby pro koncové body, které aktuálně přijímají zprávy. Směrovací služba.</span><span class="sxs-lookup"><span data-stu-id="8f66f-187">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="8f66f-188">Změna konfiguračního souboru nebo kódu hostitelské aplikace není vždy dostatečná, protože kterákoli z metod vyžaduje recyklace aplikace, což by vedlo k potenciální ztrátě všech zpráv, které jsou právě přenášeny, a potenciální výpadek při čeká se na restartování služby.</span><span class="sxs-lookup"><span data-stu-id="8f66f-188">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>

<span data-ttu-id="8f66f-189">**Konfigurace RoutingConfiguration** můžete změnit jenom programově.</span><span class="sxs-lookup"><span data-stu-id="8f66f-189">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="8f66f-190">I když můžete službu zpočátku konfigurovat pomocí konfiguračního souboru, můžete změnit jenom konfiguraci za běhu, a to tak, že vytvoříte novou **Konfigurace RoutingConfiguration** a předáte ji jako parametr metodě <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> vystavené rozšířením služby <xref:System.ServiceModel.Routing.RoutingExtension>.</span><span class="sxs-lookup"><span data-stu-id="8f66f-190">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfiguration** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="8f66f-191">Všechny zprávy, které jsou aktuálně ve přenosu, se budou směrovat pomocí předchozí konfigurace, zatímco zprávy přijaté po volání **ApplyConfiguration** používají novou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="8f66f-191">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="8f66f-192">Následující příklad ukazuje vytvoření instance směrovací služby a následné úpravě konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8f66f-192">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>

```csharp
RoutingConfiguration routingConfig = new RoutingConfiguration();
routingConfig.RouteOnHeadersOnly = true;
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
RoutingBehavior routing = new RoutingBehavior(routingConfig);
routerHost.Description.Behaviors.Add(routing);
routerHost.Open();
// Construct a new RoutingConfiguration
RoutingConfiguration rc2 = new RoutingConfiguration();
ServiceEndpoint clientEndpoint = new ServiceEndpoint();
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();
// Add filters to the FilterTable in the new configuration
rc2.FilterTable.add(new MatchAllMessageFilter(),
       new List<ServiceEndpoint>() { clientEndpoint });
rc2.FilterTable.add(new MatchAllMessageFilter(),
       new List<ServiceEndpoint>() { clientEndpoint2 });
rc2.RouteOnHeadersOnly = false;
// Apply the new configuration to the Routing Service hosted in
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);
```

> [!NOTE]
> <span data-ttu-id="8f66f-193">Při aktualizaci směrovací služby tímto způsobem je možné předat pouze novou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="8f66f-193">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="8f66f-194">Není možné upravovat pouze vybrané prvky aktuální konfigurace nebo připojit nové položky k aktuální konfiguraci; musíte vytvořit a předat novou konfiguraci, která nahradí stávající.</span><span class="sxs-lookup"><span data-stu-id="8f66f-194">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>

> [!NOTE]
> <span data-ttu-id="8f66f-195">Všechny relace otevřené pomocí předchozí konfigurace pokračují v předchozí konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="8f66f-195">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="8f66f-196">Nová konfigurace je používána pouze novými relacemi.</span><span class="sxs-lookup"><span data-stu-id="8f66f-196">The new configuration is only used by new sessions.</span></span>

## <a name="error-handling"></a><span data-ttu-id="8f66f-197">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="8f66f-197">Error Handling</span></span>

<span data-ttu-id="8f66f-198">Pokud při pokusu o odeslání zprávy dojde k nějaké <xref:System.ServiceModel.CommunicationException>, probíhá zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="8f66f-198">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="8f66f-199">Tyto výjimky obvykle označují, že došlo k potížím při pokusu o komunikaci s definovaným koncovým bodem klienta, například <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>nebo <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="8f66f-199">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="8f66f-200">Zpracování chyb – kód bude také zachytit a pokusit se o opakované odeslání, když dojde k <xref:System.TimeoutException>, což je další běžná výjimka, která není odvozena od **CommunicationException**.</span><span class="sxs-lookup"><span data-stu-id="8f66f-200">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>

<span data-ttu-id="8f66f-201">Pokud dojde k jedné z předchozích výjimek, směrovací služba převezme seznam koncových bodů zálohy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-201">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="8f66f-202">Pokud se všechny koncové body zálohování nezdaří s chybou komunikace, nebo pokud koncový bod vrátí výjimku, která označuje chybu v cílové službě, služba Směrování vrátí chybu klientské aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8f66f-202">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>

> [!NOTE]
> <span data-ttu-id="8f66f-203">Funkce zpracování chyb zachytí a zpracovává výjimky, ke kterým dochází při pokusu o odeslání zprávy a při pokusu o zavření kanálu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-203">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="8f66f-204">Kód pro zpracování chyb není určen k detekci nebo zpracování výjimek vytvořených koncovými body aplikace, se kterými komunikuje. <xref:System.ServiceModel.FaultException>, který vyvolala služba, se ve směrovací službě zobrazí jako **FaultMessage** a přesměruje se na klienta.</span><span class="sxs-lookup"><span data-stu-id="8f66f-204">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>
>
> <span data-ttu-id="8f66f-205">Pokud dojde k chybě, když se směrovací služba pokusí o předání zprávy, můžete získat <xref:System.ServiceModel.FaultException> na straně klienta, a ne <xref:System.ServiceModel.EndpointNotFoundException>, který byste normálně získali při absenci služby směrování.</span><span class="sxs-lookup"><span data-stu-id="8f66f-205">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="8f66f-206">Směrovací služba může proto maskovat výjimky a neposkytuje úplnou transparentnost, Pokud neprojdete vnořené výjimky.</span><span class="sxs-lookup"><span data-stu-id="8f66f-206">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>

### <a name="tracing-exceptions"></a><span data-ttu-id="8f66f-207">Trasování výjimek</span><span class="sxs-lookup"><span data-stu-id="8f66f-207">Tracing Exceptions</span></span>

<span data-ttu-id="8f66f-208">Při odeslání zprávy do koncového bodu v seznamu se služba Směrování vysleduje výsledná data výjimky a připojí podrobnosti o výjimce jako vlastnost zprávy s názvem **výjimky**.</span><span class="sxs-lookup"><span data-stu-id="8f66f-208">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="8f66f-209">Tím se zachová data výjimky a umožní uživatelům programový přístup prostřednictvím kontroly zpráv.</span><span class="sxs-lookup"><span data-stu-id="8f66f-209">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="8f66f-210">Data výjimky jsou uložena na jednu zprávu ve slovníku, který mapuje název koncového bodu na podrobnosti výjimky zjištěné při pokusu o odeslání zprávy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-210">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>

### <a name="backup-endpoints"></a><span data-ttu-id="8f66f-211">Koncové body zálohování</span><span class="sxs-lookup"><span data-stu-id="8f66f-211">Backup Endpoints</span></span>

<span data-ttu-id="8f66f-212">Každá položka filtru v tabulce filtru může volitelně určovat seznam koncových bodů zálohy, které se používají v případě selhání přenosu při odesílání do primárního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-212">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="8f66f-213">Pokud dojde k selhání, služba Směrování se pokusí zprávu přenést do první položky v seznamu koncových bodů zálohy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-213">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="8f66f-214">Pokud se tento pokus o odeslání narazí i na selhání přenosu, pokusí se další koncový bod v seznamu zálohování.</span><span class="sxs-lookup"><span data-stu-id="8f66f-214">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="8f66f-215">Směrovací služba pokračuje v posílání zpráv do každého koncového bodu v seznamu, dokud se zpráva úspěšně nepřijme, všechny koncové body vrátí selhání přenosu, nebo koncový bod vrátí selhání bez přenosu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-215">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>

<span data-ttu-id="8f66f-216">Následující příklady nakonfigurují směrovací službu tak, aby používala seznam zálohování.</span><span class="sxs-lookup"><span data-stu-id="8f66f-216">The following examples configure the Routing Service to use a backup list.</span></span>

```xml
<routing>
  <filters>
    <!-- Create a MatchAll filter that catches all messages -->
    <filter name="MatchAllFilter1" filterType="MatchAll" />
  </filters>
  <filterTables>
    <!-- Set up the Routing Service's Message Filter Table -->
    <filterTable name="filterTable1">
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
        <!-- Listed in the backupEndpointList -->
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
    </filterTable>
  </filterTables>
  <!-- Create the backup endpoint list -->
  <backupLists>
    <!-- Add an endpoint list that contains the backup destinations -->
    <backupList name="backupEndpointList">
      <add endpointName="realDestination" />
      <add endpointName="backupDestination" />
    </backupList>
  </backupLists>
</routing>
```

```csharp
//create the endpoint list that contains the service endpoints we want to route to
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();
//add the endpoints in the order that the Routing Service should contact them
//first add the endpoint that we know is down
//clearly, normally you wouldn't know that this endpoint was down by default
backupList.Add(fakeDestination);
//then add the real Destination endpoint
//the Routing Service attempts to send to this endpoint only if it
//encounters a TimeOutException or CommunicationException when sending
//to the previous endpoint in the list.
backupList.Add(realDestination);
//add the backupDestination endpoint
//the Routing Service attempts to send to this endpoint only if it
//encounters a TimeOutException or CommunicationsException when sending
//to the previous endpoints in the list
backupList.Add(backupDestination);
//create the default RoutingConfiguration option
RoutingConfiguration rc = new RoutingConfiguration();
//add a MatchAll filter to the Routing Configuration's filter table
//map it to the list of endpoints defined above
//when a message matches this filter, it is sent to the endpoints in the list in order
//if an endpoint is down or does not respond (which the first endpoint won't
//since the client does not exist), the Routing Service automatically moves the message
//to the next endpoint in the list and try again.
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);
```

### <a name="supported-error-patterns"></a><span data-ttu-id="8f66f-217">Podporované vzorce chyb</span><span class="sxs-lookup"><span data-stu-id="8f66f-217">Supported Error Patterns</span></span>

<span data-ttu-id="8f66f-218">Následující tabulka popisuje vzory, které jsou kompatibilní s používáním seznamů záložních koncových bodů, spolu s poznámkami popisujícími podrobnosti zpracování chyb pro konkrétní vzory.</span><span class="sxs-lookup"><span data-stu-id="8f66f-218">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>

|<span data-ttu-id="8f66f-219">Vzor</span><span class="sxs-lookup"><span data-stu-id="8f66f-219">Pattern</span></span>|<span data-ttu-id="8f66f-220">Relace</span><span class="sxs-lookup"><span data-stu-id="8f66f-220">Session</span></span>|<span data-ttu-id="8f66f-221">Transakce</span><span class="sxs-lookup"><span data-stu-id="8f66f-221">Transaction</span></span>|<span data-ttu-id="8f66f-222">Kontext příjmu</span><span class="sxs-lookup"><span data-stu-id="8f66f-222">Receive Context</span></span>|<span data-ttu-id="8f66f-223">Seznam zálohování je podporovaný.</span><span class="sxs-lookup"><span data-stu-id="8f66f-223">Backup List Supported</span></span>|<span data-ttu-id="8f66f-224">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f66f-224">Notes</span></span>|
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|
|<span data-ttu-id="8f66f-225">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="8f66f-225">One-Way</span></span>||||<span data-ttu-id="8f66f-226">Ano</span><span class="sxs-lookup"><span data-stu-id="8f66f-226">Yes</span></span>|<span data-ttu-id="8f66f-227">Pokusí se znovu odeslat zprávu na koncový bod zálohy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-227">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="8f66f-228">Pokud je tato zpráva vícesměrové vysílání, do svého cílového umístění zálohy se přesune jenom zpráva v neúspěšném kanálu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-228">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|
|<span data-ttu-id="8f66f-229">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="8f66f-229">One-Way</span></span>||<span data-ttu-id="8f66f-230">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-230">✔️</span></span>||<span data-ttu-id="8f66f-231">Ne</span><span class="sxs-lookup"><span data-stu-id="8f66f-231">No</span></span>|<span data-ttu-id="8f66f-232">Je vyvolána výjimka a transakce je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="8f66f-232">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="8f66f-233">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="8f66f-233">One-Way</span></span>|||<span data-ttu-id="8f66f-234">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-234">✔️</span></span>|<span data-ttu-id="8f66f-235">Ano</span><span class="sxs-lookup"><span data-stu-id="8f66f-235">Yes</span></span>|<span data-ttu-id="8f66f-236">Pokusí se znovu odeslat zprávu na koncový bod zálohy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-236">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="8f66f-237">Po úspěšném přijetí zprávy dokončete všechny kontexty příjmu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-237">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="8f66f-238">Pokud není zpráva úspěšně přijata žádným koncovým bodem, neprovádějte kontext Receive.</span><span class="sxs-lookup"><span data-stu-id="8f66f-238">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="8f66f-239">Při vícesměrovém vysílání této zprávy je kontext příjmu dokončen pouze v případě, že zpráva byla úspěšně přijata alespoň jedním koncovým bodem (primárním nebo záložním).</span><span class="sxs-lookup"><span data-stu-id="8f66f-239">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="8f66f-240">Pokud žádný z koncových bodů v žádné ze všech cest vícesměrového vysílání úspěšně neobdrží zprávu, neprovádějte kontext Receive.</span><span class="sxs-lookup"><span data-stu-id="8f66f-240">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|
|<span data-ttu-id="8f66f-241">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="8f66f-241">One-Way</span></span>||<span data-ttu-id="8f66f-242">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-242">✔️</span></span>|<span data-ttu-id="8f66f-243">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-243">✔️</span></span>|<span data-ttu-id="8f66f-244">Ano</span><span class="sxs-lookup"><span data-stu-id="8f66f-244">Yes</span></span>|<span data-ttu-id="8f66f-245">Přerušit předchozí transakci, vytvořit novou transakci a znovu odeslat všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-245">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="8f66f-246">Zprávy, u kterých došlo k chybě, se přenáší do cílového umístění zálohy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-246">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="8f66f-247">Po vytvoření transakce, ve které jsou všechny přenosy úspěšné, dokončete kontext příjmu a potvrďte transakci.</span><span class="sxs-lookup"><span data-stu-id="8f66f-247">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|
|<span data-ttu-id="8f66f-248">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="8f66f-248">One-Way</span></span>|<span data-ttu-id="8f66f-249">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-249">✔️</span></span>|||<span data-ttu-id="8f66f-250">Ano</span><span class="sxs-lookup"><span data-stu-id="8f66f-250">Yes</span></span>|<span data-ttu-id="8f66f-251">Pokusí se znovu odeslat zprávu na koncový bod zálohy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-251">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="8f66f-252">Ve scénáři vícesměrového vysílání se v rámci zálohování znovu přemístí pouze zprávy v relaci, u kterých došlo k chybě, nebo v relaci, jejichž zavření relace se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="8f66f-252">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|
|<span data-ttu-id="8f66f-253">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="8f66f-253">One-Way</span></span>|<span data-ttu-id="8f66f-254">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-254">✔️</span></span>|<span data-ttu-id="8f66f-255">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-255">✔️</span></span>||<span data-ttu-id="8f66f-256">Ne</span><span class="sxs-lookup"><span data-stu-id="8f66f-256">No</span></span>|<span data-ttu-id="8f66f-257">Je vyvolána výjimka a transakce je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="8f66f-257">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="8f66f-258">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="8f66f-258">One-Way</span></span>|<span data-ttu-id="8f66f-259">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-259">✔️</span></span>||<span data-ttu-id="8f66f-260">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-260">✔️</span></span>|<span data-ttu-id="8f66f-261">Ano</span><span class="sxs-lookup"><span data-stu-id="8f66f-261">Yes</span></span>|<span data-ttu-id="8f66f-262">Pokusí se znovu odeslat zprávu na koncový bod zálohy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-262">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="8f66f-263">Jakmile se všechna zpráva pošle bez chyby, relace indikuje žádné další zprávy a směrovací služba úspěšně zavřela všechny kanály odchozích relací, všechny kontexty příjmu jsou dokončeny a kanál příchozí relace je uzavřený.</span><span class="sxs-lookup"><span data-stu-id="8f66f-263">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|
|<span data-ttu-id="8f66f-264">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="8f66f-264">One-Way</span></span>|<span data-ttu-id="8f66f-265">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-265">✔️</span></span>|<span data-ttu-id="8f66f-266">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-266">✔️</span></span>|<span data-ttu-id="8f66f-267">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-267">✔️</span></span>|<span data-ttu-id="8f66f-268">Ano</span><span class="sxs-lookup"><span data-stu-id="8f66f-268">Yes</span></span>|<span data-ttu-id="8f66f-269">Přeruší aktuální transakci a vytvoří novou.</span><span class="sxs-lookup"><span data-stu-id="8f66f-269">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="8f66f-270">Znovu odešle všechny předchozí zprávy v relaci.</span><span class="sxs-lookup"><span data-stu-id="8f66f-270">Resend all previous messages in the session.</span></span> <span data-ttu-id="8f66f-271">Po vytvoření transakce, ve které byly všechny zprávy úspěšně odeslány a relace indikuje žádné další zprávy, jsou všechny kanály odchozích relací uzavřeny, jsou všechny kontexty příjmu dokončeny s transakcí, kanál příchozí relace je uzavřeno a transakce je potvrzena.</span><span class="sxs-lookup"><span data-stu-id="8f66f-271">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="8f66f-272">Když jsou relace vícesměrové vysílání, zprávy, u kterých došlo k chybě, se odešlou do stejného cílového umístění jako předtím a zprávy, které se objevily, se odesílají do cílů zálohování.</span><span class="sxs-lookup"><span data-stu-id="8f66f-272">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|
|<span data-ttu-id="8f66f-273">Obousměrný postup</span><span class="sxs-lookup"><span data-stu-id="8f66f-273">Two-Way</span></span>||||<span data-ttu-id="8f66f-274">Ano</span><span class="sxs-lookup"><span data-stu-id="8f66f-274">Yes</span></span>|<span data-ttu-id="8f66f-275">Odeslat do cílového umístění zálohy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-275">Send to a backup destination.</span></span>  <span data-ttu-id="8f66f-276">Až kanál vrátí zprávu odpovědi, vrátí odpověď původnímu klientovi.</span><span class="sxs-lookup"><span data-stu-id="8f66f-276">After a channel returns a response message, return the response to the original client.</span></span>|
|<span data-ttu-id="8f66f-277">Obousměrný postup</span><span class="sxs-lookup"><span data-stu-id="8f66f-277">Two-Way</span></span>|<span data-ttu-id="8f66f-278">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-278">✔️</span></span>|||<span data-ttu-id="8f66f-279">Ano</span><span class="sxs-lookup"><span data-stu-id="8f66f-279">Yes</span></span>|<span data-ttu-id="8f66f-280">Odeslat všechny zprávy na kanálu do cílového umístění zálohy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-280">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="8f66f-281">Až kanál vrátí zprávu odpovědi, vrátí odpověď původnímu klientovi.</span><span class="sxs-lookup"><span data-stu-id="8f66f-281">After a channel returns a response message, return the response to the original client.</span></span>|
|<span data-ttu-id="8f66f-282">Obousměrný postup</span><span class="sxs-lookup"><span data-stu-id="8f66f-282">Two-Way</span></span>||<span data-ttu-id="8f66f-283">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-283">✔️</span></span>||<span data-ttu-id="8f66f-284">Ne</span><span class="sxs-lookup"><span data-stu-id="8f66f-284">No</span></span>|<span data-ttu-id="8f66f-285">Je vyvolána výjimka a transakce je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="8f66f-285">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="8f66f-286">Obousměrný postup</span><span class="sxs-lookup"><span data-stu-id="8f66f-286">Two-Way</span></span>|<span data-ttu-id="8f66f-287">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-287">✔️</span></span>|<span data-ttu-id="8f66f-288">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-288">✔️</span></span>||<span data-ttu-id="8f66f-289">Ne</span><span class="sxs-lookup"><span data-stu-id="8f66f-289">No</span></span>|<span data-ttu-id="8f66f-290">Je vyvolána výjimka a transakce je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="8f66f-290">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="8f66f-291">Duplex</span><span class="sxs-lookup"><span data-stu-id="8f66f-291">Duplex</span></span>||||<span data-ttu-id="8f66f-292">Ne</span><span class="sxs-lookup"><span data-stu-id="8f66f-292">No</span></span>|<span data-ttu-id="8f66f-293">Komunikace bez relací není v současné době podporovaná.</span><span class="sxs-lookup"><span data-stu-id="8f66f-293">Non-session duplex communication is not currently supported.</span></span>|
|<span data-ttu-id="8f66f-294">Duplex</span><span class="sxs-lookup"><span data-stu-id="8f66f-294">Duplex</span></span>|<span data-ttu-id="8f66f-295">✔️</span><span class="sxs-lookup"><span data-stu-id="8f66f-295">✔️</span></span>|||<span data-ttu-id="8f66f-296">Ano</span><span class="sxs-lookup"><span data-stu-id="8f66f-296">Yes</span></span>|<span data-ttu-id="8f66f-297">Odeslat do cílového umístění zálohy.</span><span class="sxs-lookup"><span data-stu-id="8f66f-297">Send to a backup destination.</span></span>|

## <a name="hosting"></a><span data-ttu-id="8f66f-298">Hosting</span><span class="sxs-lookup"><span data-stu-id="8f66f-298">Hosting</span></span>

<span data-ttu-id="8f66f-299">Vzhledem k tomu, že je služba Směrování implementována jako služba WCF, musí být buď v rámci aplikace, nebo hostovaná službou IIS, nebo WAS.</span><span class="sxs-lookup"><span data-stu-id="8f66f-299">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="8f66f-300">Doporučuje se, aby směrovací služba byla hostována buď ve službě IIS, WAS, nebo v aplikaci služby systému Windows, která umožňuje využívat funkce automatické správy spuštění a životního cyklu, které jsou k dispozici v těchto hostitelských prostředích.</span><span class="sxs-lookup"><span data-stu-id="8f66f-300">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>

<span data-ttu-id="8f66f-301">Následující příklad znázorňuje hostování směrovací služby v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8f66f-301">The following example demonstrates hosting the Routing Service in an application.</span></span>

```csharp
using (ServiceHost serviceHost =
                new ServiceHost(typeof(RoutingService)))
```

<span data-ttu-id="8f66f-302">Chcete-li hostovat směrovací službu ve službě IIS nebo WAS, je nutné buď vytvořit soubor služby (. svc), nebo použít aktivaci služby na základě konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8f66f-302">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="8f66f-303">Při použití souboru služby je nutné zadat <xref:System.ServiceModel.Routing.RoutingService> pomocí parametru služby.</span><span class="sxs-lookup"><span data-stu-id="8f66f-303">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="8f66f-304">Následující příklad obsahuje ukázkový soubor služby, který se dá použít k hostování směrovací služby se službou IIS nebo WAS.</span><span class="sxs-lookup"><span data-stu-id="8f66f-304">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,
     PublicKeyToken=31bf3856ad364e35" %>
```

## <a name="routing-service-and-impersonation"></a><span data-ttu-id="8f66f-305">Služba Směrování a zosobnění</span><span class="sxs-lookup"><span data-stu-id="8f66f-305">Routing Service and Impersonation</span></span>

<span data-ttu-id="8f66f-306">Směrovací službu WCF lze použít s zosobněním pro posílání i přijímání zpráv.</span><span class="sxs-lookup"><span data-stu-id="8f66f-306">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="8f66f-307">Platí všechna obvyklá omezení Windows pro zosobnění.</span><span class="sxs-lookup"><span data-stu-id="8f66f-307">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="8f66f-308">Pokud jste museli nastavit oprávnění služby nebo účtu pro použití zosobnění při psaní vlastní služby, budete muset provést stejný postup, abyste mohli použít zosobnění u směrovací služby.</span><span class="sxs-lookup"><span data-stu-id="8f66f-308">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="8f66f-309">Další informace najdete v tématu [delegování a zosobnění](delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="8f66f-309">For more information, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>

<span data-ttu-id="8f66f-310">Zosobnění pomocí směrovací služby vyžaduje buď použití zosobnění ASP.NET v režimu kompatibility ASP.NET, nebo použití přihlašovacích údajů systému Windows, které byly nakonfigurovány tak, aby umožňovaly zosobnění.</span><span class="sxs-lookup"><span data-stu-id="8f66f-310">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="8f66f-311">Další informace o režimu kompatibility ASP.NET najdete v tématu [služby WCF a ASP.NET](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="8f66f-311">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>

> [!WARNING]
> <span data-ttu-id="8f66f-312">Směrovací služba WCF nepodporuje zosobnění s využitím základního ověřování.</span><span class="sxs-lookup"><span data-stu-id="8f66f-312">The WCF Routing Service does not support impersonation with basic authentication.</span></span>

<span data-ttu-id="8f66f-313">Pokud chcete používat zosobnění ASP.NET se službou směrování, povolte v hostitelském prostředí služby režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8f66f-313">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="8f66f-314">Směrovací služba již byla označena jako povolení režimu kompatibility ASP.NET a zosobnění bude automaticky povoleno.</span><span class="sxs-lookup"><span data-stu-id="8f66f-314">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="8f66f-315">Zosobnění je jediné podporované použití integrace ASP.NET se směrovací službou.</span><span class="sxs-lookup"><span data-stu-id="8f66f-315">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>

<span data-ttu-id="8f66f-316">Pokud chcete používat zosobnění přihlašovacích údajů systému Windows se službou směrování, je nutné nakonfigurovat pověření i službu.</span><span class="sxs-lookup"><span data-stu-id="8f66f-316">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="8f66f-317">Objekt přihlašovacích údajů klienta (<xref:System.ServiceModel.Security.WindowsClientCredential>přístupný z <xref:System.ServiceModel.ChannelFactory>) definuje vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>, která musí být nastavena tak, aby povolovala zosobnění.</span><span class="sxs-lookup"><span data-stu-id="8f66f-317">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="8f66f-318">Nakonec ve službě potřebujete nakonfigurovat chování <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> pro nastavení `ImpersonateCallerForAllOperations` na `true`.</span><span class="sxs-lookup"><span data-stu-id="8f66f-318">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="8f66f-319">Směrovací služba používá tento příznak k rozhodnutí, jestli se mají vytvořit klienti pro předávání zpráv s povoleným zosobněním.</span><span class="sxs-lookup"><span data-stu-id="8f66f-319">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f66f-320">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f66f-320">See also</span></span>

- [<span data-ttu-id="8f66f-321">Filtry zpráv</span><span class="sxs-lookup"><span data-stu-id="8f66f-321">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="8f66f-322">Kontrakty pro směrování</span><span class="sxs-lookup"><span data-stu-id="8f66f-322">Routing Contracts</span></span>](routing-contracts.md)
- [<span data-ttu-id="8f66f-323">Výběr filtru</span><span class="sxs-lookup"><span data-stu-id="8f66f-323">Choosing a Filter</span></span>](choosing-a-filter.md)
