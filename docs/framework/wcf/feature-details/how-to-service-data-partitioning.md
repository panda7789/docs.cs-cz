---
title: 'Postupy: Vytvoření oddílů dat služby'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 49aefd88d73732a139a79f8c53d5beca44d4d4ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947876"
---
# <a name="how-to-service-data-partitioning"></a>Postupy: Vytvoření oddílů dat služby
Toto téma popisuje základní kroky potřebné k rozdělení zpráv mezi více instancí stejné cílové služby. Vytváření oddílů dat služby se obvykle používá v případě, že potřebujete škálovat službu tak, aby poskytovala lepší kvalitu služeb, nebo když potřebujete konkrétní způsob zpracovávat žádosti od různých zákazníků. Například zprávy od vysoké hodnoty nebo "Gold" můžou být potřeba zpracovat s vyšší prioritou než zprávy ze standardního zákazníka.  
  
 V tomto příkladu jsou zprávy směrovány do jedné ze dvou instancí služby regularCalc. Obě instance služby jsou identické. Nicméně služba reprezentovaná koncovým bodem calculator1 zpracovává zprávy obdržené od zákazníků s vysokou hodnotou a koncovým bodem kalkulačky zpracovává zprávy od jiných zákazníků.  
  
 Zpráva odeslaná z klienta neobsahuje žádná jedinečná data, která by bylo možné použít k identifikaci instance služby, na kterou se má zpráva směrovat. Aby každý klient mohl směrovat data do konkrétní cílové služby, implementujeme dva koncové body služby, které budou použity pro příjem zpráv.  
  
> [!NOTE]
> I když tento příklad používá ke dělení dat konkrétní koncové body, může to být také provedeno pomocí informací obsažených v samotné zprávě, jako jsou například záhlaví nebo textová data.  
  
### <a name="implement-service-data-partitioning"></a>Implementace dělení dat služby  
  
1. Vytvořte základní konfiguraci směrovací služby zadáním koncových bodů služby vystavených službou. Následující příklad definuje dva koncové body, které budou použity pro příjem zpráv. Také definuje koncové body klienta, které slouží k posílání zpráv do instancí služby regularCalc.  
  
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
  
2. Definujte filtry používané ke směrování zpráv do cílových koncových bodů.  V tomto příkladu se používá filtr koncového bodu k určení, který koncový bod služby obdržel zprávu. Následující příklad definuje nezbytný oddíl směrování a filtry.  
  
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
  
3. Definujte tabulku filtru, která přidruží jednotlivé filtry ke koncovému bodu klienta. V tomto příkladu bude zpráva směrována podle konkrétního koncového bodu, ve kterém byla přijata. Vzhledem k tomu, že zpráva může odpovídat pouze jednomu ze dvou možných filtrů, není nutné používat prioritu filtru k řízení pořadí, ve kterém jsou filtry vyhodnocovány.  
  
     Následující definice tabulky filtru a přidává filtry definované dříve.  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. Chcete-li vyhodnotit příchozí zprávy proti filtrům obsaženým v tabulce, je nutné přidružit tabulku filtru k koncovým bodům služby pomocí chování směrování. Následující příklad ukazuje přidružení "filterTable1" k koncovým bodům služby:  
  
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
 Následuje úplný seznam konfiguračního souboru.  
  
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
