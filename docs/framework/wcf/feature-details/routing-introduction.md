---
title: Směrování – úvod
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: e540e084305aee51d6820cc9ae43f7791d5c07d6
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842762"
---
# <a name="routing-introduction"></a><span data-ttu-id="c0e9b-102">Směrování – úvod</span><span class="sxs-lookup"><span data-stu-id="c0e9b-102">Routing Introduction</span></span>
<span data-ttu-id="c0e9b-103">Směrovací služba poskytuje obecný modulární SOAP zprostředkovatel, který je schopen směrování zpráv na základě obsahu zpráv.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-103">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="c0e9b-104">Ve službě Směrování můžete vytvořit komplexní logiku směrování, která umožňuje implementovat scénáře, jako je služba agregace, Správa verzí služby, priority směrování a směrování vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-104">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="c0e9b-105">Směrovací služba taky poskytuje chyba zpracování, který umožňuje nastavení seznamů zálohování koncových bodů, do které se odešlou zprávy, pokud dojde k chybě při odesílání na cílové primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-105">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>  
  
 <span data-ttu-id="c0e9b-106">Toto téma je určené pro ty novým uživatelům služby Směrování a pokrývá základní konfiguraci a který je hostitelem služby směrování.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-106">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c0e9b-107">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c0e9b-107">Configuration</span></span>  
 <span data-ttu-id="c0e9b-108">Směrovací služba je implementovaná jako služba WCF, který zpřístupňuje jeden nebo více koncových bodů služby, které přijímají zprávy z klientských aplikací a směrování zpráv do cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-108">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="c0e9b-109">Poskytuje služby <xref:System.ServiceModel.Routing.RoutingBehavior>, který se použije ke koncovým bodům služby určeného službou.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-109">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="c0e9b-110">Toto chování slouží ke konfiguraci různých aspektů jak služba funguje.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-110">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="c0e9b-111">Pro usnadnění konfigurace, pokud je používán konfigurační soubor, parametry jsou určeny na **chování RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-111">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="c0e9b-112">Ve scénářích založený na kódu, tyto parametry by se zadal jako součást <xref:System.ServiceModel.Routing.RoutingConfiguration> objektu, který je pak možné předat do **chování RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-112">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>  
  
 <span data-ttu-id="c0e9b-113">Při spouštění, přidá toto chování <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, který se používá k provedení protokolu SOAP zpracování zpráv do koncových bodů klienta.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-113">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="c0e9b-114">To umožňuje službě směrování přenosu zpráv do koncových bodů, které vyžadují jinou **MessageVersion** než byla přijata zpráva přes koncový bod.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-114">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="c0e9b-115">**Chování RoutingBehavior** také zaregistruje rozšíření služby, <xref:System.ServiceModel.Routing.RoutingExtension>, který představuje bod usnadnění pro úpravu konfigurace služby směrování v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-115">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>  
  
 <span data-ttu-id="c0e9b-116">**Konfigurace RoutingConfiguration** třída poskytuje konzistentní způsob konfigurace a aktualizuje se konfigurace služby směrování.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-116">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="c0e9b-117">Obsahuje parametry, které fungují jako nastavení služby Směrování a slouží ke konfiguraci **chování RoutingBehavior** při spuštění služby, nebo je předán **třída RoutingExtension** upravit směrování konfigurace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-117">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>  
  
 <span data-ttu-id="c0e9b-118">Směrování logika používá ke směrování na základě obsahu zpráv je definována seskupením několika <xref:System.ServiceModel.Dispatcher.MessageFilter> objekty do filtru tabulky (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objekty).</span><span class="sxs-lookup"><span data-stu-id="c0e9b-118">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="c0e9b-119">Příchozí zprávy se vyhodnocují před filtry zpráv obsažené v tabulce filtrů a pro každou **MessageFilter** , který odpovídá zprávě, předávají do cílového koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-119">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="c0e9b-120">Tabulky filtru, který se má použít pro směrování zpráv je určené vlastností buď **chování RoutingBehavior** v konfiguraci nebo prostřednictvím kódu pomocí **konfigurace RoutingConfiguration** objektu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-120">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>  
  
### <a name="defining-endpoints"></a><span data-ttu-id="c0e9b-121">Definování koncových bodů</span><span class="sxs-lookup"><span data-stu-id="c0e9b-121">Defining Endpoints</span></span>  
 <span data-ttu-id="c0e9b-122">Když to může zdát, že byste měli začít konfiguraci tak, že definujete směrování logika, kterou budete používat, prvním krokem by ve skutečnosti k určení tvaru budete směrování zpráv do koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-122">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="c0e9b-123">Směrovací služba používá smlouvy definující tvar kanály použité pro příjem a odesílání zpráv a proto tvar vstupní kanál musí odpovídat výstupní kanál.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-123">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="c0e9b-124">Například pokud jsou směrování do koncových bodů, které používají tvar kanálu požadavek odpověď, pak musíte použít kompatibilní kontrakt na vstupní koncové body, jako <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-124">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>  
  
 <span data-ttu-id="c0e9b-125">To znamená, že pokud vaše cílové koncové body pomocí smluv s více vzorky komunikace (jako je například míchání jednosměrnou a obousměrnou), nebude možné vytvořit koncový bod jedinou službou, která může přijímat a směrování zpráv do všech z nich.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-125">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="c0e9b-126">Musíte určit, jaké koncové body kompatibilní obrazce a definovat jeden nebo více koncových bodů služby, které se použijí pro příjem zpráv má být směrována na cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-126">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0e9b-127">Při práci s smluv, které určují víc komunikačních schémat (například kombinaci jednosměrnou a obousměrnou operations), použití duplexního kontraktu na směrování služby, jako je řešení <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-127">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="c0e9b-128">Ale to znamená, že vazba musí být schopné duplexní komunikaci, která nemusí být možné pro všechny scénáře.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-128">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="c0e9b-129">V situacích, kdy to není možné může být nutné které budou zohledňovat komunikaci do více koncových bodů nebo úpravách aplikace.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-129">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>  
  
 <span data-ttu-id="c0e9b-130">Další informace o kontrakty pro směrování najdete v tématu [kontrakty pro směrování](routing-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="c0e9b-130">For more information about routing contracts, see [Routing Contracts](routing-contracts.md).</span></span>  
  
 <span data-ttu-id="c0e9b-131">Po definování koncového bodu služby, můžete použít **chování RoutingBehavior** přidružit konkrétní **konfigurace RoutingConfiguration** s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-131">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="c0e9b-132">Při konfiguraci pomocí konfiguračního souboru služby směrování **chování RoutingBehavior** slouží k určení filtru tabulky, která obsahuje logiku směrování používají ke zpracování zpráv přijatých na tomto koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-132">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="c0e9b-133">Pokud konfigurujete směrovací služba prostřednictvím kódu programu můžete zadat filtr tabulky pomocí **konfigurace RoutingConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-133">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>  
  
 <span data-ttu-id="c0e9b-134">Následující příklad definuje služeb a klientských koncových bodů, které se používají službou směrování, jak prostřednictvím kódu programu a pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-134">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="c0e9b-135">Tento příklad konfiguruje službu směrování k vystavení jednoho koncového bodu s adresou `http://localhost:8000/routingservice/router`, který se používá pro příjem zpráv bude směrovat.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-135">This example configures the Routing Service to expose a single endpoint with an address of `http://localhost:8000/routingservice/router`, which is used to receive messages to be routed.</span></span> <span data-ttu-id="c0e9b-136">Protože zprávy jsou směrovány do koncových bodů požadavek odpověď, koncový bod služby používá <xref:System.ServiceModel.Routing.IRequestReplyRouter> kontraktu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-136">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="c0e9b-137">Tato konfigurace taky definuje je koncový bod konkrétního klienta `http://localhost:8000/servicemodelsample/service` zprávy jsou směrovány do.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-137">This configuration also defines a single client endpoint of `http://localhost:8000/servicemodelsample/service` that messages are routed to.</span></span> <span data-ttu-id="c0e9b-138">Filtr tabulky (není vidět) s názvem "routingTable1" obsahuje logiku směrování slouží ke směrování zpráv a je přidružen koncový bod služby s použitím **chování RoutingBehavior** (pro konfigurační soubor) nebo  **Konfigurace RoutingConfiguration** (pro programovou konfiguraci).</span><span class="sxs-lookup"><span data-stu-id="c0e9b-138">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>  
  
### <a name="routing-logic"></a><span data-ttu-id="c0e9b-139">Logiku směrování</span><span class="sxs-lookup"><span data-stu-id="c0e9b-139">Routing Logic</span></span>  
 <span data-ttu-id="c0e9b-140">K definování směrování logikou používanou pro směrování zpráv, musíte určit, co mohou být data obsažená v rámci příchozích zpráv jednoznačně reagovali na ni.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-140">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="c0e9b-141">Například pokud všechny cílové koncové body, které jsou směrování sdílet stejné akce SOAP hodnotu akce obsažené v něm není jasně ukazuje na jaké konkrétní koncového bodu zprávy by měl směrovat na.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-141">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="c0e9b-142">Pokud jeden konkrétní koncový bod musí jednoznačně směrovat zprávy, by měl filtrovat data, která jednoznačně identifikuje cílového koncového bodu, který se zpráva směruje do.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-142">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>  
  
 <span data-ttu-id="c0e9b-143">Směrovací služba nabízí několik **MessageFilter** implementace, které zkontrolovat konkrétní hodnoty ve zprávě, jako je například adresa, akce, název koncového bodu nebo dokonce dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-143">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="c0e9b-144">Pokud žádná z těchto implementací nevyhovuje vašim potřebám, můžete vytvořit vlastní **MessageFilter** implementace.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-144">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="c0e9b-145">Další informace o filtrech zpráv a porovnání implementace používá služba Směrování najdete v tématu [filtry zpráv](message-filters.md) a [výběr filtru](choosing-a-filter.md).</span><span class="sxs-lookup"><span data-stu-id="c0e9b-145">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](message-filters.md) and [Choosing a Filter](choosing-a-filter.md).</span></span>  
  
 <span data-ttu-id="c0e9b-146">Několik filtrů zpráv jsou uspořádané do filtru tabulky, které každou **MessageFilter** s koncovým bodem v cílové.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-146">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="c0e9b-147">Volitelně můžete filtru tabulky lze také zadat seznam koncových bodů zálohování, které směrovací služba se pokusí odeslat zprávu, která se v případě selhání přenosu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-147">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>  
  
 <span data-ttu-id="c0e9b-148">Ve výchozím nastavení se všechny filtry zpráv v tabulce filtrů vyhodnocují současně; Můžete však zadat <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> , který způsobí, že filtry zpráv, který se má vyhodnotit v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-148">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="c0e9b-149">Všechny položky s nejvyšší prioritou jsou vyhodnoceny jako první a filtry zpráv nižší priority nebudou vyhodnoceny, pokud se najde shoda na vyšší úrovni priority.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-149">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="c0e9b-150">Další informace o filtru tabulky, najdete v části [filtry zpráv](message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="c0e9b-150">For more information about filter tables, see [Message Filters](message-filters.md).</span></span>  
  
 <span data-ttu-id="c0e9b-151">Následující příklady používají <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, který se hodnotí jako `true` pro všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-151">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="c0e9b-152">To **MessageFilter** se přidá do tabulky "routingTable1" filtr, který přidruží **MessageFilter** s koncovým bodem klienta s názvem "CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="c0e9b-152">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="c0e9b-153">**Chování RoutingBehavior** pak určuje, že tato tabulka má být použito pro směrování zpráv zpracovaných v koncovém bodě služby.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-153">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>  
  
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
>  <span data-ttu-id="c0e9b-154">Ve výchozím nastavení vyhodnotí směrovací služba pouze záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-154">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="c0e9b-155">Pokud chcete povolit filtry pro přístup k textu zprávy, je nutné nastavit <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> k `false`.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-155">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>  
  
 <span data-ttu-id="c0e9b-156">**Vícesměrové vysílání**</span><span class="sxs-lookup"><span data-stu-id="c0e9b-156">**Multicast**</span></span>  
  
 <span data-ttu-id="c0e9b-157">Zatímco mnoho konfigurací směrovací služba použít exkluzivní filtr logiku, která provádí směrování zpráv do jediného určitého koncového bodu, budete muset směrování danou zprávu do více cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-157">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="c0e9b-158">K vícesměrovému vysílání zpráv do více cílů musí být splněné následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="c0e9b-158">To multicast a message to multiple destinations, the following conditions must be true:</span></span>  
  
-   <span data-ttu-id="c0e9b-159">Tvar kanálu nesmí být požadavek odpověď (i když mohou být jednosměrné nebo obousměrné,) vzhledem k tomu, že pouze jednu odpověď lze přijímat pomocí klientské aplikace v odpovědi na požadavek.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-159">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>  
  
-   <span data-ttu-id="c0e9b-160">Několik filtrů musí vracet `true` při vyhodnocování zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-160">Multiple filters must return `true` when evaluating the message.</span></span>  
  
 <span data-ttu-id="c0e9b-161">Pokud jste splnili tyto podmínky se zpráva směruje na všechny koncové body všech filtrů, která se vyhodnotí `true`.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-161">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="c0e9b-162">Následující příklad definuje konfiguraci směrování, jejímž výsledkem zprávy směruje se oba koncové body v případě, že je adresa koncového bodu ve zprávě `http://localhost:8000/routingservice/router/rounding`.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-162">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is `http://localhost:8000/routingservice/router/rounding`.</span></span>  
  
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
  
### <a name="soap-processing"></a><span data-ttu-id="c0e9b-163">Zpracování SOAP</span><span class="sxs-lookup"><span data-stu-id="c0e9b-163">SOAP Processing</span></span>  
 <span data-ttu-id="c0e9b-164">Pro podporu směrování zpráv mezi rozdílných protokolů **chování RoutingBehavior** ve výchozím nastavení přidá <xref:System.ServiceModel.Routing.SoapProcessingBehavior> do všech koncových bodů klienta, které zprávy jsou směrovány na.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-164">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="c0e9b-165">Toto chování automaticky vytvoří nový **MessageVersion** před směrováním zprávy na koncový bod, jakož i vytváření kompatibilní **MessageVersion** pro jakýkoliv dokument odpověď před vrácením do žádost o klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-165">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>  
  
 <span data-ttu-id="c0e9b-166">Kroky k vytvoření nového **MessageVersion** odchozí zprávy jsou následující:</span><span class="sxs-lookup"><span data-stu-id="c0e9b-166">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>  
  
 <span data-ttu-id="c0e9b-167">**Zpracování žádosti**</span><span class="sxs-lookup"><span data-stu-id="c0e9b-167">**Request processing**</span></span>  
  
-   <span data-ttu-id="c0e9b-168">Získejte **MessageVersion** výstupní vazbu/kanálu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-168">Get the **MessageVersion** of the outbound binding/channel.</span></span>  
  
-   <span data-ttu-id="c0e9b-169">Získejte čtečka textu pro původní zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-169">Get the body reader for the original message.</span></span>  
  
-   <span data-ttu-id="c0e9b-170">Vytvořte novou zprávu o stejnou akci, čtečky textu a nový **MessageVersion**.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-170">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>  
  
-   <span data-ttu-id="c0e9b-171">Pokud <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, zkopírujte do, z FaultTo a záhlaví RelatesTo nové zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-171">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
-   <span data-ttu-id="c0e9b-172">Zkopírujte všechny vlastnosti zprávy do nové zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-172">Copy all message properties to the new message.</span></span>  
  
-   <span data-ttu-id="c0e9b-173">Store původní zprávy s požadavkem pro použití při zpracování odpovědi.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-173">Store the original request message to use when processing the response.</span></span>  
  
-   <span data-ttu-id="c0e9b-174">Vrátí novou zprávu požadavku.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-174">Return the new request message.</span></span>  
  
 <span data-ttu-id="c0e9b-175">**Zpracování odpovědi**</span><span class="sxs-lookup"><span data-stu-id="c0e9b-175">**Response processing**</span></span>  
  
-   <span data-ttu-id="c0e9b-176">Získejte **MessageVersion** původní zprávy s požadavkem.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-176">Get the **MessageVersion** of the original request message.</span></span>  
  
-   <span data-ttu-id="c0e9b-177">Získání čtečky textu zprávy přijaté odpovědi.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-177">Get the body reader for the received response message.</span></span>  
  
-   <span data-ttu-id="c0e9b-178">Vytvoření nové zprávy odpovědi se stejnou akci, čtečky textu a **MessageVersion** původní zprávy s požadavkem.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-178">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>  
  
-   <span data-ttu-id="c0e9b-179">Pokud <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, zkopírujte do, z FaultTo a záhlaví RelatesTo nové zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-179">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
-   <span data-ttu-id="c0e9b-180">Zkopírujte vlastnosti zprávy do nové zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-180">Copy the message properties to the new message.</span></span>  
  
-   <span data-ttu-id="c0e9b-181">Vrátí nové zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-181">Return the new response message.</span></span>  
  
 <span data-ttu-id="c0e9b-182">Ve výchozím nastavení **SoapProcessingBehavior** se automaticky přidá do koncových bodů klienta podle <xref:System.ServiceModel.Routing.RoutingBehavior> při spuštění služby; však můžete řídit, zda zpracování SOAP se přidá do všech koncových bodů klienta pomocí <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-182">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="c0e9b-183">Můžete také přidat chování přímo do určitého koncového bodu a povolit nebo zakázat toto chování na úrovni koncového bodu, pokud přesněji řídit zpracování SOAP se vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-183">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0e9b-184">Pokud zpracování SOAP je zakázaná pro koncový bod, který vyžaduje jinou třídu MessageVersion než původní zprávy s požadavkem, je nutné zadat vlastní mechanismus pro provedení změny protokolu SOAP, které jsou nutné před odesláním zprávy cílový koncový bod.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-184">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>  
  
 <span data-ttu-id="c0e9b-185">V následujících příkladech **soapProcessingEnabled** vlastnost se používá při prevenci **SoapProcessingBehavior** z automaticky přidán do všech koncových bodů klientů.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-185">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>  
  
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
  
### <a name="dynamic-configuration"></a><span data-ttu-id="c0e9b-186">Dynamickou konfiguraci</span><span class="sxs-lookup"><span data-stu-id="c0e9b-186">Dynamic Configuration</span></span>  
 <span data-ttu-id="c0e9b-187">Při přidání dalších klientských koncových bodů, nebo třeba upravit filtry, které se používají ke směrování zpráv, potřebujete způsob, jak aktualizovat konfiguraci dynamicky za běhu, aby se zabránilo přerušení služby aktuálně příjem zpráv pomocí koncových bodů Služba směrování.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-187">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="c0e9b-188">Úprava konfiguračního souboru nebo kód hostitelskou aplikaci nestačí vždy, protože některé z metod vyžaduje provedení recyklace aplikace, což by mohlo dojít k potenciální ztrátě všechny zprávy momentálně v provozu a má větší potenciál pro výpadku, zatímco Čekání na službu restartovat.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-188">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>  
  
 <span data-ttu-id="c0e9b-189">Upravit lze pouze **konfigurace RoutingConfiguration** prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-189">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="c0e9b-190">Zatímco služba může počáteční konfiguraci pomocí konfiguračního souboru, můžete upravovat konfiguraci za běhu pouze tak, že vytváří nový **RoutingConfigution** a předejte ji jako parametr, který se <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> – metoda vystavené <xref:System.ServiceModel.Routing.RoutingExtension> služby rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-190">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfigution** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="c0e9b-191">Všechny zprávy aktuálně při přenosu i nadále možné směrovat pomocí předchozí konfigurace, při zprávy přijaté po volání **ApplyConfiguration** používat nové nakonfigurování.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-191">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="c0e9b-192">Následující příklad ukazuje vytvoření instance služby Směrování a následně úpravou konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-192">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>  
  
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
>  <span data-ttu-id="c0e9b-193">Při aktualizaci služby směrování tímto způsobem je pouze možné předat novou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-193">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="c0e9b-194">Není možné změnit pouze vybrané prvky aktuální konfigurace nebo přidání nových položek do aktuální konfigurace. musíte vytvořit a předat novou konfiguraci, která nahradí stávající.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-194">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0e9b-195">Otevřít pomocí předchozí konfiguraci relace pokračovat pomocí předchozí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-195">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="c0e9b-196">Nová konfigurace se používá pouze pomocí nové relace.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-196">The new configuration is only used by new sessions.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="c0e9b-197">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="c0e9b-197">Error Handling</span></span>  
 <span data-ttu-id="c0e9b-198">Pokud existuje <xref:System.ServiceModel.CommunicationException> dochází při pokusu o odeslání zprávy, zkuste místo pro zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-198">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="c0e9b-199">Tyto výjimky obvykle signalizují, že došlo k potížím při pokusu o komunikaci s koncovým bodem definované klienta, například <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, nebo <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-199">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="c0e9b-200">Zpracování – kód chyby: také zachytit a pokus opakujte při odesílání <xref:System.TimeoutException> dojde, což je další běžné výjimku, která není odvozena od **communicationexception –**.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-200">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>  
  
 <span data-ttu-id="c0e9b-201">Při jedné z předchozí výjimky, směrovací služba převezme služby při selhání do seznamu zálohy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-201">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="c0e9b-202">Pokud všechny koncové body zálohování neúspěšné a zobrazí se selháním komunikace nebo pokud koncový bod vrací výjimku, která indikuje selhání v rámci cílové služby, směrovací služba vrátí chybu do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-202">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0e9b-203">Funkce zpracování chyb shromažďuje a zpracovává výjimky, ke kterým dochází při pokusu o odeslání zprávy a při pokusu o zavření kanálu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-203">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="c0e9b-204">Kód pro zpracování chyb není určena pro zjišťování nebo zpracování výjimek vytvořených koncových bodů aplikace, který komunikuje s; <xref:System.ServiceModel.FaultException> vyvolané služby se zobrazí na směrování služby jako **FaultMessage** a je počet plynoucích zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-204">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>  
>   
>  <span data-ttu-id="c0e9b-205">Pokud dojde k chybě, když se pokusí služba směrování přenosu zprávy, se může zobrazit <xref:System.ServiceModel.FaultException> na straně klienta, spíše než <xref:System.ServiceModel.EndpointNotFoundException> získali byste normálně chybí směrovací službou.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-205">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="c0e9b-206">Směrovací služba může proto maskovat výjimky a poskytovat úplnou transparentnost není-li prozkoumat vnořené výjimky.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-206">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>  
  
### <a name="tracing-exceptions"></a><span data-ttu-id="c0e9b-207">Sledování výjimek</span><span class="sxs-lookup"><span data-stu-id="c0e9b-207">Tracing Exceptions</span></span>  
 <span data-ttu-id="c0e9b-208">Při odesílání zprávy na koncový bod v seznamu se nezdaří, směrovací služba trasování Výsledná data výjimky a připojí podrobnosti o výjimce jako do zprávy vlastnost s názvem **výjimky**.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-208">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="c0e9b-209">To zachová data výjimky a umožňuje programový přístup uživatelů prostřednictvím zprávy inspector.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-209">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="c0e9b-210">Výjimka data se ukládají na zprávu ve slovníku, který mapuje název koncového bodu na podrobnosti o výjimce došlo při pokusu o odeslání zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-210">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>  
  
### <a name="backup-endpoints"></a><span data-ttu-id="c0e9b-211">Zálohování koncových bodů</span><span class="sxs-lookup"><span data-stu-id="c0e9b-211">Backup Endpoints</span></span>  
 <span data-ttu-id="c0e9b-212">Každá položka filtru v tabulce filtrů můžete volitelně zadat seznamu zálohy koncových bodů, které se používají v případě selhání přenosu, při odesílání na primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-212">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="c0e9b-213">Pokud dojde k takové chybě, směrovací služba se pokusí zaslání zprávy na první položku v seznamu zálohy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-213">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="c0e9b-214">Pokud tento pokus o odeslání také zaznamená selhání přenosu, zkusí se další koncový bod v seznamu záloh.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-214">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="c0e9b-215">Směrovací služba pokračuje v odesílání zprávy pro každý koncový bod v seznamu, dokud úspěšně doručení zprávy, všechny koncové body, vrátí hodnotu Neúspěch přenosu nebo selhání než přenos je vrácený koncový bod.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-215">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>  
  
 <span data-ttu-id="c0e9b-216">Následující příklady konfigurovat směrovací služba použít záložní seznam.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-216">The following examples configure the Routing Service to use a backup list.</span></span>  
  
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
  
### <a name="supported-error-patterns"></a><span data-ttu-id="c0e9b-217">Vzory podporované chyb</span><span class="sxs-lookup"><span data-stu-id="c0e9b-217">Supported Error Patterns</span></span>  
 <span data-ttu-id="c0e9b-218">Následující tabulka popisuje vzory, které jsou kompatibilní s použitím seznamů záložního koncového bodu, spolu s poznámky popisující podrobnosti o zpracování chyb pro určité vzory.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-218">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>  
  
|<span data-ttu-id="c0e9b-219">Vzor</span><span class="sxs-lookup"><span data-stu-id="c0e9b-219">Pattern</span></span>|<span data-ttu-id="c0e9b-220">Relace</span><span class="sxs-lookup"><span data-stu-id="c0e9b-220">Session</span></span>|<span data-ttu-id="c0e9b-221">Transakce</span><span class="sxs-lookup"><span data-stu-id="c0e9b-221">Transaction</span></span>|<span data-ttu-id="c0e9b-222">Kontextu přijetí</span><span class="sxs-lookup"><span data-stu-id="c0e9b-222">Receive Context</span></span>|<span data-ttu-id="c0e9b-223">Nepodporuje zálohování seznamu</span><span class="sxs-lookup"><span data-stu-id="c0e9b-223">Backup List Supported</span></span>|<span data-ttu-id="c0e9b-224">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0e9b-224">Notes</span></span>|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|<span data-ttu-id="c0e9b-225">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="c0e9b-225">One-Way</span></span>||||<span data-ttu-id="c0e9b-226">Ano</span><span class="sxs-lookup"><span data-stu-id="c0e9b-226">Yes</span></span>|<span data-ttu-id="c0e9b-227">Pokusí se znovu odeslat zprávu na záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-227">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="c0e9b-228">Pokud se tato zpráva vícesměrového vysílání, pouze zprávu na selhání kanálu je přesunout do jeho cílovou složku zálohy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-228">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|  
|<span data-ttu-id="c0e9b-229">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="c0e9b-229">One-Way</span></span>||<span data-ttu-id="c0e9b-230">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-230">![Check mark](media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="c0e9b-231">Ne</span><span class="sxs-lookup"><span data-stu-id="c0e9b-231">No</span></span>|<span data-ttu-id="c0e9b-232">Vyvolá se výjimka a transakce je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-232">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="c0e9b-233">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="c0e9b-233">One-Way</span></span>|||<span data-ttu-id="c0e9b-234">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-234">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="c0e9b-235">Ano</span><span class="sxs-lookup"><span data-stu-id="c0e9b-235">Yes</span></span>|<span data-ttu-id="c0e9b-236">Pokusí se znovu odeslat zprávu na záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-236">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="c0e9b-237">Po zprávy se úspěšně přijatá, dokončení všech zobrazí kontexty.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-237">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="c0e9b-238">Pokud zpráva není úspěšně přijme libovolný koncový bod, nejsou dokončeny kontext přijetí.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-238">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="c0e9b-239">Když se tato zpráva vícesměrového vysílání, kontext přijetí se dokončí, pouze pokud zpráva se úspěšně přijme aspoň jeden koncový bod (primárních nebo záložních).</span><span class="sxs-lookup"><span data-stu-id="c0e9b-239">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="c0e9b-240">Pokud žádný z koncových bodů v některém z vícesměrového vysílání cesty úspěšně zobrazí zpráva, kontext přijetí nedokončí.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-240">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|  
|<span data-ttu-id="c0e9b-241">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="c0e9b-241">One-Way</span></span>||<span data-ttu-id="c0e9b-242">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-242">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="c0e9b-243">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-243">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="c0e9b-244">Ano</span><span class="sxs-lookup"><span data-stu-id="c0e9b-244">Yes</span></span>|<span data-ttu-id="c0e9b-245">Přerušit předchozí transakce, vytvořte novou transakci a znovu odeslat všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-245">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="c0e9b-246">Cíl zálohy se přenáší zprávy, které došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-246">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="c0e9b-247">Po vytvoření transakce ve kterém veškeré přenosy dat úspěšné dokončení kontexty přijetí a potvrzení transakce.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-247">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|  
|<span data-ttu-id="c0e9b-248">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="c0e9b-248">One-Way</span></span>|<span data-ttu-id="c0e9b-249">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-249">![Check mark](media/checkmark.gif "Checkmark")</span></span>|||<span data-ttu-id="c0e9b-250">Ano</span><span class="sxs-lookup"><span data-stu-id="c0e9b-250">Yes</span></span>|<span data-ttu-id="c0e9b-251">Pokusí se znovu odeslat zprávu na záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-251">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="c0e9b-252">V případě vícesměrového vysílání se znovu pouze zprávy v relaci došlo k chybě nebo relaci zavřete jehož relaci se nepovedlo odeslat do cíle zálohování.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-252">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|  
|<span data-ttu-id="c0e9b-253">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="c0e9b-253">One-Way</span></span>|<span data-ttu-id="c0e9b-254">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-254">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="c0e9b-255">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-255">![Check mark](media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="c0e9b-256">Ne</span><span class="sxs-lookup"><span data-stu-id="c0e9b-256">No</span></span>|<span data-ttu-id="c0e9b-257">Vyvolá se výjimka a transakce je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-257">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="c0e9b-258">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="c0e9b-258">One-Way</span></span>|<span data-ttu-id="c0e9b-259">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-259">![Check mark](media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="c0e9b-260">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-260">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="c0e9b-261">Ano</span><span class="sxs-lookup"><span data-stu-id="c0e9b-261">Yes</span></span>|<span data-ttu-id="c0e9b-262">Pokusí se znovu odeslat zprávu na záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-262">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="c0e9b-263">Po všechny zprávy odešle dokončena bez chyb, relace indikuje žádné další zprávy a služba Směrování úspěšně zavře všechny odchozí relace kanálů, obdrží všechny kontexty jsou dokončeny, a kanálů příchozích relací je uzavřen.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-263">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|  
|<span data-ttu-id="c0e9b-264">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="c0e9b-264">One-Way</span></span>|<span data-ttu-id="c0e9b-265">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-265">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="c0e9b-266">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-266">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="c0e9b-267">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-267">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="c0e9b-268">Ano</span><span class="sxs-lookup"><span data-stu-id="c0e9b-268">Yes</span></span>|<span data-ttu-id="c0e9b-269">Zrušit aktuální transakci a vytvořte novou.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-269">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="c0e9b-270">Znovu odešlete všechny předchozí zprávy v relaci.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-270">Resend all previous messages in the session.</span></span> <span data-ttu-id="c0e9b-271">Poté, co byl vytvořen transakce které všechny zprávy se úspěšně odeslaly a relace indikuje, že se žádné další zprávy, všechny odchozí relace kanály zavřená, zobrazí všechny kontexty jsou dokončeny s transakcí, je kanálů příchozích relací zavření, a je transakce potvrzena.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-271">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="c0e9b-272">Když probíhá relace vícesměrového vysílání zpráv, u kterých nedošlo k chybě se zopakuje pro stejný cíl jako před a zpráv, ke které došlo k chybě odesílají do cíle zálohování.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-272">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|  
|<span data-ttu-id="c0e9b-273">Obousměrný</span><span class="sxs-lookup"><span data-stu-id="c0e9b-273">Two-Way</span></span>||||<span data-ttu-id="c0e9b-274">Ano</span><span class="sxs-lookup"><span data-stu-id="c0e9b-274">Yes</span></span>|<span data-ttu-id="c0e9b-275">Poslat cílovou složku zálohy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-275">Send to a backup destination.</span></span>  <span data-ttu-id="c0e9b-276">Po kanál vrátí zprávu odpovědi, vrátí odpověď klientovi původní.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-276">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="c0e9b-277">Obousměrný</span><span class="sxs-lookup"><span data-stu-id="c0e9b-277">Two-Way</span></span>|<span data-ttu-id="c0e9b-278">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-278">![Check mark](media/checkmark.gif "Checkmark")</span></span>|||<span data-ttu-id="c0e9b-279">Ano</span><span class="sxs-lookup"><span data-stu-id="c0e9b-279">Yes</span></span>|<span data-ttu-id="c0e9b-280">Odeslání všech zpráv na kanál pro cílovou složku zálohy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-280">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="c0e9b-281">Po kanál vrátí zprávu odpovědi, vrátí odpověď klientovi původní.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-281">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="c0e9b-282">Obousměrný</span><span class="sxs-lookup"><span data-stu-id="c0e9b-282">Two-Way</span></span>||<span data-ttu-id="c0e9b-283">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-283">![Check mark](media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="c0e9b-284">Ne</span><span class="sxs-lookup"><span data-stu-id="c0e9b-284">No</span></span>|<span data-ttu-id="c0e9b-285">Vyvolá se výjimka a transakce je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-285">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="c0e9b-286">Obousměrný</span><span class="sxs-lookup"><span data-stu-id="c0e9b-286">Two-Way</span></span>|<span data-ttu-id="c0e9b-287">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-287">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="c0e9b-288">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-288">![Check mark](media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="c0e9b-289">Ne</span><span class="sxs-lookup"><span data-stu-id="c0e9b-289">No</span></span>|<span data-ttu-id="c0e9b-290">Vyvolá se výjimka a transakce je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-290">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="c0e9b-291">Duplex</span><span class="sxs-lookup"><span data-stu-id="c0e9b-291">Duplex</span></span>||||<span data-ttu-id="c0e9b-292">Ne</span><span class="sxs-lookup"><span data-stu-id="c0e9b-292">No</span></span>|<span data-ttu-id="c0e9b-293">Duplexní komunikaci mimo relace se aktuálně nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-293">Non-session duplex communication is not currently supported.</span></span>|  
|<span data-ttu-id="c0e9b-294">Duplex</span><span class="sxs-lookup"><span data-stu-id="c0e9b-294">Duplex</span></span>|<span data-ttu-id="c0e9b-295">![Zaškrtávací políčko](media/checkmark.gif "značky zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="c0e9b-295">![Check mark](media/checkmark.gif "Checkmark")</span></span>|||<span data-ttu-id="c0e9b-296">Ano</span><span class="sxs-lookup"><span data-stu-id="c0e9b-296">Yes</span></span>|<span data-ttu-id="c0e9b-297">Poslat cílovou složku zálohy.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-297">Send to a backup destination.</span></span>|  
  
## <a name="hosting"></a><span data-ttu-id="c0e9b-298">Hostování</span><span class="sxs-lookup"><span data-stu-id="c0e9b-298">Hosting</span></span>  
 <span data-ttu-id="c0e9b-299">Protože směrovací služba je implementovaná jako služba WCF, se musí být buď v rámci aplikace v místním prostředí nebo hostované službou IIS nebo WAS.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-299">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="c0e9b-300">Doporučuje se, že směrovací služba hostitelem služby IIS, WAS nebo aplikace služby Windows využít k automatickému spuštění a životního cyklu správy funkce dostupné v těchto prostředích.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-300">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>  
  
 <span data-ttu-id="c0e9b-301">Následující příklad ukazuje, který je hostitelem služby směrování v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-301">The following example demonstrates hosting the Routing Service in an application.</span></span>  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 <span data-ttu-id="c0e9b-302">K hostování služby směrování v rámci služby IIS nebo WAS, musíte vytvořit soubor služby (.svc) nebo použít aktivaci prostřednictvím konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-302">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="c0e9b-303">Při použití souboru služby, je nutné zadat <xref:System.ServiceModel.Routing.RoutingService> pomocí parametru služby.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-303">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="c0e9b-304">Následující příklad obsahuje ukázkový soubor služby, který slouží k hostování služby směrování pomocí služby IIS nebo WAS.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-304">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a><span data-ttu-id="c0e9b-305">Služba Směrování a zosobnění</span><span class="sxs-lookup"><span data-stu-id="c0e9b-305">Routing Service and Impersonation</span></span>  
 <span data-ttu-id="c0e9b-306">Směrovací služba WCF je možné s zosobnění pro odesílání a příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-306">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="c0e9b-307">Použít obvyklé omezení Windows zosobnění.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-307">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="c0e9b-308">Pokud byste potřebovali nastavení účtu služby nebo oprávnění k použití zosobnění při zápisu vlastní služby, pak budete muset provést tyto stejné kroky pro použití zosobnění se směrovací službou.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-308">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="c0e9b-309">Další informace najdete v tématu [delegace a zosobnění](delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="c0e9b-309">For more information, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="c0e9b-310">Zosobnění se směrovací službou vyžaduje použití zosobnění technologie ASP.NET v režimu kompatibility ASP.NET nebo používání přihlašovacích údajů Windows, které jsou nakonfigurované k povolení zosobnění.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-310">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="c0e9b-311">Další informace o režim kompatibility ASP.NET najdete v tématu [služby WCF a ASP.NET](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="c0e9b-311">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c0e9b-312">Směrovací služba WCF nepodporuje zosobnění se základním ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-312">The WCF Routing Service does not support impersonation with basic authentication.</span></span>  
  
 <span data-ttu-id="c0e9b-313">Použití zosobnění technologie ASP.NET se směrovací službou, povolte režim kompatibility ASP.NET ve službě hostitelské prostředí.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-313">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="c0e9b-314">Směrovací služba již byla označena jako umožňuje režim kompatibility ASP.NET a zosobnění se automaticky povolí.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-314">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="c0e9b-315">Zosobnění je podporované pouze použití integrace ASP.NET se směrovací službou.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-315">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>  
  
 <span data-ttu-id="c0e9b-316">Použití zosobnění přihlašovacích údajů Windows se směrovací službou musíte nakonfigurovat přihlašovací údaje a služby.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-316">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="c0e9b-317">Objekt přihlašovacích údajů klienta (<xref:System.ServiceModel.Security.WindowsClientCredential>, přístupné z <xref:System.ServiceModel.ChannelFactory>) definuje <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost, která musí být nastaven tak, aby povolovala zosobnění.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-317">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="c0e9b-318">Nakonec ve službě je nutné nakonfigurovat <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> chování nastavení `ImpersonateCallerForAllOperations` k `true`.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-318">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="c0e9b-319">Směrovací služba používá tento příznak se rozhodnout, jestli se má vytvořit klienty pro předávání zpráv s zosobnění povoleno.</span><span class="sxs-lookup"><span data-stu-id="c0e9b-319">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e9b-320">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0e9b-320">See Also</span></span>  
 [<span data-ttu-id="c0e9b-321">Filtry zpráv</span><span class="sxs-lookup"><span data-stu-id="c0e9b-321">Message Filters</span></span>](message-filters.md)  
 [<span data-ttu-id="c0e9b-322">Kontrakty pro směrování</span><span class="sxs-lookup"><span data-stu-id="c0e9b-322">Routing Contracts</span></span>](routing-contracts.md)  
 [<span data-ttu-id="c0e9b-323">Výběr filtru</span><span class="sxs-lookup"><span data-stu-id="c0e9b-323">Choosing a Filter</span></span>](choosing-a-filter.md)
