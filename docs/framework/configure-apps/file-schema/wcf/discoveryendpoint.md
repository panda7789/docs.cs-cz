---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 6bb5be09ea598296f01e186280c45757dee9405d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919135"
---
# <a name="discoveryendpoint"></a><span data-ttu-id="e56b5-101">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="e56b5-101">\<discoveryEndpoint></span></span>

<span data-ttu-id="e56b5-102">Tento prvek konfigurace definuje standardní koncový bod s pevným kontraktem zjišťování.</span><span class="sxs-lookup"><span data-stu-id="e56b5-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="e56b5-103">Po přidání do konfigurace služby určuje, kde naslouchat pro zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="e56b5-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="e56b5-104">Po přidání do konfigurace klienta Určuje, kam se mají odesílat dotazy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="e56b5-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="e56b5-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e56b5-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e56b5-106">\<Oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e56b5-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e56b5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e56b5-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e56b5-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e56b5-108">Attributes and elements</span></span>

<span data-ttu-id="e56b5-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e56b5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e56b5-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e56b5-110">Attributes</span></span>

| <span data-ttu-id="e56b5-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e56b5-111">Attribute</span></span>        | <span data-ttu-id="e56b5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e56b5-112">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="e56b5-113">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="e56b5-113">discoveryMode</span></span>    | <span data-ttu-id="e56b5-114">Řetězec, který určuje režim protokolu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="e56b5-114">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="e56b5-115">Platné hodnoty jsou "ad hoc" a "spravovaná".</span><span class="sxs-lookup"><span data-stu-id="e56b5-115">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="e56b5-116">V spravovaném režimu protokol spoléhá na proxy zjišťování, které funguje jako úložiště zjistitelných služeb.</span><span class="sxs-lookup"><span data-stu-id="e56b5-116">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="e56b5-117">Režim ad hoc vyžaduje, aby protokol používal k vyhledání dostupných služeb mechanismus vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="e56b5-117">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="e56b5-118">Další informace o této vlastnosti naleznete v tématu <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="e56b5-118">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="e56b5-119">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="e56b5-119">discoveryVersion</span></span> | <span data-ttu-id="e56b5-120">Řetězec, který určuje jednu ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="e56b5-120">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="e56b5-121">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="e56b5-121">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="e56b5-122">Tato hodnota je typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="e56b5-122">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="e56b5-123">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="e56b5-123">maxResponseDelay</span></span> | <span data-ttu-id="e56b5-124">Hodnota TimeSpan, která určuje maximální hodnotu pro prodlevu, po kterou bude protokol zjišťování čekat před odesláním určitých zpráv, jako je například shoda sondy nebo vyřešení shody.</span><span class="sxs-lookup"><span data-stu-id="e56b5-124">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="e56b5-125">Pokud jsou všechny ProbeMatches odesílány ve stejnou dobu, může dojít k zaplavení sítě.</span><span class="sxs-lookup"><span data-stu-id="e56b5-125">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="e56b5-126">Aby k tomu nedošlo, ProbeMatches se odesílají s náhodným zpožděním mezi jednotlivými ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="e56b5-126">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="e56b5-127">Náhodné zpoždění je v rozsahu 0 až k hodnotě nastavené tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="e56b5-127">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="e56b5-128">Pokud je tento atribut nastaven na hodnotu 0, zprávy ProbeMatches se odesílají v těsné smyčce bez jakéhokoli zpoždění.</span><span class="sxs-lookup"><span data-stu-id="e56b5-128">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="e56b5-129">V opačném případě se zprávy ProbeMatches odesílají s náhodným zpožděním tak, aby celková doba potřebná k odeslání všech ProbeMatches zpráv nepřekročila maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="e56b5-129">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="e56b5-130">Tato hodnota je relevantní jenom pro služby, které nepoužívají klienti.</span><span class="sxs-lookup"><span data-stu-id="e56b5-130">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="e56b5-131">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e56b5-131">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="e56b5-132">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="e56b5-132">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="e56b5-133">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="e56b5-133">Child elements</span></span>

<span data-ttu-id="e56b5-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="e56b5-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e56b5-135">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="e56b5-135">Parent elements</span></span>

| <span data-ttu-id="e56b5-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="e56b5-136">Element</span></span> | <span data-ttu-id="e56b5-137">Popis</span><span class="sxs-lookup"><span data-stu-id="e56b5-137">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="e56b5-138">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e56b5-138">\<standardEndpoints></span></span>](standardendpoints.md) | <span data-ttu-id="e56b5-139">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="e56b5-139">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="e56b5-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="e56b5-140">Example</span></span>

<span data-ttu-id="e56b5-141">Následující příklad demonstruje službu, která naslouchá na zprávách zjišťování přes přenos přes síť s vícesměrovým vysíláním.</span><span class="sxs-lookup"><span data-stu-id="e56b5-141">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="e56b5-142">Příklad explicitně určuje verzi WS-Discovery z dubna 2005.</span><span class="sxs-lookup"><span data-stu-id="e56b5-142">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="e56b5-143">Standardní konfigurace koncového bodu je definována pro každou službu a nelze ji sdílet přes službu.</span><span class="sxs-lookup"><span data-stu-id="e56b5-143">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="e56b5-144">Pokud by měla mít stejný koncový bod zjišťování jiná služba, je nutné do oddílu této služby přidat stejnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e56b5-144">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="peerNetDiscovery"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              kind="discoveryEndpoint"
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  </service>
</services>
<standardEndpoints>
  <discoveryEndpoint>
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"
                      version="WSDiscoveryApril2005" />
  </discoveryEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="e56b5-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e56b5-145">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
