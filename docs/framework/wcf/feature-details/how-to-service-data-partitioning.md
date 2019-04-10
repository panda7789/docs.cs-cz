---
title: 'Postupy: Vytvoření oddílů dat služby'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 17cb80bf253491eb563d6fd45b5997e452f542e1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300382"
---
# <a name="how-to-service-data-partitioning"></a>Postupy: Vytvoření oddílů dat služby
Toto téma popisuje základní kroky potřebné k oddílu zprávy do několika instancí stejné cílové služby. Dělení dat služby se obvykle používá, když budete chtít škálování služby, aby bylo možné poskytovat lepší kvalitu služby, nebo pokud potřebujete zpracovávat požadavky různých zákazníků určitým způsobem. Zprávy z vysoké hodnoty nebo zákazníky za "Zlatá" může například potřeba zpracovat s vyšší prioritou než zpráv od standardní zákazníka.  
  
 V tomto příkladu zprávy jsou směrovány na jednu ze dvou instancí služby regularCalc. Obě instance služby jsou identické; ale reprezentované zprávami procesy calculator1 koncový bod služby obdrželi od zákazníků vysoké hodnoty, koncový bod Kalkulačka 2 procesy zpráv od ostatních zákazníků  
  
 Z klienta byla odeslána zpráva nemá jedinečných dat, který můžete použít k identifikaci které se mají směrovat zprávy k instanci služby. Povolit každá klient data trasy pro konkrétní cílové služby Implementujeme dva koncové body služby, které se použijí pro příjem zpráv.  
  
> [!NOTE]
>  Přestože tento příklad používá konkrétní koncové body k dělení dat, to může také provést pomocí informací obsažených v rámci vlastní zprávě například Hlavička nebo text data.  
  
### <a name="implement-service-data-partitioning"></a>Dělení dat implementace služby  
  
1. Vytvoření základní konfigurace služby směrování zadat koncové body služby určeného službou. Následující příklad definuje dva koncové body, které se budou používat pro příjem zpráv. Také definuje koncové body klienta, které se používají k odesílání zpráv do instance služby regularCalc.  
  
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
  
2. Určit filtry, které slouží ke směrování zpráv do cílové koncové body.  V tomto příkladu Název_koncového_bodu filtr slouží k určení, které koncový bod služby zobrazila zpráva. Následující příklad definuje oddíl nezbytné směrování a filtry.  
  
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
  
3. Definujte filtr tabulky, který každý filtr přidruží koncový bod klienta. V tomto příkladu budou směrovat zprávy na základě konkrétní koncového bodu, který byl přijat přes. Vzhledem k tomu, že zpráva odpovídá pouze jeden z filtrů dva možné, není nutné pro řídit pořadí, ve které filtry jsou vyhodnocovány pomocí Priorita filtru.  
  
     Následující definuje filtr tabulky a přidá filtry definovali dříve.  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. Vyhodnocování příchozích zpráv proti filtry, které jsou obsaženy v tabulce, musíte přidružit tabulky filtru koncových bodů služby pomocí směrování chování. Následující příklad ukazuje přiřazování "filterTable1" s koncovými body služby:  
  
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
 Tady je úplný seznam všech konfiguračního souboru.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Směrovací služby](../../../../docs/framework/wcf/samples/routing-services.md)
