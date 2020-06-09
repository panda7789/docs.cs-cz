---
title: 'Postupy: Vytvoření oddílů dat služby'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 3b2f86ee6a4dea25fb5c972d4cecb1b9ed411b29
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601189"
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="a875c-102">Postupy: Vytvoření oddílů dat služby</span><span class="sxs-lookup"><span data-stu-id="a875c-102">How To: Service Data Partitioning</span></span>
<span data-ttu-id="a875c-103">Toto téma popisuje základní kroky potřebné k rozdělení zpráv mezi více instancí stejné cílové služby.</span><span class="sxs-lookup"><span data-stu-id="a875c-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="a875c-104">Vytváření oddílů dat služby se obvykle používá v případě, že potřebujete škálovat službu tak, aby poskytovala lepší kvalitu služeb, nebo když potřebujete konkrétní způsob zpracovávat žádosti od různých zákazníků.</span><span class="sxs-lookup"><span data-stu-id="a875c-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="a875c-105">Například zprávy od vysoké hodnoty nebo "Gold" můžou být potřeba zpracovat s vyšší prioritou než zprávy ze standardního zákazníka.</span><span class="sxs-lookup"><span data-stu-id="a875c-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="a875c-106">V tomto příkladu jsou zprávy směrovány do jedné ze dvou instancí služby regularCalc.</span><span class="sxs-lookup"><span data-stu-id="a875c-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="a875c-107">Obě instance služby jsou identické. Nicméně služba reprezentovaná koncovým bodem calculator1 zpracovává zprávy obdržené od zákazníků s vysokou hodnotou a koncovým bodem kalkulačky zpracovává zprávy od jiných zákazníků.</span><span class="sxs-lookup"><span data-stu-id="a875c-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="a875c-108">Zpráva odeslaná z klienta neobsahuje žádná jedinečná data, která by bylo možné použít k identifikaci instance služby, na kterou se má zpráva směrovat.</span><span class="sxs-lookup"><span data-stu-id="a875c-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="a875c-109">Aby každý klient mohl směrovat data do konkrétní cílové služby, implementujeme dva koncové body služby, které budou použity pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="a875c-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a875c-110">I když tento příklad používá ke dělení dat konkrétní koncové body, může to být také provedeno pomocí informací obsažených v samotné zprávě, jako jsou například záhlaví nebo textová data.</span><span class="sxs-lookup"><span data-stu-id="a875c-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="a875c-111">Implementace dělení dat služby</span><span class="sxs-lookup"><span data-stu-id="a875c-111">Implement Service Data Partitioning</span></span>  
  
1. <span data-ttu-id="a875c-112">Vytvořte základní konfiguraci směrovací služby zadáním koncových bodů služby vystavených službou.</span><span class="sxs-lookup"><span data-stu-id="a875c-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="a875c-113">Následující příklad definuje dva koncové body, které budou použity pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="a875c-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="a875c-114">Také definuje koncové body klienta, které slouží k posílání zpráv do instancí služby regularCalc.</span><span class="sxs-lookup"><span data-stu-id="a875c-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
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
  
2. <span data-ttu-id="a875c-115">Definujte filtry používané ke směrování zpráv do cílových koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="a875c-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="a875c-116">V tomto příkladu se používá filtr koncového bodu k určení, který koncový bod služby obdržel zprávu.</span><span class="sxs-lookup"><span data-stu-id="a875c-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="a875c-117">Následující příklad definuje nezbytný oddíl směrování a filtry.</span><span class="sxs-lookup"><span data-stu-id="a875c-117">The following example defines the necessary routing section and filters.</span></span>  
  
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
  
3. <span data-ttu-id="a875c-118">Definujte tabulku filtru, která přidruží jednotlivé filtry ke koncovému bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="a875c-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="a875c-119">V tomto příkladu bude zpráva směrována podle konkrétního koncového bodu, ve kterém byla přijata.</span><span class="sxs-lookup"><span data-stu-id="a875c-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="a875c-120">Vzhledem k tomu, že zpráva může odpovídat pouze jednomu ze dvou možných filtrů, není nutné používat prioritu filtru k řízení pořadí, ve kterém jsou filtry vyhodnocovány.</span><span class="sxs-lookup"><span data-stu-id="a875c-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="a875c-121">Následující definice tabulky filtru a přidává filtry definované dříve.</span><span class="sxs-lookup"><span data-stu-id="a875c-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="a875c-122">Chcete-li vyhodnotit příchozí zprávy proti filtrům obsaženým v tabulce, je nutné přidružit tabulku filtru k koncovým bodům služby pomocí chování směrování.</span><span class="sxs-lookup"><span data-stu-id="a875c-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="a875c-123">Následující příklad ukazuje přidružení "filterTable1" k koncovým bodům služby:</span><span class="sxs-lookup"><span data-stu-id="a875c-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="a875c-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="a875c-124">Example</span></span>  
 <span data-ttu-id="a875c-125">Následuje úplný seznam konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a875c-125">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a875c-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a875c-126">See also</span></span>

- [<span data-ttu-id="a875c-127">Směrovací služby</span><span class="sxs-lookup"><span data-stu-id="a875c-127">Routing Services</span></span>](../samples/routing-services.md)
