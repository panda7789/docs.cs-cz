---
title: "Směrování – úvod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e0fe14f096ae0914235ea1d23b874f0aea906d9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="routing-introduction"></a><span data-ttu-id="e5b21-102">Směrování – úvod</span><span class="sxs-lookup"><span data-stu-id="e5b21-102">Routing Introduction</span></span>
<span data-ttu-id="e5b21-103">Poskytuje službu Směrování obecné modulární SOAP zprostředkující umožňující směrování zpráv na základě obsahu zprávy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-103">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="e5b21-104">Se službou směrování můžete vytvořit komplexní směrování logiku, která umožňuje implementovat scénáře, jako je služba agregace, verze služby, s prioritou směrování a směrování vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="e5b21-104">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="e5b21-105">Směrovací služby obsahuje také chyba zpracování, které umožňuje nastavit seznam zálohování koncových bodů, ke kterému jsou zprávy odesílány, pokud dojde k chybě při odesílání na cílové primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e5b21-105">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>  
  
 <span data-ttu-id="e5b21-106">Toto téma je určené pro ty novým uživatelům služby Směrování a popisuje základní konfigurace a který je hostitelem služby směrování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-106">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e5b21-107">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="e5b21-107">Configuration</span></span>  
 <span data-ttu-id="e5b21-108">Směrovací služby je implementovaný jako službu WCF, které vystavuje jeden nebo více služby koncových bodů, které přijímají zprávy z klientské aplikace a směrování zpráv na jeden nebo více cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="e5b21-108">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="e5b21-109">Poskytuje služby <xref:System.ServiceModel.Routing.RoutingBehavior>, který se použije ke koncovým bodům služby, který je zveřejněný prostřednictvím služby.</span><span class="sxs-lookup"><span data-stu-id="e5b21-109">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="e5b21-110">Toto chování slouží ke konfiguraci různé aspekty jak služba funguje.</span><span class="sxs-lookup"><span data-stu-id="e5b21-110">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="e5b21-111">Pro usnadnění konfigurace při použití konfiguračního souboru, parametry jsou zadány na **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="e5b21-111">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="e5b21-112">Ve scénářích založené na kódu by tyto parametry zadané v rámci <xref:System.ServiceModel.Routing.RoutingConfiguration> objekt, který může být předána do **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="e5b21-112">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>  
  
 <span data-ttu-id="e5b21-113">Při spouštění, přidá toto chování <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, který se používá k provádění SOAP zpracování zpráv, na koncové body klientů.</span><span class="sxs-lookup"><span data-stu-id="e5b21-113">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="e5b21-114">To umožňuje službě směrování přenosu zpráv do koncových bodů, které vyžadují jinou **verze MessageVersion** než zpráva byla přijata přes koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e5b21-114">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="e5b21-115">**RoutingBehavior** také zaregistruje rozšíření služby, <xref:System.ServiceModel.Routing.RoutingExtension>, které poskytuje bod usnadnění pro úpravu konfigurace směrování služby za běhu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-115">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>  
  
 <span data-ttu-id="e5b21-116">**RoutingConfiguration** třída poskytuje konzistentní způsob konfigurace a aktualizuje se konfigurace služby směrování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-116">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="e5b21-117">Obsahuje parametry, které fungují jako nastavení služby Směrování a slouží ke konfiguraci **RoutingBehavior** při spuštění služby, nebo je předán **RoutingExtension** k úpravě směrování konfigurace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-117">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>  
  
 <span data-ttu-id="e5b21-118">Směrování logikou používanou k provedení na základě obsahu směrování zpráv je definované seskupení více <xref:System.ServiceModel.Dispatcher.MessageFilter> filtrovat objekty společně do tabulky (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objektů).</span><span class="sxs-lookup"><span data-stu-id="e5b21-118">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="e5b21-119">Příchozí zprávy jsou porovnán s filtry zpráv, které jsou obsažené v tabulce filtru a pro každou **MessageFilter** odpovídající zprávu, předají do cílového koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-119">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="e5b21-120">Je zadána buď pomocí filtru tabulky, který se má použít pro směrování zpráv **RoutingBehavior** v konfiguraci nebo prostřednictvím kódu pomocí **RoutingConfiguration** objektu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-120">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>  
  
### <a name="defining-endpoints"></a><span data-ttu-id="e5b21-121">Definování koncové body</span><span class="sxs-lookup"><span data-stu-id="e5b21-121">Defining Endpoints</span></span>  
 <span data-ttu-id="e5b21-122">Při může zdát, že začněte konfiguraci definováním logice směrování, které budete používat, prvním krokem by měl být ve skutečnosti k určení tvaru, který bude směrování zpráv do koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="e5b21-122">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="e5b21-123">Směrovací služby používá smluv, které definují obrazec kanály použité pro příjem a odesílání zpráv, a proto obrazec vstupní kanál nástroje se musí shodovat s kanálu výstup.</span><span class="sxs-lookup"><span data-stu-id="e5b21-123">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="e5b21-124">Například, pokud jsou směrování do koncových bodů, které používají tvar kanálu požadavku a odpovědi, pak musíte použít kontraktu kompatibilní na příchozí koncových bodů, například <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span><span class="sxs-lookup"><span data-stu-id="e5b21-124">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>  
  
 <span data-ttu-id="e5b21-125">To znamená, že pokud cílové koncové body používat kontrakty s více komunikačních schémat (například kombinování jednosměrná a obousměrná operations), nebude možné vytvořit jeden služby koncový bod, který může přijímat a směrování zpráv do všech z nich.</span><span class="sxs-lookup"><span data-stu-id="e5b21-125">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="e5b21-126">Je třeba určit, které koncové body kompatibilní tvarů a definujte jeden nebo více služby koncových bodů, které se použije pro příjem zpráv k odeslání do cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="e5b21-126">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5b21-127">Při práci s smluv, které určují víc komunikačních schémat (například směs jednosměrná a obousměrná operations), použití duplexního kontraktu na směrování služby, jako je alternativní řešení <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span><span class="sxs-lookup"><span data-stu-id="e5b21-127">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="e5b21-128">Ale to znamená, že vazba musí být schopný duplexní komunikace, která nemusí být možné pro všechny scénáře.</span><span class="sxs-lookup"><span data-stu-id="e5b21-128">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="e5b21-129">Ve scénářích, kde to není možné může být nutné řešení komunikace do víc koncových bodů nebo úprava aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5b21-129">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>  
  
 <span data-ttu-id="e5b21-130">Další informace o směrování kontrakty najdete v tématu [kontrakty pro směrování](../../../../docs/framework/wcf/feature-details/routing-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="e5b21-130">For more information about routing contracts, see [Routing Contracts](../../../../docs/framework/wcf/feature-details/routing-contracts.md).</span></span>  
  
 <span data-ttu-id="e5b21-131">Až koncový bod služby je nadefinované, můžete použít **RoutingBehavior** přidružit konkrétní **RoutingConfiguration** ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-131">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="e5b21-132">Při konfiguraci služby směrování pomocí konfiguračního souboru **RoutingBehavior** slouží k určení filtru tabulky, která obsahuje směrování logiku používá ke zpracování zprávy přijaté na tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e5b21-132">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="e5b21-133">Pokud konfigurujete směrovací služby prostřednictvím kódu programu můžete zadat tabulku filtru pomocí **RoutingConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="e5b21-133">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>  
  
 <span data-ttu-id="e5b21-134">V následujícím příkladu definuje klienta a služby koncové body, které používají směrovací služby prostřednictvím kódu programu i pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="e5b21-134">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="e5b21-135">Tento příklad konfiguruje službu Směrování a vystavit jeden koncový bod s adresou "http://localhost: 8000/routingservice/směrovače", který se používá pro příjem zpráv k odeslání.</span><span class="sxs-lookup"><span data-stu-id="e5b21-135">This example configures the Routing Service to expose a single endpoint with an address of "http://localhost:8000/routingservice/router", which is used to receive messages to be routed.</span></span> <span data-ttu-id="e5b21-136">Protože zprávy jsou směrovány do koncových bodů požadavku a odpovědi, koncový bod služby používá <xref:System.ServiceModel.Routing.IRequestReplyRouter> kontrakt.</span><span class="sxs-lookup"><span data-stu-id="e5b21-136">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="e5b21-137">Tato konfigurace také definuje koncový bod jednoho klienta "http://localhost: 8000/servicemodelsample nebo služby", jsou směrovány zprávy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-137">This configuration also defines a single client endpoint of "http://localhost:8000/servicemodelsample/service" that messages are routed to.</span></span> <span data-ttu-id="e5b21-138">Tabulka filtru (není vidět) s názvem "routingTable1" obsahuje směrování logikou používanou pro směrování zpráv a je přidružen koncový bod služby pomocí **RoutingBehavior** (pro konfigurační soubor) nebo  **RoutingConfiguration** (pro Programová konfigurace).</span><span class="sxs-lookup"><span data-stu-id="e5b21-138">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>  
  
### <a name="routing-logic"></a><span data-ttu-id="e5b21-139">Směrování logiky</span><span class="sxs-lookup"><span data-stu-id="e5b21-139">Routing Logic</span></span>  
 <span data-ttu-id="e5b21-140">K definování směrování logikou používanou pro směrování zpráv, je třeba určit, jaké data obsažená v příchozí zprávy můžou jednoznačně reagovali na ni.</span><span class="sxs-lookup"><span data-stu-id="e5b21-140">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="e5b21-141">Například pokud všechny cílové koncové body, které jsou směrování sdílet stejné akce SOAP, hodnota akce obsažené v zpráva není vhodný indikátor které konkrétní koncového bodu zpráva by měl směrovat na.</span><span class="sxs-lookup"><span data-stu-id="e5b21-141">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="e5b21-142">Pokud pro jeden konkrétní koncový bod musí jednoznačně směrování zpráv, by měl filtrovat na datech, která jednoznačně identifikuje cílového koncového bodu, který je zpráva směrována na.</span><span class="sxs-lookup"><span data-stu-id="e5b21-142">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>  
  
 <span data-ttu-id="e5b21-143">Směrovací služby nabízí několik **MessageFilter** implementací, které prohlédnout konkrétní hodnoty ve zprávě, jako je například adresu, akce, název koncového bodu nebo i dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="e5b21-143">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="e5b21-144">Pokud žádná z těchto implementace podle svých potřeb můžete vytvořit vlastní **MessageFilter** implementace.</span><span class="sxs-lookup"><span data-stu-id="e5b21-144">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="e5b21-145">Další informace o filtry zpráv a porovnání implementace používá služba Směrování najdete v tématu [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md) a [výběr filtru](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md).</span><span class="sxs-lookup"><span data-stu-id="e5b21-145">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md) and [Choosing a Filter](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md).</span></span>  
  
 <span data-ttu-id="e5b21-146">Více filtrů zpráv jsou uspořádané do filtru tabulky, které jednotlivé přiřadit **MessageFilter** s cílový koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e5b21-146">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="e5b21-147">Volitelně filtru tabulky lze také určit seznam koncových bodů zálohování, které směrovací služby se pokusí odeslat zprávu, která se v případě selhání přenosu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-147">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>  
  
 <span data-ttu-id="e5b21-148">Ve výchozím nastavení všechny filtry zpráv v tabulce filtru se vyhodnocují současně; Můžete však zadat <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> , která způsobí filtry zpráv, který se má vyhodnotit v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="e5b21-148">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="e5b21-149">Všechny položky s nejvyšší prioritou se vyhodnocují jako první a filtry zpráv nižší priority nebudou vyhodnoceny, pokud je nalezena shoda s vyšší úrovní priority.</span><span class="sxs-lookup"><span data-stu-id="e5b21-149">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="e5b21-150">Další informace o filtru tabulky najdete v tématu [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="e5b21-150">For more information about filter tables, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md).</span></span>  
  
 <span data-ttu-id="e5b21-151">Následující příklady používají <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, který se vyhodnocuje `true` pro všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-151">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="e5b21-152">To **MessageFilter** se přidá do tabulky "routingTable1" filtr, který přidruží **MessageFilter** s koncovým bodem klienta s názvem "CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="e5b21-152">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="e5b21-153">**RoutingBehavior** pak určuje, že tato tabulka musí používat ke směrování zpráv zpracovaných v koncovém bodě služby.</span><span class="sxs-lookup"><span data-stu-id="e5b21-153">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>  
  
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
>  <span data-ttu-id="e5b21-154">Ve výchozím nastavení vyhodnotí směrovací služby pouze záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-154">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="e5b21-155">Chcete-li povolit filtry pro přístup k textu zprávy, musíte nastavit <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> k `false`.</span><span class="sxs-lookup"><span data-stu-id="e5b21-155">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>  
  
 <span data-ttu-id="e5b21-156">**Vícesměrové vysílání**</span><span class="sxs-lookup"><span data-stu-id="e5b21-156">**Multicast**</span></span>  
  
 <span data-ttu-id="e5b21-157">Při mnoho konfigurace směrování služby používat výhradní filtru logiky, která směrování zpráv do pouze jeden konkrétní koncový bod, můžete směrovat danou zprávou více cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="e5b21-157">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="e5b21-158">Pro vícesměrové vysílání zprávu pro více cílů musí být splněné následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="e5b21-158">To multicast a message to multiple destinations, the following conditions must be true:</span></span>  
  
-   <span data-ttu-id="e5b21-159">Tvar kanálu nesmí být požadavku a odpovědi (ale nemusí být jednosměrná nebo duplexní,) protože pouze jednu odpověď lze přijímat pomocí klienta aplikace v odpovědi na požadavek.</span><span class="sxs-lookup"><span data-stu-id="e5b21-159">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>  
  
-   <span data-ttu-id="e5b21-160">Více filtrů musí vracet `true` při vyhodnocování zprávy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-160">Multiple filters must return `true` when evaluating the message.</span></span>  
  
 <span data-ttu-id="e5b21-161">Pokud jsou tyto podmínky splněny, zpráva se směruje na všechny koncové body všechny filtry, která se vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="e5b21-161">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="e5b21-162">V následujícím příkladu definuje konfigurace směrování, jejímž výsledkem zprávy směrovány do obou koncových bodů, pokud je adresa koncového bodu ve zprávě http://localhost: 8000/routingservice/směrovače nebo zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="e5b21-162">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is http://localhost:8000/routingservice/router/rounding.</span></span>  
  
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
  
### <a name="soap-processing"></a><span data-ttu-id="e5b21-163">Zpracování protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="e5b21-163">SOAP Processing</span></span>  
 <span data-ttu-id="e5b21-164">Pro podporu směrování zpráv mezi odlišné protokoly **RoutingBehavior** ve výchozím nastavení přidá <xref:System.ServiceModel.Routing.SoapProcessingBehavior> pro všechny koncové klienta, které jsou směrovány zprávy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-164">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="e5b21-165">Toto chování automaticky vytvoří nový **verze MessageVersion** před směrování zprávy do koncového bodu, jakož i vytváření kompatibilní **verze MessageVersion** pro každý dokument odpovědi, před jeho vrácením aplikace vznášející požadavek klienta.</span><span class="sxs-lookup"><span data-stu-id="e5b21-165">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>  
  
 <span data-ttu-id="e5b21-166">Kroky potřebné k vytvoření nové **verze MessageVersion** odchozí zprávy jsou následující:</span><span class="sxs-lookup"><span data-stu-id="e5b21-166">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>  
  
 <span data-ttu-id="e5b21-167">**Zpracování žádosti**</span><span class="sxs-lookup"><span data-stu-id="e5b21-167">**Request processing**</span></span>  
  
-   <span data-ttu-id="e5b21-168">Získat **verze MessageVersion** odchozí vazba nebo kanálu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-168">Get the **MessageVersion** of the outbound binding/channel.</span></span>  
  
-   <span data-ttu-id="e5b21-169">Získáte čtečka textu pro původní zprávy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-169">Get the body reader for the original message.</span></span>  
  
-   <span data-ttu-id="e5b21-170">Vytvořte novou zprávu o stejnou akci, čtečky textu a novou **verze MessageVersion**.</span><span class="sxs-lookup"><span data-stu-id="e5b21-170">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>  
  
-   <span data-ttu-id="e5b21-171">Pokud <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, zkopírujte na, z FaultTo a související s záhlaví novou zprávu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-171">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
-   <span data-ttu-id="e5b21-172">Zkopírujte všechny vlastnosti zprávy do nové zprávy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-172">Copy all message properties to the new message.</span></span>  
  
-   <span data-ttu-id="e5b21-173">Uložte na původní zprávu požadavku pro použití při zpracování odpovědi.</span><span class="sxs-lookup"><span data-stu-id="e5b21-173">Store the original request message to use when processing the response.</span></span>  
  
-   <span data-ttu-id="e5b21-174">Vrátí novou zprávu požadavku.</span><span class="sxs-lookup"><span data-stu-id="e5b21-174">Return the new request message.</span></span>  
  
 <span data-ttu-id="e5b21-175">**Zpracování odpovědi**</span><span class="sxs-lookup"><span data-stu-id="e5b21-175">**Response processing**</span></span>  
  
-   <span data-ttu-id="e5b21-176">Získat **verze MessageVersion** původní zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="e5b21-176">Get the **MessageVersion** of the original request message.</span></span>  
  
-   <span data-ttu-id="e5b21-177">Získání čtečky textu zprávy přijaté odpovědi.</span><span class="sxs-lookup"><span data-stu-id="e5b21-177">Get the body reader for the received response message.</span></span>  
  
-   <span data-ttu-id="e5b21-178">Vytvoření nové zprávy odpovědi stejné akce čtečky textu a **verze MessageVersion** původní zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="e5b21-178">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>  
  
-   <span data-ttu-id="e5b21-179">Pokud <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, zkopírujte na, z FaultTo a související s záhlaví novou zprávu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-179">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
-   <span data-ttu-id="e5b21-180">Vlastnosti zprávy zkopírujte do nové zprávy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-180">Copy the message properties to the new message.</span></span>  
  
-   <span data-ttu-id="e5b21-181">Vrátí nové zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="e5b21-181">Return the new response message.</span></span>  
  
 <span data-ttu-id="e5b21-182">Ve výchozím nastavení **SoapProcessingBehavior** se automaticky přidá do koncových bodů klienta podle <xref:System.ServiceModel.Routing.RoutingBehavior> při spuštění služby; však můžete řídit, jestli je zpracování SOAP přidané do všechny koncové body klienta pomocí <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e5b21-182">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="e5b21-183">Můžete také přidat přímo na konkrétní chování a povolit nebo zakázat toto chování na úrovni koncového bodu, pokud je potřeba podrobnější řízení zpracování protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e5b21-183">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5b21-184">Pokud SOAP zpracování je zakázán pro koncový bod, který vyžaduje jinou třídu MessageVersion než původní zprávu požadavku, je nutné zadat vlastní mechanismus pro všechny změny protokolu SOAP, které jsou nutné před odesláním zprávy do cílový koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e5b21-184">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>  
  
 <span data-ttu-id="e5b21-185">V následujících příkladech **soapProcessingEnabled** vlastnost se používá při prevenci **SoapProcessingBehavior** automaticky přidat všechny koncové body klienta.</span><span class="sxs-lookup"><span data-stu-id="e5b21-185">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>  
  
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
  
### <a name="dynamic-configuration"></a><span data-ttu-id="e5b21-186">Dynamické konfigurace</span><span class="sxs-lookup"><span data-stu-id="e5b21-186">Dynamic Configuration</span></span>  
 <span data-ttu-id="e5b21-187">Je-li přidat koncové body další klienta, nebo změňte filtry, které se používají ke směrování zpráv, musí být způsob, jak aktualizovat konfiguraci dynamicky za běhu, aby se zabránilo přerušení služby aktuálně přijímání zpráv pomocí koncových bodů Služba směrování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-187">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="e5b21-188">Úprava konfigurační soubor nebo kód hostitelskou aplikaci nestačí vždy, protože buď metoda vyžaduje provedení recyklace aplikace, což by vedlo k potenciální ztrátě všechny zprávy právě přenosu a možné výpadek při Čeká se na službu restartovat.</span><span class="sxs-lookup"><span data-stu-id="e5b21-188">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>  
  
 <span data-ttu-id="e5b21-189">Upravit lze pouze **RoutingConfiguration** prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-189">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="e5b21-190">Nejdřív nakonfigurovat službu pomocí konfiguračního souboru, můžete upravit pouze konfiguraci v době běhu vytvořením nové **RoutingConfigution** a předejte ji jako parametr, který se <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> – metoda vystavené <xref:System.ServiceModel.Routing.RoutingExtension> služby rozšíření.</span><span class="sxs-lookup"><span data-stu-id="e5b21-190">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfigution** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="e5b21-191">Všechny zprávy právě přenosu nadále ho směrovat pomocí předchozí konfiguraci při zprávy přijaté po volání **ApplyConfiguration** použít novou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e5b21-191">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="e5b21-192">Následující příklad ukazuje vytvoření instance služby Směrování a následně změna konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e5b21-192">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>  
  
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
>  <span data-ttu-id="e5b21-193">Při aktualizaci služby směrování tímto způsobem je jenom možné předat novou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e5b21-193">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="e5b21-194">Není možné změnit pouze vyberte prvky aktuální konfigurace nebo přidání nových položek pro aktuální konfiguraci; musíte vytvořit a předat novou konfiguraci, který nahrazuje stávající.</span><span class="sxs-lookup"><span data-stu-id="e5b21-194">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5b21-195">Všechny relace otevřené pomocí předchozí konfiguraci pokračovat pomocí předchozí konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e5b21-195">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="e5b21-196">Nová konfigurace se používá pouze pomocí nové relace.</span><span class="sxs-lookup"><span data-stu-id="e5b21-196">The new configuration is only used by new sessions.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="e5b21-197">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="e5b21-197">Error Handling</span></span>  
 <span data-ttu-id="e5b21-198">Pokud existuje <xref:System.ServiceModel.CommunicationException> je došlo při pokusu o odeslání zprávy, proveďte místní zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="e5b21-198">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="e5b21-199">Tyto výjimky typicky značí, že došlo k potížím při pokusu o komunikaci s koncového bodu definovaného klienta, například <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, nebo <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="e5b21-199">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="e5b21-200">Zpracování – kód chyby se také catch a pokus opakovat při odesílání <xref:System.TimeoutException> dojde, což je další běžné výjimku, který není odvozen od **communicationexception –**.</span><span class="sxs-lookup"><span data-stu-id="e5b21-200">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>  
  
 <span data-ttu-id="e5b21-201">Když dojde k některé z předchozích výjimek, směrovací služby převezme na seznam zálohování koncové body.</span><span class="sxs-lookup"><span data-stu-id="e5b21-201">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="e5b21-202">Pokud všechny koncové body zálohování nezdaří s chybou komunikace, nebo pokud koncový bod vrací výjimku, která indikuje selhání v rámci cílové služby, směrovací služby vrátí chybu do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5b21-202">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5b21-203">Zpracování chyb funkce zaznamená a zpracovává výjimky, které ke kterým dochází při pokusu o odeslání zprávy a při pokusu o zavření kanálu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-203">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="e5b21-204">Kód pro ošetření chyb není určena pro zjišťování nebo zpracování výjimek vytvořených koncových bodů aplikace, které je komunikaci s; <xref:System.ServiceModel.FaultException> vyvolané služby se zobrazuje na směrování služby jako **FaultMessage** a je plynoucích zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="e5b21-204">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>  
>   
>  <span data-ttu-id="e5b21-205">Pokud dojde k chybě při směrování služba se pokusí předávání zprávu, může dojít <xref:System.ServiceModel.FaultException> na straně klienta, ne <xref:System.ServiceModel.EndpointNotFoundException> by za normálních okolností získat chybí službu směrování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-205">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="e5b21-206">Směrovací služba může proto maskování výjimky a neposkytuje plnou průhlednost, není-li prověřit vnořené výjimky.</span><span class="sxs-lookup"><span data-stu-id="e5b21-206">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>  
  
### <a name="tracing-exceptions"></a><span data-ttu-id="e5b21-207">Trasování výjimky</span><span class="sxs-lookup"><span data-stu-id="e5b21-207">Tracing Exceptions</span></span>  
 <span data-ttu-id="e5b21-208">Při odesílání zprávy do koncového bodu v seznamu se nezdaří, směrovací služby trasování Výsledná data výjimky a připojí podrobnosti o výjimce jako vlastnost zprávu s názvem **výjimky**.</span><span class="sxs-lookup"><span data-stu-id="e5b21-208">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="e5b21-209">To zachovává data výjimky a umožňuje programový přístup uživatelů prostřednictvím inspector zprávy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-209">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="e5b21-210">Výjimka data se ukládají na zprávu ve slovník, který mapuje název koncového bodu na podrobnosti o výjimce došlo při pokusu o odeslání zprávy do něj.</span><span class="sxs-lookup"><span data-stu-id="e5b21-210">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>  
  
### <a name="backup-endpoints"></a><span data-ttu-id="e5b21-211">Zálohování koncové body</span><span class="sxs-lookup"><span data-stu-id="e5b21-211">Backup Endpoints</span></span>  
 <span data-ttu-id="e5b21-212">Každý záznam filtru v tabulce filtru můžete volitelně zadat seznam zálohování koncových bodů, které se používají v případě selhání přenosu při odesílání na primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e5b21-212">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="e5b21-213">Pokud dojde k takové selhání, pokusí se službu směrování přenosu zprávy první položce v seznamu zálohování koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e5b21-213">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="e5b21-214">Pokud tento pokus o odeslání taky zaznamená selhání přenosu, zkusí se další koncového bodu v záložním seznamu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-214">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="e5b21-215">Směrovací služby pokračuje v odesílání zprávy na každý koncový bod v seznamu, dokud zpráva se úspěšně přijme, všechny koncové body vrátí chybu přenosu nebo jiný přenos selhání je vrácen rutinou koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e5b21-215">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>  
  
 <span data-ttu-id="e5b21-216">V následujících příkladech konfiguruje službu směrování na používání zálohování seznamu.</span><span class="sxs-lookup"><span data-stu-id="e5b21-216">The following examples configure the Routing Service to use a backup list.</span></span>  
  
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
  
### <a name="supported-error-patterns"></a><span data-ttu-id="e5b21-217">Vzory podporované chyby</span><span class="sxs-lookup"><span data-stu-id="e5b21-217">Supported Error Patterns</span></span>  
 <span data-ttu-id="e5b21-218">Následující tabulka popisuje vzorů, které jsou kompatibilní s použitím seznamů zálohování koncový bod, společně s poznámky popisující podrobnosti o zpracování chyb pro určité vzory.</span><span class="sxs-lookup"><span data-stu-id="e5b21-218">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>  
  
|<span data-ttu-id="e5b21-219">Vzor</span><span class="sxs-lookup"><span data-stu-id="e5b21-219">Pattern</span></span>|<span data-ttu-id="e5b21-220">Relace</span><span class="sxs-lookup"><span data-stu-id="e5b21-220">Session</span></span>|<span data-ttu-id="e5b21-221">Transakce</span><span class="sxs-lookup"><span data-stu-id="e5b21-221">Transaction</span></span>|<span data-ttu-id="e5b21-222">Přijímat kontextu</span><span class="sxs-lookup"><span data-stu-id="e5b21-222">Receive Context</span></span>|<span data-ttu-id="e5b21-223">Zálohování seznamu podporována</span><span class="sxs-lookup"><span data-stu-id="e5b21-223">Backup List Supported</span></span>|<span data-ttu-id="e5b21-224">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5b21-224">Notes</span></span>|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|<span data-ttu-id="e5b21-225">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="e5b21-225">One-Way</span></span>||||<span data-ttu-id="e5b21-226">Ano</span><span class="sxs-lookup"><span data-stu-id="e5b21-226">Yes</span></span>|<span data-ttu-id="e5b21-227">Pokusí se znovu odeslat zprávu na koncový bod zálohování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-227">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="e5b21-228">Pokud je tato zpráva vícesměrového vysílání, pouze zprávu na selhání kanálu je přesunout do cíle zálohování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-228">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|  
|<span data-ttu-id="e5b21-229">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="e5b21-229">One-Way</span></span>||<span data-ttu-id="e5b21-230">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-230">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="e5b21-231">Ne</span><span class="sxs-lookup"><span data-stu-id="e5b21-231">No</span></span>|<span data-ttu-id="e5b21-232">Je vyvolána výjimka, a transakce je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="e5b21-232">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="e5b21-233">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="e5b21-233">One-Way</span></span>|||<span data-ttu-id="e5b21-234">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-234">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="e5b21-235">Ano</span><span class="sxs-lookup"><span data-stu-id="e5b21-235">Yes</span></span>|<span data-ttu-id="e5b21-236">Pokusí se znovu odeslat zprávu na koncový bod zálohování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-236">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="e5b21-237">Po zpráva se úspěšně přijatá, dokončení všech zobrazí kontexty.</span><span class="sxs-lookup"><span data-stu-id="e5b21-237">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="e5b21-238">Pokud zpráva není úspěšně přijme žádný koncový bod, neprovádějte kontext receive.</span><span class="sxs-lookup"><span data-stu-id="e5b21-238">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="e5b21-239">Když se tato zpráva vícesměrového vysílání, kontext receive je vyplněno pouze pokud zpráva se úspěšně přijme aspoň jeden koncový bod (primární nebo zálohování).</span><span class="sxs-lookup"><span data-stu-id="e5b21-239">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="e5b21-240">Pokud žádná z koncových bodů ve všech vícesměrového vysílání cestách úspěšně zobrazí zpráva, neprovádějte kontext receive.</span><span class="sxs-lookup"><span data-stu-id="e5b21-240">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|  
|<span data-ttu-id="e5b21-241">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="e5b21-241">One-Way</span></span>||<span data-ttu-id="e5b21-242">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-242">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="e5b21-243">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-243">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="e5b21-244">Ano</span><span class="sxs-lookup"><span data-stu-id="e5b21-244">Yes</span></span>|<span data-ttu-id="e5b21-245">Abort předchozí transakce, vytvořte novou transakci a znovu odeslat všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-245">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="e5b21-246">Zprávy, které došlo k chybě, se přenáší do cílového umístění zálohy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-246">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="e5b21-247">Po vytvoření transakce ve které všechny přenosy úspěšné dokončete kontexty příjmu a potvrzení transakce.</span><span class="sxs-lookup"><span data-stu-id="e5b21-247">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|  
|<span data-ttu-id="e5b21-248">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="e5b21-248">One-Way</span></span>|<span data-ttu-id="e5b21-249">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-249">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|||<span data-ttu-id="e5b21-250">Ano</span><span class="sxs-lookup"><span data-stu-id="e5b21-250">Yes</span></span>|<span data-ttu-id="e5b21-251">Pokusí se znovu odeslat zprávu na koncový bod zálohování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-251">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="e5b21-252">V případě vícesměrového vysílání jsou pouze zprávy, že došlo k chybě v relaci nebo relaci zavřete jehož relace se nezdařilo nutno do cíle zálohování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-252">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|  
|<span data-ttu-id="e5b21-253">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="e5b21-253">One-Way</span></span>|<span data-ttu-id="e5b21-254">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-254">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="e5b21-255">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-255">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="e5b21-256">Ne</span><span class="sxs-lookup"><span data-stu-id="e5b21-256">No</span></span>|<span data-ttu-id="e5b21-257">Je vyvolána výjimka, a transakce je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="e5b21-257">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="e5b21-258">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="e5b21-258">One-Way</span></span>|<span data-ttu-id="e5b21-259">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-259">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="e5b21-260">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-260">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="e5b21-261">Ano</span><span class="sxs-lookup"><span data-stu-id="e5b21-261">Yes</span></span>|<span data-ttu-id="e5b21-262">Pokusí se znovu odeslat zprávu na koncový bod zálohování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-262">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="e5b21-263">Po všechny zprávy odesílá dokončení bez chyby, relace určuje žádné další zprávy a směrovací služby úspěšně zavře všechny odchozí relace linek, všechny obdrží kontexty jsou dokončeny, a kanál příchozí relace je uzavřený.</span><span class="sxs-lookup"><span data-stu-id="e5b21-263">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|  
|<span data-ttu-id="e5b21-264">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="e5b21-264">One-Way</span></span>|<span data-ttu-id="e5b21-265">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-265">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="e5b21-266">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-266">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="e5b21-267">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-267">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="e5b21-268">Ano</span><span class="sxs-lookup"><span data-stu-id="e5b21-268">Yes</span></span>|<span data-ttu-id="e5b21-269">Přerušit aktuální transakci a vytvořte novou.</span><span class="sxs-lookup"><span data-stu-id="e5b21-269">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="e5b21-270">Odešlete ji znova všechny předchozí zprávy v relaci.</span><span class="sxs-lookup"><span data-stu-id="e5b21-270">Resend all previous messages in the session.</span></span> <span data-ttu-id="e5b21-271">Po transakce vytvořila ve kterém mají byl úspěšně odeslán všechny zprávy relace určuje, že žádné další zprávy, všechny kanály odchozí relace zavřou, přijímat všechny kontexty se dokončila s transakcí, kanál příchozí relace je zavřená, a že je transakce potvrzena.</span><span class="sxs-lookup"><span data-stu-id="e5b21-271">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="e5b21-272">Pokud bude relací vícesměrového vysílání, které jsou ke stejnému cíli jako před nutno zprávy, které měl žádná chyba a zprávy, které došlo k chybě odešlou do cíle zálohování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-272">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|  
|<span data-ttu-id="e5b21-273">Obousměrné</span><span class="sxs-lookup"><span data-stu-id="e5b21-273">Two-Way</span></span>||||<span data-ttu-id="e5b21-274">Ano</span><span class="sxs-lookup"><span data-stu-id="e5b21-274">Yes</span></span>|<span data-ttu-id="e5b21-275">Odeslat do cílového umístění zálohy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-275">Send to a backup destination.</span></span>  <span data-ttu-id="e5b21-276">Po kanál, který vrátí zprávu odpovědi, vrátí odpověď na původní klienta.</span><span class="sxs-lookup"><span data-stu-id="e5b21-276">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="e5b21-277">Obousměrné</span><span class="sxs-lookup"><span data-stu-id="e5b21-277">Two-Way</span></span>|<span data-ttu-id="e5b21-278">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-278">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|||<span data-ttu-id="e5b21-279">Ano</span><span class="sxs-lookup"><span data-stu-id="e5b21-279">Yes</span></span>|<span data-ttu-id="e5b21-280">Odešlete všechny zprávy na kanálu cíl zálohy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-280">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="e5b21-281">Po kanál, který vrátí zprávu odpovědi, vrátí odpověď na původní klienta.</span><span class="sxs-lookup"><span data-stu-id="e5b21-281">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="e5b21-282">Obousměrné</span><span class="sxs-lookup"><span data-stu-id="e5b21-282">Two-Way</span></span>||<span data-ttu-id="e5b21-283">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-283">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="e5b21-284">Ne</span><span class="sxs-lookup"><span data-stu-id="e5b21-284">No</span></span>|<span data-ttu-id="e5b21-285">Je vyvolána výjimka, a transakce je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="e5b21-285">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="e5b21-286">Obousměrné</span><span class="sxs-lookup"><span data-stu-id="e5b21-286">Two-Way</span></span>|<span data-ttu-id="e5b21-287">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-287">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="e5b21-288">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-288">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="e5b21-289">Ne</span><span class="sxs-lookup"><span data-stu-id="e5b21-289">No</span></span>|<span data-ttu-id="e5b21-290">Je vyvolána výjimka, a transakce je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="e5b21-290">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="e5b21-291">Duplex</span><span class="sxs-lookup"><span data-stu-id="e5b21-291">Duplex</span></span>||||<span data-ttu-id="e5b21-292">Ne</span><span class="sxs-lookup"><span data-stu-id="e5b21-292">No</span></span>|<span data-ttu-id="e5b21-293">Duplexní komunikace non relace se aktuálně nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="e5b21-293">Non-session duplex communication is not currently supported.</span></span>|  
|<span data-ttu-id="e5b21-294">Duplex</span><span class="sxs-lookup"><span data-stu-id="e5b21-294">Duplex</span></span>|<span data-ttu-id="e5b21-295">![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")</span><span class="sxs-lookup"><span data-stu-id="e5b21-295">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|||<span data-ttu-id="e5b21-296">Ano</span><span class="sxs-lookup"><span data-stu-id="e5b21-296">Yes</span></span>|<span data-ttu-id="e5b21-297">Odeslat do cílového umístění zálohy.</span><span class="sxs-lookup"><span data-stu-id="e5b21-297">Send to a backup destination.</span></span>|  
  
## <a name="hosting"></a><span data-ttu-id="e5b21-298">Hostování</span><span class="sxs-lookup"><span data-stu-id="e5b21-298">Hosting</span></span>  
 <span data-ttu-id="e5b21-299">Protože směrovací služby je implementovaná jako služby WCF, musí to být buď samoobslužně hostované v rámci aplikace nebo hostované služby IIS nebo WAS.</span><span class="sxs-lookup"><span data-stu-id="e5b21-299">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="e5b21-300">Doporučuje se, že směrovací služby hostované ve služby IIS, WAS nebo aplikace služby systému Windows využívat výhod automatické spuštění a životního cyklu správy funkce dostupné v těchto hostitelská prostředí.</span><span class="sxs-lookup"><span data-stu-id="e5b21-300">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>  
  
 <span data-ttu-id="e5b21-301">Následující příklad ukazuje, který je hostitelem služby směrování v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e5b21-301">The following example demonstrates hosting the Routing Service in an application.</span></span>  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 <span data-ttu-id="e5b21-302">K hostování služby směrování v rámci služby IIS nebo WAS, musíte vytvořit soubor služby (SVC) nebo použít aktivaci prostřednictvím konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="e5b21-302">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="e5b21-303">Při použití souboru služby, je nutné zadat <xref:System.ServiceModel.Routing.RoutingService> pomocí parametru služby.</span><span class="sxs-lookup"><span data-stu-id="e5b21-303">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="e5b21-304">Následující příklad obsahuje ukázkový soubor služby, které je možné k hostování služby IIS nebo WAS směrování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-304">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a><span data-ttu-id="e5b21-305">Služba Směrování a zosobnění</span><span class="sxs-lookup"><span data-stu-id="e5b21-305">Routing Service and Impersonation</span></span>  
 <span data-ttu-id="e5b21-306">Směrovací služby WCF můžete použít s zosobnění pro odesílání a přijímání zpráv.</span><span class="sxs-lookup"><span data-stu-id="e5b21-306">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="e5b21-307">Použít všechny obvyklé omezení Windows zosobnění.</span><span class="sxs-lookup"><span data-stu-id="e5b21-307">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="e5b21-308">Pokud by musel nastavení účtu služby nebo oprávnění k použití zosobnění při zápisu vlastní služby, pak budete muset provést tyto stejné kroky při použití zosobnění se směrovací službou.</span><span class="sxs-lookup"><span data-stu-id="e5b21-308">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="e5b21-309">Další informace najdete v tématu [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="e5b21-309">For more information, see [Delegation and Impersonation](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="e5b21-310">Zosobnění se směrovací službou vyžaduje použití zosobnění technologie ASP.NET v režimu kompatibility ASP.NET nebo použití pověření systému Windows, které byly nakonfigurovány k povolení zosobnění.</span><span class="sxs-lookup"><span data-stu-id="e5b21-310">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="e5b21-311">Další informace o režim kompatibility ASP.NET najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="e5b21-311">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="e5b21-312">Směrovací služby WCF nepodporuje zosobnění se základním ověřováním.</span><span class="sxs-lookup"><span data-stu-id="e5b21-312">The WCF Routing Service does not support impersonation with basic authentication.</span></span>  
  
 <span data-ttu-id="e5b21-313">Chcete-li použít zosobnění technologie ASP.NET se službou směrování, povolte režim kompatibility ASP.NET ve službě hostování prostředí.</span><span class="sxs-lookup"><span data-stu-id="e5b21-313">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="e5b21-314">Směrovací služba již byl označen jako což režim kompatibility ASP.NET a zosobnění budou automaticky povolené.</span><span class="sxs-lookup"><span data-stu-id="e5b21-314">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="e5b21-315">Zosobnění je používat jenom podporované ASP.NET integrace se službou směrování.</span><span class="sxs-lookup"><span data-stu-id="e5b21-315">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>  
  
 <span data-ttu-id="e5b21-316">Použití zosobnění pro pověření systému Windows se směrovací službou musíte nakonfigurovat přihlašovací údaje a služby.</span><span class="sxs-lookup"><span data-stu-id="e5b21-316">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="e5b21-317">Objekt pověření klienta (<xref:System.ServiceModel.Security.WindowsClientCredential>, přístupný z <xref:System.ServiceModel.ChannelFactory>) definuje <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost, která musí být nastavena tak, aby povolovala zosobnění.</span><span class="sxs-lookup"><span data-stu-id="e5b21-317">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="e5b21-318">Nakonec služby je nutné nakonfigurovat <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> chování nastavit `ImpersonateCallerForAllOperations` k `true`.</span><span class="sxs-lookup"><span data-stu-id="e5b21-318">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="e5b21-319">Směrovací služba používá tento příznak se rozhodnout, jestli se mají vytvořit klienty pro předávání zpráv s zosobnění povoleno.</span><span class="sxs-lookup"><span data-stu-id="e5b21-319">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b21-320">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5b21-320">See Also</span></span>  
 [<span data-ttu-id="e5b21-321">Filtry zpráv</span><span class="sxs-lookup"><span data-stu-id="e5b21-321">Message Filters</span></span>](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [<span data-ttu-id="e5b21-322">Kontrakty pro směrování</span><span class="sxs-lookup"><span data-stu-id="e5b21-322">Routing Contracts</span></span>](../../../../docs/framework/wcf/feature-details/routing-contracts.md)  
 [<span data-ttu-id="e5b21-323">Výběr filtru</span><span class="sxs-lookup"><span data-stu-id="e5b21-323">Choosing a Filter</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md)
