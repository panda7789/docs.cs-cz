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
# <a name="how-to-error-handling"></a><span data-ttu-id="2a382-102">Postupy: zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="2a382-102">How To: Error Handling</span></span>

<span data-ttu-id="2a382-103">Toto téma popisuje základní kroky potřebné k vytvoření konfigurace směrování, která využívá zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="2a382-103">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="2a382-104">V tomto příkladu jsou zprávy směrovány do cílového koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2a382-104">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="2a382-105">Pokud zprávu nelze doručit kvůli chybě související se sítí nebo komunikací (<xref:System.ServiceModel.CommunicationException>), zpráva se znovu vymění do alternativního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2a382-105">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="2a382-106">Aby bylo možné simulovat selhání sítě, cílový koncový bod použitý v tomto příkladu obsahuje nesprávnou adresu.</span><span class="sxs-lookup"><span data-stu-id="2a382-106">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="2a382-107">Zprávy směrované do tohoto koncového bodu selžou, protože na zadané adrese nenaslouchá žádná služba.</span><span class="sxs-lookup"><span data-stu-id="2a382-107">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>

> [!NOTE]
> <span data-ttu-id="2a382-108">Přestože příklad obsažený v tomto tématu výslovně nezabývá nastavení časového limitu, musíte při použití zpracování chyb vzít v úvahu tyto skutečnosti.</span><span class="sxs-lookup"><span data-stu-id="2a382-108">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="2a382-109">Pokud dojde k chybám, dojde k další prodlevě, než klient obdrží odpověď.</span><span class="sxs-lookup"><span data-stu-id="2a382-109">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="2a382-110">Důvodem je to, že chyba je přijata ve směrovací službě, která se pak pokusí odeslat zprávu do koncového bodu zálohy.</span><span class="sxs-lookup"><span data-stu-id="2a382-110">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="2a382-111">Pokud jsou hodnoty časového limitu přidružené k primárnímu a cílovému koncovému bodu zálohy velké, může klient při převzetí služeb při selhání na více koncových bodů v seznamu zálohování vyskytnout dlouhou prodlevu, než se úspěšně pošle.</span><span class="sxs-lookup"><span data-stu-id="2a382-111">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>
>
> <span data-ttu-id="2a382-112">Vzhledem k tomu, že služba Směrování by mohla narazit na maximální zpoždění rovnající se součtu hodnoty časového limitu všech koncových bodů přidružených k filtru, doporučujeme, abyste v klientovi odpovídajícím způsobem zvýšili očekávaný časový limit.</span><span class="sxs-lookup"><span data-stu-id="2a382-112">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>

### <a name="implement-error-handling"></a><span data-ttu-id="2a382-113">Implementace zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="2a382-113">Implement Error Handling</span></span>

1. <span data-ttu-id="2a382-114">Vytvořte základní konfiguraci směrovací služby zadáním koncového bodu služby vystaveného službou.</span><span class="sxs-lookup"><span data-stu-id="2a382-114">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="2a382-115">Následující příklad definuje jeden koncový bod služby, který slouží k přijímání zpráv.</span><span class="sxs-lookup"><span data-stu-id="2a382-115">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="2a382-116">Také definuje koncové body klienta, které se používají k posílání zpráv. deadDestination a realDestination.</span><span class="sxs-lookup"><span data-stu-id="2a382-116">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="2a382-117">Koncový bod deadDestination obsahuje adresu, která neodkazuje na běžící službu a slouží k simulaci selhání sítě při odesílání zpráv do tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2a382-117">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>

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

2. <span data-ttu-id="2a382-118">Definujte filtry používané ke směrování zpráv do cílových koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="2a382-118">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="2a382-119">V tomto příkladu se používá filtr MatchAll ke spárování všech zpráv přijatých směrovací službou.</span><span class="sxs-lookup"><span data-stu-id="2a382-119">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. <span data-ttu-id="2a382-120">Definujte seznam koncových bodů zálohování, který obsahuje koncové body, na které se zpráva pošle v případě, že dojde k selhání sítě nebo komunikace při posílání do primárního cílového koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2a382-120">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="2a382-121">Následující příklad definuje seznam zálohování, který obsahuje jeden koncový bod. v seznamu zálohování je však možné zadat více koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="2a382-121">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>

     <span data-ttu-id="2a382-122">Pokud seznam zálohování obsahuje několik koncových bodů, když dojde k selhání sítě nebo komunikace, pokusí se služba Směrování odeslat zprávu do prvního koncového bodu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="2a382-122">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="2a382-123">Pokud dojde k chybě sítě nebo komunikace při posílání do tohoto koncového bodu, služba Směrování se pokusí odeslat zprávu na další koncový bod obsažený v seznamu.</span><span class="sxs-lookup"><span data-stu-id="2a382-123">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="2a382-124">Služba pokračuje v posílání zpráv do každého koncového bodu v seznamu záložních bodů zálohování, dokud se zpráva úspěšně neodešle, všechny koncové body zálohování vrátí síť nebo chybu související s komunikací nebo zpráva se odešle a koncový bod vrátí nepřipojenou síť. Chyba související se službou bez komunikace.</span><span class="sxs-lookup"><span data-stu-id="2a382-124">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. <span data-ttu-id="2a382-125">Definujte tabulku filtru, která přidruží filtr k deadDestination koncovému bodu a seznamu koncových bodů zálohování.</span><span class="sxs-lookup"><span data-stu-id="2a382-125">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="2a382-126">Směrovací služba se nejdříve pokusí odeslat zprávu do cílového koncového bodu přidruženého k filtru.</span><span class="sxs-lookup"><span data-stu-id="2a382-126">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="2a382-127">Vzhledem k tomu, že deadDestination obsahuje adresu, která neodkazuje na běžící službu, dojde k chybě sítě.</span><span class="sxs-lookup"><span data-stu-id="2a382-127">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="2a382-128">Směrovací služba se pak pokusí odeslat zprávu na koncový bod zadaný v backupEndpointList.</span><span class="sxs-lookup"><span data-stu-id="2a382-128">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointList.</span></span>

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

5. <span data-ttu-id="2a382-129">Chcete-li vyhodnotit příchozí zprávy proti filtru obsaženému v tabulce filtru, je nutné přidružit tabulku filtru k koncovým bodům služby pomocí chování směrování.</span><span class="sxs-lookup"><span data-stu-id="2a382-129">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="2a382-130">Následující příklad ukazuje přidružení "filterTable1" k koncovým bodům služby.</span><span class="sxs-lookup"><span data-stu-id="2a382-130">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>

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

## <a name="example"></a><span data-ttu-id="2a382-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a382-131">Example</span></span>

<span data-ttu-id="2a382-132">Následuje úplný seznam konfiguračního souboru:</span><span class="sxs-lookup"><span data-stu-id="2a382-132">The following is a complete listing of the configuration file:</span></span>

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
