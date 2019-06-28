---
title: 'Postupy: Zpracování chyb'
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 4958e7914d9feb32dc00d11a215cf8247e9baffc
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424607"
---
# <a name="how-to-error-handling"></a>Postupy: Zpracování chyb

Toto téma popisuje základní kroky potřebné pro vytvoření konfigurace směrování, která používá zpracování chyb. V tomto příkladu zprávy jsou směrovány do cílového koncového bodu. Pokud zprávu nelze doručit z důvodu sítě nebo selhání týkajícího se komunikace (<xref:System.ServiceModel.CommunicationException>), zpráva se znovu odeslat do alternativní koncový bod.

> [!NOTE]
> K simulaci selhání sítě, cílový koncový bod použitý v tomto příkladu obsahuje nesprávnou adresu. Zprávy směruje do tohoto koncového bodu selže, protože žádná služba naslouchá na zadané adrese.

> [!NOTE]
> Zatímco například obsažené v tomto tématu se nezabývá explicitně nastavení časového limitu, je nutné provést tyto v úvahu při používání zpracování chyb. Pokud k chybám, bude dalšímu zpoždění došlo k předtím, než klient obdrží odpověď. Je to proto, že je chybě u služby směrování, která se pak pokusí odeslat zprávu do záložního koncového bodu. Pokud přidružené hodnoty časového limitu primárního a záložního cílové koncové body jsou velké, klient se může setkat dlouhé zpoždění jako zprávy převezme služby při selhání více koncových bodů v seznamu zálohování před odesláním úspěšně.
>
> Protože směrovací služba setkat se shoduje se součtem hodnotu časového limitu pro všechny koncové body přidružené k filtru Maximální zpoždění, doporučujeme zvýšit očekávané časový limit na straně klienta odpovídajícím způsobem.

### <a name="implement-error-handling"></a>Implementace zpracování chyb

1. Vytvořte základní konfiguraci směrovací služby tak, že zadáte koncový bod služby, vystavený službou. Následující příklad definuje jedinou službou koncový bod, který se používá pro příjem zpráv. Také definuje koncové body klienta, které se používají k odesílání zprávy. deadDestination a realDestination. Koncový bod deadDestination obsahuje adresu, která neodkazuje na spuštěnou službu a slouží k simulaci selhání sítě, při odesílání zpráv do tohoto koncového bodu.

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

2. Určit filtry, které slouží ke směrování zpráv do cílové koncové body.  V tomto příkladu je použit filtr MatchAll tak, aby odpovídaly všechny zprávy přijaté službou směrování.

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. Definování seznamu záložního koncového bodu, který obsahuje koncové body, které je odeslána zpráva v případě selhání sítě nebo komunikace při odesílání na cílové primární koncový bod. Následující příklad definuje záložní seznam, který obsahuje jeden koncový bod; však lze zadat více koncových bodů v zálohování seznamu.

     Pokud záložní seznam obsahuje několik koncových bodů, když síť nebo dojde k chybě komunikace, směrovací služba se pokusí odeslat zprávu na první koncový bod v seznamu. Pokud dojde k chybě sítě nebo komunikace při odesílání na tento koncový bod, směrovací služba se pokusí odeslat zprávu do další koncový bod obsažených v seznamu. Služba pokračuje v odesílání zprávy každý koncový bod v seznamu záložního koncového bodu, dokud je zpráva odeslána úspěšně, všechny koncové body zálohy vrátit sítě nebo chyba týkající se komunikace nebo je zpráva odeslána a koncový bod vrátí síti, Chyba nesouvisející se komunikace.

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. Definujte tabulku filtru, která filtr přidruží koncový bod deadDestination a seznamu zálohy koncových bodů.  Směrovací služba se nejprve pokusí odeslat zprávu do koncového bodu cílové přidružené k filtru. Vzhledem k tomu, deadDestination obsahuje adresu, která neodkazuje na spuštěnou službu, výsledkem je chyba sítě. Směrovací služba se pak pokusí odeslat zprávu do koncového bodu určeného v backupEndpointList.

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

5. Vyhodnocování příchozích zpráv s použitím filtru obsažené v tabulce filtrů, je třeba přidružit tabulky filtru koncových bodů služby pomocí směrování chování.  Následující příklad ukazuje přiřazování "filterTable1" pomocí koncových bodů služby.

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

Tady je úplný seznam všech konfiguračního souboru.

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
            <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->
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
