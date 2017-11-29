---
title: '&lt;udpDiscoveryEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 21f0165f8cda6701aa11058f2dac1bdde0f9ebbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltudpdiscoveryendpointgt"></a><span data-ttu-id="ce3bb-102">&lt;udpDiscoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="ce3bb-102">&lt;udpDiscoveryEndpoint&gt;</span></span>
<span data-ttu-id="ce3bb-103">Tento element konfigurace definuje standardní koncový bod, který je předem nakonfigurovaný pro operace zjišťování přes UDP vícesměrového vysílání vazby.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-103">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="ce3bb-104">Tento koncový bod má pevnou kontraktu a podporuje dvě verze protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-104">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="ce3bb-105">Kromě toho má pevnou vazba UDP a výchozí adresu podle specifikace WS-Discovery (WS-Discovery. dubna 2005 nebo V1.1 WS-Discovery)...</span><span class="sxs-lookup"><span data-stu-id="ce3bb-105">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1)..</span></span>  
  
 <span data-ttu-id="ce3bb-106">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ce3bb-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="ce3bb-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ce3bb-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce3bb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce3bb-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <discoveryEndpoint>           <standardEndpoint                  discoveryMode="Adhoc/Managed"                  discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"                  maxResponseDelay="Timespan"                  multicastAddress="Uri"                   name="String" />       </discoveryEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce3bb-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ce3bb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ce3bb-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce3bb-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ce3bb-111">Attributes</span></span>  
  
|<span data-ttu-id="ce3bb-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="ce3bb-112">Attribute</span></span>|<span data-ttu-id="ce3bb-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ce3bb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce3bb-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="ce3bb-114">discoveryMode</span></span>|<span data-ttu-id="ce3bb-115">Řetězec, který určuje režim zjišťování protokolu.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="ce3bb-116">Platné hodnoty jsou "Ad hoc" a "Spravovaný".</span><span class="sxs-lookup"><span data-stu-id="ce3bb-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="ce3bb-117">Ve spravovaném režimu protokol spoléhá na zjišťování Proxy, která funguje jako úložiště zjistitelný služeb.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="ce3bb-118">Ad hoc režim vyžaduje, aby protokol bude použit UDP vícesměrového vysílání mechanismus k vyhledání dostupných služeb.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="ce3bb-119">Tato hodnota je typu <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-119">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="ce3bb-120">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="ce3bb-120">discoveryVersion</span></span>|<span data-ttu-id="ce3bb-121">Řetězec, který určuje jeden z dvě verze protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="ce3bb-122">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="ce3bb-123">Tato hodnota je typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="ce3bb-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="ce3bb-124">maxResponseDelay</span></span>|<span data-ttu-id="ce3bb-125">Časový interval hodnotu, která určuje maximální hodnota zpoždění protokol zjišťování bude čekat před odesláním některé zprávy, jako je například testu nebo vyřešit shodu.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="ce3bb-126">Pokud jsou všechny ProbeMatches odesílá ve stejnou dobu, může způsobit storm sítě.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="ce3bb-127">Chcete-li tomu zabránit, odešlou ProbeMatches s náhodné zpoždění mezi každou ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="ce3bb-128">Hodnota náhodného zpoždění je v rozsahu 0 je hodnota nastavená tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="ce3bb-129">Pokud tento atribut je nastaven na hodnotu 0, jsou odesílány zprávy ProbeMatches ve smyčce úzkou bez jakéhokoli zpoždění.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="ce3bb-130">ProbeMatches zprávy, jinak se odesílají s některé náhodné zpoždění tak, aby celkový čas potřebný k zasílání ProbeMatches není delší než maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="ce3bb-131">Tato hodnota je platné pouze pro služby, není použita klienty.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-131">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="ce3bb-132">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="ce3bb-132">multicastAddress</span></span>|<span data-ttu-id="ce3bb-133">Identifikátor Uri, který určuje adresu vícesměrového vysílání pro odesílání a přijímání zpráv zjišťování.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-133">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="ce3bb-134">Výchozí hodnota je jako vyhovující specifikace protokolu adresy vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-134">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="ce3bb-135">Řetězec, který určuje název konfigurace standardní koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-135">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="ce3bb-136">Název je používán `endpointConfiguration` atribut propojení koncový bod standardní konfiguraci koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-136">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce3bb-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ce3bb-137">Child Elements</span></span>  
  
|<span data-ttu-id="ce3bb-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="ce3bb-138">Element</span></span>|<span data-ttu-id="ce3bb-139">Popis</span><span class="sxs-lookup"><span data-stu-id="ce3bb-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce3bb-140">\<udpTransportSettings ></span><span class="sxs-lookup"><span data-stu-id="ce3bb-140">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="ce3bb-141">Kolekce nastavení, která vám umožní nakonfigurovat přenosu UDP pro koncový bod UDP.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-141">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce3bb-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ce3bb-142">Parent Elements</span></span>  
  
|<span data-ttu-id="ce3bb-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="ce3bb-143">Element</span></span>|<span data-ttu-id="ce3bb-144">Popis</span><span class="sxs-lookup"><span data-stu-id="ce3bb-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce3bb-145">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ce3bb-145">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="ce3bb-146">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-146">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ce3bb-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce3bb-147">Example</span></span>  
 <span data-ttu-id="ce3bb-148">Následující příklad ukazuje služby naslouchání pro zjišťování zpráv přes protokol UDP. přenos vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="ce3bb-148">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ce3bb-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce3bb-149">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
