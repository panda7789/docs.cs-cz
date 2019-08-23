---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: e6e567e8a657b4c1683ae4abfb14f96a0f272e4a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934583"
---
# <a name="udpdiscoveryendpoint"></a><span data-ttu-id="e2828-101">\<udpDiscoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="e2828-101">\<udpDiscoveryEndpoint></span></span>
<span data-ttu-id="e2828-102">Tento prvek konfigurace definuje standardní koncový bod, který je předem nakonfigurovaný pro operace zjišťování prostřednictvím vazby vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="e2828-102">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="e2828-103">Tento koncový bod má pevný kontrakt a podporuje dvě verze protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="e2828-103">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="e2828-104">Kromě toho má pevnou vazbu UDP a výchozí adresu uvedenou ve specifikacích WS-Discovery (WS-Discovery duben 2005 nebo WS-Discovery V 1.1).</span><span class="sxs-lookup"><span data-stu-id="e2828-104">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
 <span data-ttu-id="e2828-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e2828-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e2828-106">\<Oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e2828-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2828-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2828-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2828-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e2828-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e2828-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e2828-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2828-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e2828-110">Attributes</span></span>  
  
|<span data-ttu-id="e2828-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e2828-111">Attribute</span></span>|<span data-ttu-id="e2828-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e2828-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2828-113">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="e2828-113">discoveryMode</span></span>|<span data-ttu-id="e2828-114">Řetězec, který určuje režim protokolu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="e2828-114">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="e2828-115">Platné hodnoty jsou "ad hoc" a "spravovaná".</span><span class="sxs-lookup"><span data-stu-id="e2828-115">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="e2828-116">V spravovaném režimu protokol spoléhá na proxy zjišťování, které funguje jako úložiště zjistitelných služeb.</span><span class="sxs-lookup"><span data-stu-id="e2828-116">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="e2828-117">Režim ad hoc vyžaduje, aby protokol používal k vyhledání dostupných služeb mechanismus vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="e2828-117">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="e2828-118">Tato hodnota je typu <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="e2828-118">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="e2828-119">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="e2828-119">discoveryVersion</span></span>|<span data-ttu-id="e2828-120">Řetězec, který určuje jednu ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="e2828-120">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="e2828-121">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="e2828-121">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="e2828-122">Tato hodnota je typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="e2828-122">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="e2828-123">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="e2828-123">maxResponseDelay</span></span>|<span data-ttu-id="e2828-124">Hodnota TimeSpan, která určuje maximální hodnotu pro prodlevu, po kterou bude protokol zjišťování čekat před odesláním určitých zpráv, jako je například shoda sondy nebo vyřešení shody.</span><span class="sxs-lookup"><span data-stu-id="e2828-124">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="e2828-125">Pokud jsou všechny ProbeMatches odesílány ve stejnou dobu, může dojít k zaplavení sítě.</span><span class="sxs-lookup"><span data-stu-id="e2828-125">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="e2828-126">Aby k tomu nedošlo, ProbeMatches se odesílají s náhodným zpožděním mezi jednotlivými ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="e2828-126">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="e2828-127">Náhodné zpoždění je v rozsahu 0 až k hodnotě nastavené tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="e2828-127">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="e2828-128">Pokud je tento atribut nastaven na hodnotu 0, zprávy ProbeMatches se odesílají v těsné smyčce bez jakéhokoli zpoždění.</span><span class="sxs-lookup"><span data-stu-id="e2828-128">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="e2828-129">V opačném případě se zprávy ProbeMatches odesílají s náhodným zpožděním tak, aby celková doba potřebná k odeslání všech ProbeMatches zpráv nepřekročila maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="e2828-129">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="e2828-130">Tato hodnota je relevantní jenom pro služby, které nepoužívají klienti.</span><span class="sxs-lookup"><span data-stu-id="e2828-130">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="e2828-131">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="e2828-131">multicastAddress</span></span>|<span data-ttu-id="e2828-132">Identifikátor URI, který určuje adresu vícesměrového vysílání, která se má použít pro odesílání a příjem zpráv zjišťování.</span><span class="sxs-lookup"><span data-stu-id="e2828-132">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="e2828-133">Výchozí hodnota je adresa vícesměrového vysílání, která odpovídá specifikaci protokolu.</span><span class="sxs-lookup"><span data-stu-id="e2828-133">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="e2828-134">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e2828-134">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="e2828-135">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="e2828-135">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2828-136">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e2828-136">Child Elements</span></span>  
  
|<span data-ttu-id="e2828-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="e2828-137">Element</span></span>|<span data-ttu-id="e2828-138">Popis</span><span class="sxs-lookup"><span data-stu-id="e2828-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2828-139">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="e2828-139">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="e2828-140">Kolekce nastavení, která umožňují nakonfigurovat přenos UDP pro koncový bod UDP.</span><span class="sxs-lookup"><span data-stu-id="e2828-140">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2828-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e2828-141">Parent Elements</span></span>  
  
|<span data-ttu-id="e2828-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="e2828-142">Element</span></span>|<span data-ttu-id="e2828-143">Popis</span><span class="sxs-lookup"><span data-stu-id="e2828-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2828-144">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e2828-144">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="e2828-145">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="e2828-145">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e2828-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2828-146">Example</span></span>  
 <span data-ttu-id="e2828-147">Následující příklad ukazuje službu, která naslouchá zprávám zjišťování prostřednictvím přenosu vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="e2828-147">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="DiscoveryEndpoint"
              kind="udpDiscoveryEndpoint" />
  </service>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="DiscoveryEndpoint"
                        version="WSDiscoveryApril2005" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="e2828-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2828-148">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
