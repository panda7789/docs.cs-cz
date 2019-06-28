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
# <a name="how-to-error-handling"></a><span data-ttu-id="36c05-102">Postupy: Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="36c05-102">How To: Error Handling</span></span>

<span data-ttu-id="36c05-103">Toto téma popisuje základní kroky potřebné pro vytvoření konfigurace směrování, která používá zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="36c05-103">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="36c05-104">V tomto příkladu zprávy jsou směrovány do cílového koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="36c05-104">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="36c05-105">Pokud zprávu nelze doručit z důvodu sítě nebo selhání týkajícího se komunikace (<xref:System.ServiceModel.CommunicationException>), zpráva se znovu odeslat do alternativní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="36c05-105">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="36c05-106">K simulaci selhání sítě, cílový koncový bod použitý v tomto příkladu obsahuje nesprávnou adresu.</span><span class="sxs-lookup"><span data-stu-id="36c05-106">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="36c05-107">Zprávy směruje do tohoto koncového bodu selže, protože žádná služba naslouchá na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="36c05-107">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>

> [!NOTE]
> <span data-ttu-id="36c05-108">Zatímco například obsažené v tomto tématu se nezabývá explicitně nastavení časového limitu, je nutné provést tyto v úvahu při používání zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="36c05-108">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="36c05-109">Pokud k chybám, bude dalšímu zpoždění došlo k předtím, než klient obdrží odpověď.</span><span class="sxs-lookup"><span data-stu-id="36c05-109">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="36c05-110">Je to proto, že je chybě u služby směrování, která se pak pokusí odeslat zprávu do záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="36c05-110">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="36c05-111">Pokud přidružené hodnoty časového limitu primárního a záložního cílové koncové body jsou velké, klient se může setkat dlouhé zpoždění jako zprávy převezme služby při selhání více koncových bodů v seznamu zálohování před odesláním úspěšně.</span><span class="sxs-lookup"><span data-stu-id="36c05-111">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>
>
> <span data-ttu-id="36c05-112">Protože směrovací služba setkat se shoduje se součtem hodnotu časového limitu pro všechny koncové body přidružené k filtru Maximální zpoždění, doporučujeme zvýšit očekávané časový limit na straně klienta odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="36c05-112">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>

### <a name="implement-error-handling"></a><span data-ttu-id="36c05-113">Implementace zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="36c05-113">Implement Error Handling</span></span>

1. <span data-ttu-id="36c05-114">Vytvořte základní konfiguraci směrovací služby tak, že zadáte koncový bod služby, vystavený službou.</span><span class="sxs-lookup"><span data-stu-id="36c05-114">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="36c05-115">Následující příklad definuje jedinou službou koncový bod, který se používá pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="36c05-115">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="36c05-116">Také definuje koncové body klienta, které se používají k odesílání zprávy. deadDestination a realDestination.</span><span class="sxs-lookup"><span data-stu-id="36c05-116">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="36c05-117">Koncový bod deadDestination obsahuje adresu, která neodkazuje na spuštěnou službu a slouží k simulaci selhání sítě, při odesílání zpráv do tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="36c05-117">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>

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

2. <span data-ttu-id="36c05-118">Určit filtry, které slouží ke směrování zpráv do cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="36c05-118">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="36c05-119">V tomto příkladu je použit filtr MatchAll tak, aby odpovídaly všechny zprávy přijaté službou směrování.</span><span class="sxs-lookup"><span data-stu-id="36c05-119">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. <span data-ttu-id="36c05-120">Definování seznamu záložního koncového bodu, který obsahuje koncové body, které je odeslána zpráva v případě selhání sítě nebo komunikace při odesílání na cílové primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="36c05-120">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="36c05-121">Následující příklad definuje záložní seznam, který obsahuje jeden koncový bod; však lze zadat více koncových bodů v zálohování seznamu.</span><span class="sxs-lookup"><span data-stu-id="36c05-121">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>

     <span data-ttu-id="36c05-122">Pokud záložní seznam obsahuje několik koncových bodů, když síť nebo dojde k chybě komunikace, směrovací služba se pokusí odeslat zprávu na první koncový bod v seznamu.</span><span class="sxs-lookup"><span data-stu-id="36c05-122">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="36c05-123">Pokud dojde k chybě sítě nebo komunikace při odesílání na tento koncový bod, směrovací služba se pokusí odeslat zprávu do další koncový bod obsažených v seznamu.</span><span class="sxs-lookup"><span data-stu-id="36c05-123">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="36c05-124">Služba pokračuje v odesílání zprávy každý koncový bod v seznamu záložního koncového bodu, dokud je zpráva odeslána úspěšně, všechny koncové body zálohy vrátit sítě nebo chyba týkající se komunikace nebo je zpráva odeslána a koncový bod vrátí síti, Chyba nesouvisející se komunikace.</span><span class="sxs-lookup"><span data-stu-id="36c05-124">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. <span data-ttu-id="36c05-125">Definujte tabulku filtru, která filtr přidruží koncový bod deadDestination a seznamu zálohy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="36c05-125">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="36c05-126">Směrovací služba se nejprve pokusí odeslat zprávu do koncového bodu cílové přidružené k filtru.</span><span class="sxs-lookup"><span data-stu-id="36c05-126">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="36c05-127">Vzhledem k tomu, deadDestination obsahuje adresu, která neodkazuje na spuštěnou službu, výsledkem je chyba sítě.</span><span class="sxs-lookup"><span data-stu-id="36c05-127">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="36c05-128">Směrovací služba se pak pokusí odeslat zprávu do koncového bodu určeného v backupEndpointList.</span><span class="sxs-lookup"><span data-stu-id="36c05-128">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointList.</span></span>

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

5. <span data-ttu-id="36c05-129">Vyhodnocování příchozích zpráv s použitím filtru obsažené v tabulce filtrů, je třeba přidružit tabulky filtru koncových bodů služby pomocí směrování chování.</span><span class="sxs-lookup"><span data-stu-id="36c05-129">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="36c05-130">Následující příklad ukazuje přiřazování "filterTable1" pomocí koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="36c05-130">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>

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

## <a name="example"></a><span data-ttu-id="36c05-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="36c05-131">Example</span></span>

<span data-ttu-id="36c05-132">Tady je úplný seznam všech konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="36c05-132">Following is a complete listing of the configuration file.</span></span>

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
