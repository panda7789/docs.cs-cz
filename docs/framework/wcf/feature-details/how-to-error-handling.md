---
title: "Postupy: Zpracování chyb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5b0fe57bb6a4604c86e63a154e3af5542672912
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-error-handling"></a><span data-ttu-id="cca3f-102">Postupy: Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="cca3f-102">How To: Error Handling</span></span>
<span data-ttu-id="cca3f-103">Toto téma popisuje základní kroky potřebné pro vytvoření konfigurace směrování, která používá zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="cca3f-103">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="cca3f-104">V tomto příkladu zprávy jsou směrovány do cílového koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="cca3f-104">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="cca3f-105">Pokud zprávu nelze doručit z důvodu v síti nebo na chybu týkající se komunikace (<xref:System.ServiceModel.CommunicationException>), je nutno zprávu na alternativní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="cca3f-105">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cca3f-106">Simulace selhání sítě, do cílového koncového bodu použité v tomto příkladu obsahuje nesprávnou adresu.</span><span class="sxs-lookup"><span data-stu-id="cca3f-106">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="cca3f-107">Zprávy směrované na tento koncový bod selhání jako žádná služba naslouchá na zadanou adresu.</span><span class="sxs-lookup"><span data-stu-id="cca3f-107">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cca3f-108">Při příklad obsažené v tomto tématu se nezabývá explicitně nastavení časového limitu, je nutné provést tyto v úvahu při použití zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="cca3f-108">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="cca3f-109">Když dojde k chybám, budou existovat další prodlevu došlo předtím, než klient obdrží odpověď.</span><span class="sxs-lookup"><span data-stu-id="cca3f-109">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="cca3f-110">Důvodem je chyba přijme služby směrování, která se pokusí k odeslání zprávy do koncového bodu zálohy.</span><span class="sxs-lookup"><span data-stu-id="cca3f-110">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="cca3f-111">Pokud přidružené hodnoty časového limitu primární a záložní cílové koncové body jsou velké, klient může mít dlouhém zpoždění, protože zpráva převezme několik koncových bodů v záložním seznamu před se úspěšně odeslal.</span><span class="sxs-lookup"><span data-stu-id="cca3f-111">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>  
>   
>  <span data-ttu-id="cca3f-112">Vzhledem k tomu, že směrovací služby může dojít k maximální zpoždění, která je určena součtem časový limit pro všechny koncové body přidružené k filtru, doporučujeme zvýšit očekávaný časový limit na straně klienta odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="cca3f-112">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>  
  
### <a name="implement-error-handling"></a><span data-ttu-id="cca3f-113">Implementace zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="cca3f-113">Implement Error Handling</span></span>  
  
1.  <span data-ttu-id="cca3f-114">Vytvořte základní konfigurace směrování služby zadáním koncový bod služby, který je zveřejněný prostřednictvím služby.</span><span class="sxs-lookup"><span data-stu-id="cca3f-114">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="cca3f-115">V následujícím příkladu definuje koncového bodu jedné služby, který se používá pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="cca3f-115">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="cca3f-116">Definuje také koncové body klientů, které se používají k odesílání zpráv; deadDestination a realDestination.</span><span class="sxs-lookup"><span data-stu-id="cca3f-116">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="cca3f-117">Koncový bod deadDestination obsahuje adresu, která neodkazuje na spuštěnou službu a slouží k simulaci selhání sítě při odesílání zpráv k tomuto koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="cca3f-117">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>  
  
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
  
2.  <span data-ttu-id="cca3f-118">Zadejte filtry slouží ke směrování zpráv do cílového koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="cca3f-118">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="cca3f-119">V tomto příkladu se používá MatchAll filtru tak, aby odpovídaly všechny zprávy přijaté službou směrování.</span><span class="sxs-lookup"><span data-stu-id="cca3f-119">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>  
  
    ```xml  
    <filters>  
      <!-- Create a MatchAll filter which will catch all messages -->  
      <filter name="MatchAllFilter1" filterType="MatchAll" />  
    </filters>  
    ```  
  
3.  <span data-ttu-id="cca3f-120">Definujte seznam zálohování koncový bod, který obsahuje koncové body, které je odeslána zpráva v případě selhání sítě nebo komunikace při odesílání na cílové primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="cca3f-120">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="cca3f-121">V následujícím příkladu definuje seznam zálohování, která obsahuje jeden koncový bod; víc koncových bodů však lze zadat v záložním seznamu.</span><span class="sxs-lookup"><span data-stu-id="cca3f-121">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>  
  
     <span data-ttu-id="cca3f-122">Pokud zálohování seznam obsahuje několik koncových bodů, když síť nebo službu Směrování dojde k chybě komunikace se pokouší odeslat zprávu na první koncový bod v seznamu.</span><span class="sxs-lookup"><span data-stu-id="cca3f-122">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="cca3f-123">Pokud dojde k chybě sítě nebo komunikace při odesílání na tento koncový bod, směrovací služby se pokouší odeslat zprávu na další koncový bod obsažené v seznamu.</span><span class="sxs-lookup"><span data-stu-id="cca3f-123">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="cca3f-124">Služba bude stále poslal do každého koncového bodu v seznamu zálohování koncový bod, dokud se úspěšně odeslal zprávu, vrátí všechny koncové body zálohy v síti nebo chyba týkající se komunikace, nebo je zpráva odeslána a koncový bod vrátí jiný síť, Chyba nesouvisející komunikace.</span><span class="sxs-lookup"><span data-stu-id="cca3f-124">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>  
  
    ```xml  
    <backupLists>          
      <backupList name="backupEndpointList">  
          <add endpointName="realDestination" />  
      </backupList>  
    </backupLists>  
    ```  
  
4.  <span data-ttu-id="cca3f-125">Definujte filtr tabulky a který přidruží filtr deadDestination koncový bod a seznamu zálohování koncový bod.</span><span class="sxs-lookup"><span data-stu-id="cca3f-125">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="cca3f-126">Směrovací služby se nejprve pokusí odeslat zprávu do cílového koncového bodu, přidružené k filtru.</span><span class="sxs-lookup"><span data-stu-id="cca3f-126">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="cca3f-127">Vzhledem k tomu, že deadDestination obsahuje adresu, která neodkazuje na spuštěnou službu, výsledkem je chyba sítě.</span><span class="sxs-lookup"><span data-stu-id="cca3f-127">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="cca3f-128">Směrovací služby pokusí odeslat zprávu do zadaného v backupEndpointlist koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="cca3f-128">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointlist.</span></span>  
  
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
  
5.  <span data-ttu-id="cca3f-129">Pokud chcete vyhodnotit příchozí zprávy s použitím filtru obsažené v tabulce filtru, musíte přidružit tabulku filtru koncové body služby pomocí směrování chování.</span><span class="sxs-lookup"><span data-stu-id="cca3f-129">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="cca3f-130">Následující příklad ukazuje přiřadit "filterTable1" s koncovými body služby.</span><span class="sxs-lookup"><span data-stu-id="cca3f-130">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="cca3f-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="cca3f-131">Example</span></span>  
 <span data-ttu-id="cca3f-132">Toto je úplný seznam všech konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="cca3f-132">Following is a complete listing of the configuration file.</span></span>  
  
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
