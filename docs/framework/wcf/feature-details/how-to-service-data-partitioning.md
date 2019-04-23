---
title: 'Postupy: Vytvoření oddílů dat služby'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 17cb80bf253491eb563d6fd45b5997e452f542e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300382"
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="89621-102">Postupy: Vytvoření oddílů dat služby</span><span class="sxs-lookup"><span data-stu-id="89621-102">How To: Service Data Partitioning</span></span>
<span data-ttu-id="89621-103">Toto téma popisuje základní kroky potřebné k oddílu zprávy do několika instancí stejné cílové služby.</span><span class="sxs-lookup"><span data-stu-id="89621-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="89621-104">Dělení dat služby se obvykle používá, když budete chtít škálování služby, aby bylo možné poskytovat lepší kvalitu služby, nebo pokud potřebujete zpracovávat požadavky různých zákazníků určitým způsobem.</span><span class="sxs-lookup"><span data-stu-id="89621-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="89621-105">Zprávy z vysoké hodnoty nebo zákazníky za "Zlatá" může například potřeba zpracovat s vyšší prioritou než zpráv od standardní zákazníka.</span><span class="sxs-lookup"><span data-stu-id="89621-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="89621-106">V tomto příkladu zprávy jsou směrovány na jednu ze dvou instancí služby regularCalc.</span><span class="sxs-lookup"><span data-stu-id="89621-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="89621-107">Obě instance služby jsou identické; ale reprezentované zprávami procesy calculator1 koncový bod služby obdrželi od zákazníků vysoké hodnoty, koncový bod Kalkulačka 2 procesy zpráv od ostatních zákazníků</span><span class="sxs-lookup"><span data-stu-id="89621-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="89621-108">Z klienta byla odeslána zpráva nemá jedinečných dat, který můžete použít k identifikaci které se mají směrovat zprávy k instanci služby.</span><span class="sxs-lookup"><span data-stu-id="89621-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="89621-109">Povolit každá klient data trasy pro konkrétní cílové služby Implementujeme dva koncové body služby, které se použijí pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="89621-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89621-110">Přestože tento příklad používá konkrétní koncové body k dělení dat, to může také provést pomocí informací obsažených v rámci vlastní zprávě například Hlavička nebo text data.</span><span class="sxs-lookup"><span data-stu-id="89621-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="89621-111">Dělení dat implementace služby</span><span class="sxs-lookup"><span data-stu-id="89621-111">Implement Service Data Partitioning</span></span>  
  
1. <span data-ttu-id="89621-112">Vytvoření základní konfigurace služby směrování zadat koncové body služby určeného službou.</span><span class="sxs-lookup"><span data-stu-id="89621-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="89621-113">Následující příklad definuje dva koncové body, které se budou používat pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="89621-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="89621-114">Také definuje koncové body klienta, které se používají k odesílání zpráv do instance služby regularCalc.</span><span class="sxs-lookup"><span data-stu-id="89621-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
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
  
2. <span data-ttu-id="89621-115">Určit filtry, které slouží ke směrování zpráv do cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="89621-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="89621-116">V tomto příkladu Název_koncového_bodu filtr slouží k určení, které koncový bod služby zobrazila zpráva.</span><span class="sxs-lookup"><span data-stu-id="89621-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="89621-117">Následující příklad definuje oddíl nezbytné směrování a filtry.</span><span class="sxs-lookup"><span data-stu-id="89621-117">The following example defines the necessary routing section and filters.</span></span>  
  
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
  
3. <span data-ttu-id="89621-118">Definujte filtr tabulky, který každý filtr přidruží koncový bod klienta.</span><span class="sxs-lookup"><span data-stu-id="89621-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="89621-119">V tomto příkladu budou směrovat zprávy na základě konkrétní koncového bodu, který byl přijat přes.</span><span class="sxs-lookup"><span data-stu-id="89621-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="89621-120">Vzhledem k tomu, že zpráva odpovídá pouze jeden z filtrů dva možné, není nutné pro řídit pořadí, ve které filtry jsou vyhodnocovány pomocí Priorita filtru.</span><span class="sxs-lookup"><span data-stu-id="89621-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="89621-121">Následující definuje filtr tabulky a přidá filtry definovali dříve.</span><span class="sxs-lookup"><span data-stu-id="89621-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="89621-122">Vyhodnocování příchozích zpráv proti filtry, které jsou obsaženy v tabulce, musíte přidružit tabulky filtru koncových bodů služby pomocí směrování chování.</span><span class="sxs-lookup"><span data-stu-id="89621-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="89621-123">Následující příklad ukazuje přiřazování "filterTable1" s koncovými body služby:</span><span class="sxs-lookup"><span data-stu-id="89621-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="89621-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="89621-124">Example</span></span>  
 <span data-ttu-id="89621-125">Tady je úplný seznam všech konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="89621-125">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89621-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89621-126">See also</span></span>

- [<span data-ttu-id="89621-127">Směrovací služby</span><span class="sxs-lookup"><span data-stu-id="89621-127">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
