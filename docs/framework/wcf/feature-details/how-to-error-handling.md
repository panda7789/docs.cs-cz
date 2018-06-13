---
title: 'Postupy: Zpracování chyb'
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 7b173997eb53f8cf156ccb14083885a199dc8921
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493595"
---
# <a name="how-to-error-handling"></a>Postupy: Zpracování chyb
Toto téma popisuje základní kroky potřebné pro vytvoření konfigurace směrování, která používá zpracování chyb. V tomto příkladu zprávy jsou směrovány do cílového koncového bodu. Pokud zprávu nelze doručit z důvodu v síti nebo na chybu týkající se komunikace (<xref:System.ServiceModel.CommunicationException>), je nutno zprávu na alternativní koncový bod.  
  
> [!NOTE]
>  Simulace selhání sítě, do cílového koncového bodu použité v tomto příkladu obsahuje nesprávnou adresu. Zprávy směrované na tento koncový bod selhání jako žádná služba naslouchá na zadanou adresu.  
  
> [!NOTE]
>  Při příklad obsažené v tomto tématu se nezabývá explicitně nastavení časového limitu, je nutné provést tyto v úvahu při použití zpracování chyb. Když dojde k chybám, budou existovat další prodlevu došlo předtím, než klient obdrží odpověď. Důvodem je chyba přijme služby směrování, která se pokusí k odeslání zprávy do koncového bodu zálohy. Pokud přidružené hodnoty časového limitu primární a záložní cílové koncové body jsou velké, klient může mít dlouhém zpoždění, protože zpráva převezme několik koncových bodů v záložním seznamu před se úspěšně odeslal.  
>   
>  Vzhledem k tomu, že směrovací služby může dojít k maximální zpoždění, která je určena součtem časový limit pro všechny koncové body přidružené k filtru, doporučujeme zvýšit očekávaný časový limit na straně klienta odpovídajícím způsobem.  
  
### <a name="implement-error-handling"></a>Implementace zpracování chyb  
  
1.  Vytvořte základní konfigurace směrování služby zadáním koncový bod služby, který je zveřejněný prostřednictvím služby. V následujícím příkladu definuje koncového bodu jedné služby, který se používá pro příjem zpráv. Definuje také koncové body klientů, které se používají k odesílání zpráv; deadDestination a realDestination. Koncový bod deadDestination obsahuje adresu, která neodkazuje na spuštěnou službu a slouží k simulaci selhání sítě při odesílání zpráv k tomuto koncovému bodu.  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/" />  
          </baseAddresses>  
        </host>  
        <!-- Create the Routing Service endpoint -->  
        <endpoint address="router"  
                  binding="basicHttpBinding"  
                  name="RoutingServiceEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
  
    <!-- Create the destination endpoints that we want to send to -->  
    <client>  
      <!-- Create a dummy endpoint that we know will be down -->  
      <endpoint name="deadDestination"   
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <!-- Now create the real service endpoint -->  
      <endpoint name="realDestination"   
                address="net.tcp://localhost:8080/servicemodelsamples/service"  
                binding="netTcpBinding"   
                contract="*" />  
    </client>  
    ```  
  
2.  Zadejte filtry slouží ke směrování zpráv do cílového koncových bodů.  V tomto příkladu se používá MatchAll filtru tak, aby odpovídaly všechny zprávy přijaté službou směrování.  
  
    ```xml  
    <filters>  
      <!-- Create a MatchAll filter which will catch all messages -->  
      <filter name="MatchAllFilter1" filterType="MatchAll" />  
    </filters>  
    ```  
  
3.  Definujte seznam zálohování koncový bod, který obsahuje koncové body, které je odeslána zpráva v případě selhání sítě nebo komunikace při odesílání na cílové primární koncový bod. V následujícím příkladu definuje seznam zálohování, která obsahuje jeden koncový bod; víc koncových bodů však lze zadat v záložním seznamu.  
  
     Pokud zálohování seznam obsahuje několik koncových bodů, když síť nebo službu Směrování dojde k chybě komunikace se pokouší odeslat zprávu na první koncový bod v seznamu. Pokud dojde k chybě sítě nebo komunikace při odesílání na tento koncový bod, směrovací služby se pokouší odeslat zprávu na další koncový bod obsažené v seznamu. Služba bude stále poslal do každého koncového bodu v seznamu zálohování koncový bod, dokud se úspěšně odeslal zprávu, vrátí všechny koncové body zálohy v síti nebo chyba týkající se komunikace, nebo je zpráva odeslána a koncový bod vrátí jiný síť, Chyba nesouvisející komunikace.  
  
    ```xml  
    <backupLists>          
      <backupList name="backupEndpointList">  
          <add endpointName="realDestination" />  
      </backupList>  
    </backupLists>  
    ```  
  
4.  Definujte filtr tabulky a který přidruží filtr deadDestination koncový bod a seznamu zálohování koncový bod.  Směrovací služby se nejprve pokusí odeslat zprávu do cílového koncového bodu, přidružené k filtru. Vzhledem k tomu, že deadDestination obsahuje adresu, která neodkazuje na spuštěnou službu, výsledkem je chyba sítě. Směrovací služby pokusí odeslat zprávu do zadaného v backupEndpointlist koncového bodu.  
  
    ```xml  
    <filterTables>  
            <!-- Set up the Routing Service's Message Filter Table -->  
            <filterTable name="filterTable1">  
                <!-- Add an entity that maps the MatchAllMessageFilter to the dead destination -->  
                <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->  
                <!-- Listed in the backupEndpointList -->  
                <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>  
            </filterTable>  
          </filterTables>  
    ```  
  
5.  Pokud chcete vyhodnotit příchozí zprávy s použitím filtru obsažené v tabulce filtru, musíte přidružit tabulku filtru koncové body služby pomocí směrování chování.  Následující příklad ukazuje přiřadit "filterTable1" s koncovými body služby.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <!-- Set up the Routing Behavior -->  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a>Příklad  
 Toto je úplný seznam všech konfiguračního souboru.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/" />  
          </baseAddresses>  
        </host>  
        <!-- Create the Routing Service endpoint -->  
        <endpoint address="router"  
                  binding="basicHttpBinding"  
                  name="RoutingServiceEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <!-- Set up the Routing Behavior -->  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <!-- Create the destination endpoints that we want to send to -->  
    <client>  
      <!-- Create a dummy endpoint that we know will be down -->  
      <endpoint name="deadDestination"   
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <!-- Now create the real service endpoint -->  
      <endpoint name="realDestination"   
                address="net.tcp://localhost:8080/servicemodelsamples/service"  
                binding="netTcpBinding"   
                contract="*" />  
    </client>  
    <routing>  
      <filters>  
        <!-- Create a MatchAll filter which will catch all messages -->  
        <filter name="MatchAllFilter1" filterType="MatchAll" />  
      </filters>  
      <filterTables>  
        <!-- Set up the Routing Service's Message Filter Table -->  
        <filterTable name="filterTable1">  
            <!-- Add an entrty that maps the MatchAllMessageFilter to the dead destination -->  
            <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->  
            <!-- Listed in the backupEndpointList -->  
            <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>  
        </filterTable>  
      </filterTables>  
      <!-- Create the backup endpoint list -->  
      <backupLists>          
        <backupList name="backupEndpointList">  
            <add endpointName="realDestination" />  
        </backupList>  
      </backupLists>  
      </routing>  
  </system.serviceModel>  
</configuration>  
```
