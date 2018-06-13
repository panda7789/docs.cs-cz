---
title: 'Postupy: Vytvoření oddílů dat služby'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 47e84555e38d2a71b7741c18de5f67349a622798
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491798"
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="26b8b-102">Postupy: Vytvoření oddílů dat služby</span><span class="sxs-lookup"><span data-stu-id="26b8b-102">How To: Service Data Partitioning</span></span>
<span data-ttu-id="26b8b-103">Toto téma popisuje základní kroky potřebné k oddílu zprávy ve více instancích stejné cílové služby.</span><span class="sxs-lookup"><span data-stu-id="26b8b-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="26b8b-104">Dělení na oddíly dat služby se obvykle používá, když potřebujete škálování služby, chcete-li poskytovat lepší kvalitu služby, nebo když potřebujete zpracování požadavků různých zákazníků, určitým způsobem.</span><span class="sxs-lookup"><span data-stu-id="26b8b-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="26b8b-105">Zprávy ze vysoké hodnoty nebo zákazníků "Zlatá" možná muset zpracovat vyšší prioritu než zprávy od standardní zákazníka.</span><span class="sxs-lookup"><span data-stu-id="26b8b-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="26b8b-106">V tomto příkladu zprávy jsou směrovány do jednoho z dvě instance služby regularCalc.</span><span class="sxs-lookup"><span data-stu-id="26b8b-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="26b8b-107">Obou instancí služby jsou identické; ale služba reprezentována zprávy calculator1 koncový bod procesy přijala od zákazníků vysoké hodnoty, koncový bod kalkulačky 2 procesy zprávy od dalších zákazníků</span><span class="sxs-lookup"><span data-stu-id="26b8b-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="26b8b-108">Zpráv odeslaných z klienta nemá žádné jedinečným datům, která slouží k identifikaci které zpráva by měl směrovat na instanci služby.</span><span class="sxs-lookup"><span data-stu-id="26b8b-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="26b8b-109">Povolit každého klienta pro data trasy pro konkrétní cílové služby bude implementaci dva koncové body služby, které se použijí pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="26b8b-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26b8b-110">Tento příklad používá konkrétní koncové body k oddílu dat, to také je možné dosáhnout pomocí informací obsažených v rámci samotnou zprávu například dat Hlavička nebo text.</span><span class="sxs-lookup"><span data-stu-id="26b8b-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="26b8b-111">Dělení na oddíly dat služby implementace</span><span class="sxs-lookup"><span data-stu-id="26b8b-111">Implement Service Data Partitioning</span></span>  
  
1.  <span data-ttu-id="26b8b-112">Vytvořte základní konfigurace směrování služby zadáním koncové body služby, který je zveřejněný prostřednictvím služby.</span><span class="sxs-lookup"><span data-stu-id="26b8b-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="26b8b-113">V následujícím příkladu definuje dva koncové body, které se použije pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="26b8b-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="26b8b-114">Definuje také koncové body klientů, které se používají k odesílání zpráv do instance služby regularCalc.</span><span class="sxs-lookup"><span data-stu-id="26b8b-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
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
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
       </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
        <endpoint name="CalcEndpoint1"  
                  address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
  
        <endpoint name="CalcEndpoint2"  
                  address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
     </client>  
    ```  
  
2.  <span data-ttu-id="26b8b-115">Zadejte filtry slouží ke směrování zpráv do cílového koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="26b8b-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="26b8b-116">V tomto příkladu filtru EndpointName slouží k určení, které koncový bod služby zobrazila zpráva.</span><span class="sxs-lookup"><span data-stu-id="26b8b-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="26b8b-117">V následujícím příkladu definuje nezbytné směrování části a filtry.</span><span class="sxs-lookup"><span data-stu-id="26b8b-117">The following example defines the necessary routing section and filters.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the different message filters-->  
      <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
      <filter name="HighPriority" filterType="EndpointName"  
              filterData="calculator1Endpoint"/>  
      <filter name="NormalPriority" filterType="EndpointName"  
              filterData="calculator2Endpoint"/>  
    </filters>  
    ```  
  
3.  <span data-ttu-id="26b8b-118">Definujte tabulku filtru, který přidruží každý filtr koncový bod klienta.</span><span class="sxs-lookup"><span data-stu-id="26b8b-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="26b8b-119">V tomto příkladu budou směrovány zprávy založené na konkrétní koncový bod, který byl přijat přes.</span><span class="sxs-lookup"><span data-stu-id="26b8b-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="26b8b-120">Vzhledem k tomu, že zpráva odpovídá pouze jeden dva možné filtry, není nutné pro použití s prioritou filtru k řízení pořadí, ve které filtry jsou vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="26b8b-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="26b8b-121">Následující tabulku filtru definuje a přidá filtry definované dříve.</span><span class="sxs-lookup"><span data-stu-id="26b8b-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4.  <span data-ttu-id="26b8b-122">Pokud chcete vyhodnotit příchozí zprávy před filtry, které jsou obsaženy v tabulce, je třeba přidružit tabulku filtru koncové body služby pomocí směrování chování.</span><span class="sxs-lookup"><span data-stu-id="26b8b-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="26b8b-123">Následující příklad ukazuje přiřadit "filterTable1" s koncovými body služby:</span><span class="sxs-lookup"><span data-stu-id="26b8b-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="26b8b-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="26b8b-124">Example</span></span>  
 <span data-ttu-id="26b8b-125">Níže je úplný seznam všech konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="26b8b-125">The following is a complete listing of the configuration file.</span></span>  
  
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
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
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
      <endpoint name="CalcEndpoint1"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="CalcEndpoint2"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
  
      <filters>  
        <!--define the different message filters-->  
        <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
        <filter name="HighPriority" filterType="EndpointName"  
                filterData="calculator1Endpoint"/>  
        <filter name="NormalPriority" filterType="EndpointName"  
                filterData="calculator2Endpoint"/>  
      </filters>  
  
      <filterTables>  
        <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
          <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
        </filterTable>  
      </filterTables>  
  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26b8b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="26b8b-126">See Also</span></span>  
 [<span data-ttu-id="26b8b-127">Směrovací služby</span><span class="sxs-lookup"><span data-stu-id="26b8b-127">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
