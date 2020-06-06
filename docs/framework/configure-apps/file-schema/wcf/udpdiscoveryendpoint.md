---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 1729255c68c75f824b8cd8c87f106a4a9b3550f6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854890"
---
# \<udpDiscoveryEndpoint>
<span data-ttu-id="641ec-101">Tento prvek konfigurace definuje standardní koncový bod, který je předem nakonfigurovaný pro operace zjišťování prostřednictvím vazby vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="641ec-101">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="641ec-102">Tento koncový bod má pevný kontrakt a podporuje dvě verze protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="641ec-102">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="641ec-103">Kromě toho má pevnou vazbu UDP a výchozí adresu uvedenou ve specifikacích WS-Discovery (WS-Discovery duben 2005 nebo WS-Discovery V 1.1).</span><span class="sxs-lookup"><span data-stu-id="641ec-103">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpDiscoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="641ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="641ec-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="641ec-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="641ec-105">Attributes and Elements</span></span>  
 <span data-ttu-id="641ec-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="641ec-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="641ec-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="641ec-107">Attributes</span></span>  
  
|<span data-ttu-id="641ec-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="641ec-108">Attribute</span></span>|<span data-ttu-id="641ec-109">Popis</span><span class="sxs-lookup"><span data-stu-id="641ec-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="641ec-110">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="641ec-110">discoveryMode</span></span>|<span data-ttu-id="641ec-111">Řetězec, který určuje režim protokolu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="641ec-111">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="641ec-112">Platné hodnoty jsou "ad hoc" a "spravovaná".</span><span class="sxs-lookup"><span data-stu-id="641ec-112">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="641ec-113">V spravovaném režimu protokol spoléhá na proxy zjišťování, které funguje jako úložiště zjistitelných služeb.</span><span class="sxs-lookup"><span data-stu-id="641ec-113">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="641ec-114">Režim ad hoc vyžaduje, aby protokol používal k vyhledání dostupných služeb mechanismus vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="641ec-114">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="641ec-115">Tato hodnota je typu <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="641ec-115">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="641ec-116">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="641ec-116">discoveryVersion</span></span>|<span data-ttu-id="641ec-117">Řetězec, který určuje jednu ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="641ec-117">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="641ec-118">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="641ec-118">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="641ec-119">Tato hodnota je typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="641ec-119">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="641ec-120">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="641ec-120">maxResponseDelay</span></span>|<span data-ttu-id="641ec-121">Hodnota TimeSpan, která určuje maximální hodnotu pro prodlevu, po kterou bude protokol zjišťování čekat před odesláním určitých zpráv, jako je například shoda sondy nebo vyřešení shody.</span><span class="sxs-lookup"><span data-stu-id="641ec-121">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="641ec-122">Pokud jsou všechny ProbeMatches odesílány ve stejnou dobu, může dojít k zaplavení sítě.</span><span class="sxs-lookup"><span data-stu-id="641ec-122">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="641ec-123">Aby k tomu nedošlo, ProbeMatches se odesílají s náhodným zpožděním mezi jednotlivými ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="641ec-123">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="641ec-124">Náhodné zpoždění je v rozsahu 0 až k hodnotě nastavené tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="641ec-124">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="641ec-125">Pokud je tento atribut nastaven na hodnotu 0, zprávy ProbeMatches se odesílají v těsné smyčce bez jakéhokoli zpoždění.</span><span class="sxs-lookup"><span data-stu-id="641ec-125">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="641ec-126">V opačném případě se zprávy ProbeMatches odesílají s náhodným zpožděním tak, aby celková doba potřebná k odeslání všech ProbeMatches zpráv nepřekročila maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="641ec-126">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="641ec-127">Tato hodnota je relevantní jenom pro služby, které nepoužívají klienti.</span><span class="sxs-lookup"><span data-stu-id="641ec-127">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="641ec-128">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="641ec-128">multicastAddress</span></span>|<span data-ttu-id="641ec-129">Identifikátor URI, který určuje adresu vícesměrového vysílání, která se má použít pro odesílání a příjem zpráv zjišťování.</span><span class="sxs-lookup"><span data-stu-id="641ec-129">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="641ec-130">Výchozí hodnota je adresa vícesměrového vysílání, která odpovídá specifikaci protokolu.</span><span class="sxs-lookup"><span data-stu-id="641ec-130">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="641ec-131">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="641ec-131">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="641ec-132">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="641ec-132">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="641ec-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="641ec-133">Child Elements</span></span>  
  
|<span data-ttu-id="641ec-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="641ec-134">Element</span></span>|<span data-ttu-id="641ec-135">Description</span><span class="sxs-lookup"><span data-stu-id="641ec-135">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="641ec-136">Kolekce nastavení, která umožňují nakonfigurovat přenos UDP pro koncový bod UDP.</span><span class="sxs-lookup"><span data-stu-id="641ec-136">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="641ec-137">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="641ec-137">Parent Elements</span></span>  
  
|<span data-ttu-id="641ec-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="641ec-138">Element</span></span>|<span data-ttu-id="641ec-139">Description</span><span class="sxs-lookup"><span data-stu-id="641ec-139">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="641ec-140">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="641ec-140">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="641ec-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="641ec-141">Example</span></span>  
 <span data-ttu-id="641ec-142">Následující příklad ukazuje službu, která naslouchá zprávám zjišťování prostřednictvím přenosu vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="641ec-142">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="641ec-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="641ec-143">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
