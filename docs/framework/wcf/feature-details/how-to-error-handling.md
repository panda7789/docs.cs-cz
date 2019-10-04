---
title: 'Postupy: zpracování chyb'
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 3b8e48a74ff7671b942b5499fb3a0b5d0f389d61
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834704"
---
# <a name="how-to-error-handling"></a>Postupy: zpracování chyb

Toto téma popisuje základní kroky potřebné k vytvoření konfigurace směrování, která využívá zpracování chyb. V tomto příkladu jsou zprávy směrovány do cílového koncového bodu. Pokud zprávu nelze doručit kvůli chybě související se sítí nebo komunikací (<xref:System.ServiceModel.CommunicationException>), zpráva se znovu vymění do alternativního koncového bodu.

> [!NOTE]
> Aby bylo možné simulovat selhání sítě, cílový koncový bod použitý v tomto příkladu obsahuje nesprávnou adresu. Zprávy směrované do tohoto koncového bodu selžou, protože na zadané adrese nenaslouchá žádná služba.

> [!NOTE]
> Přestože příklad obsažený v tomto tématu výslovně nezabývá nastavení časového limitu, musíte při použití zpracování chyb vzít v úvahu tyto skutečnosti. Pokud dojde k chybám, dojde k další prodlevě, než klient obdrží odpověď. Důvodem je to, že chyba je přijata ve směrovací službě, která se pak pokusí odeslat zprávu do koncového bodu zálohy. Pokud jsou hodnoty časového limitu přidružené k primárnímu a cílovému koncovému bodu zálohy velké, může klient při převzetí služeb při selhání na více koncových bodů v seznamu zálohování vyskytnout dlouhou prodlevu, než se úspěšně pošle.
>
> Vzhledem k tomu, že služba Směrování by mohla narazit na maximální zpoždění rovnající se součtu hodnoty časového limitu všech koncových bodů přidružených k filtru, doporučujeme, abyste v klientovi odpovídajícím způsobem zvýšili očekávaný časový limit.

### <a name="implement-error-handling"></a>Implementace zpracování chyb

1. Vytvořte základní konfiguraci směrovací služby zadáním koncového bodu služby vystaveného službou. Následující příklad definuje jeden koncový bod služby, který slouží k přijímání zpráv. Také definuje koncové body klienta, které se používají k posílání zpráv. deadDestination a realDestination. Koncový bod deadDestination obsahuje adresu, která neodkazuje na běžící službu a slouží k simulaci selhání sítě při odesílání zpráv do tohoto koncového bodu.

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

2. Definujte filtry používané ke směrování zpráv do cílových koncových bodů.  V tomto příkladu se používá filtr MatchAll ke spárování všech zpráv přijatých směrovací službou.

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. Definujte seznam koncových bodů zálohování, který obsahuje koncové body, na které se zpráva pošle v případě, že dojde k selhání sítě nebo komunikace při posílání do primárního cílového koncového bodu. Následující příklad definuje seznam zálohování, který obsahuje jeden koncový bod. v seznamu zálohování je však možné zadat více koncových bodů.

     Pokud seznam zálohování obsahuje několik koncových bodů, když dojde k selhání sítě nebo komunikace, pokusí se služba Směrování odeslat zprávu do prvního koncového bodu v seznamu. Pokud dojde k chybě sítě nebo komunikace při posílání do tohoto koncového bodu, služba Směrování se pokusí odeslat zprávu na další koncový bod obsažený v seznamu. Služba pokračuje v posílání zpráv do každého koncového bodu v seznamu záložních bodů zálohování, dokud se zpráva úspěšně neodešle, všechny koncové body zálohování vrátí síť nebo chybu související s komunikací nebo zpráva se odešle a koncový bod vrátí nepřipojenou síť. Chyba související se službou bez komunikace.

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. Definujte tabulku filtru, která přidruží filtr k deadDestination koncovému bodu a seznamu koncových bodů zálohování.  Směrovací služba se nejdříve pokusí odeslat zprávu do cílového koncového bodu přidruženého k filtru. Vzhledem k tomu, že deadDestination obsahuje adresu, která neodkazuje na běžící službu, dojde k chybě sítě. Směrovací služba se pak pokusí odeslat zprávu na koncový bod zadaný v backupEndpointList.

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

5. Chcete-li vyhodnotit příchozí zprávy proti filtru obsaženému v tabulce filtru, je nutné přidružit tabulku filtru k koncovým bodům služby pomocí chování směrování.  Následující příklad ukazuje přidružení "filterTable1" k koncovým bodům služby.

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

Následuje úplný seznam konfiguračního souboru:

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
