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
# <a name="how-to-service-data-partitioning"></a>Postupy: Vytvoření oddílů dat služby
Toto téma popisuje základní kroky potřebné k oddílu zprávy ve více instancích stejné cílové služby. Dělení na oddíly dat služby se obvykle používá, když potřebujete škálování služby, chcete-li poskytovat lepší kvalitu služby, nebo když potřebujete zpracování požadavků různých zákazníků, určitým způsobem. Zprávy ze vysoké hodnoty nebo zákazníků "Zlatá" možná muset zpracovat vyšší prioritu než zprávy od standardní zákazníka.  
  
 V tomto příkladu zprávy jsou směrovány do jednoho z dvě instance služby regularCalc. Obou instancí služby jsou identické; ale služba reprezentována zprávy calculator1 koncový bod procesy přijala od zákazníků vysoké hodnoty, koncový bod kalkulačky 2 procesy zprávy od dalších zákazníků  
  
 Zpráv odeslaných z klienta nemá žádné jedinečným datům, která slouží k identifikaci které zpráva by měl směrovat na instanci služby. Povolit každého klienta pro data trasy pro konkrétní cílové služby bude implementaci dva koncové body služby, které se použijí pro příjem zpráv.  
  
> [!NOTE]
>  Tento příklad používá konkrétní koncové body k oddílu dat, to také je možné dosáhnout pomocí informací obsažených v rámci samotnou zprávu například dat Hlavička nebo text.  
  
### <a name="implement-service-data-partitioning"></a>Dělení na oddíly dat služby implementace  
  
1.  Vytvořte základní konfigurace směrování služby zadáním koncové body služby, který je zveřejněný prostřednictvím služby. V následujícím příkladu definuje dva koncové body, které se použije pro příjem zpráv. Definuje také koncové body klientů, které se používají k odesílání zpráv do instance služby regularCalc.  
  
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
  
2.  Zadejte filtry slouží ke směrování zpráv do cílového koncových bodů.  V tomto příkladu filtru EndpointName slouží k určení, které koncový bod služby zobrazila zpráva. V následujícím příkladu definuje nezbytné směrování části a filtry.  
  
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
  
3.  Definujte tabulku filtru, který přidruží každý filtr koncový bod klienta. V tomto příkladu budou směrovány zprávy založené na konkrétní koncový bod, který byl přijat přes. Vzhledem k tomu, že zpráva odpovídá pouze jeden dva možné filtry, není nutné pro použití s prioritou filtru k řízení pořadí, ve které filtry jsou vyhodnocena.  
  
     Následující tabulku filtru definuje a přidá filtry definované dříve.  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4.  Pokud chcete vyhodnotit příchozí zprávy před filtry, které jsou obsaženy v tabulce, je třeba přidružit tabulku filtru koncové body služby pomocí směrování chování. Následující příklad ukazuje přiřadit "filterTable1" s koncovými body služby:  
  
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
  
## <a name="example"></a>Příklad  
 Níže je úplný seznam všech konfiguračního souboru.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Směrovací služby](../../../../docs/framework/wcf/samples/routing-services.md)
