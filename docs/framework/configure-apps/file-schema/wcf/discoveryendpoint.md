---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32b14f8fb3235040a51455f2099a403c8312c699
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855391"
---
# <a name="discoveryendpoint"></a><span data-ttu-id="eca6e-101">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="eca6e-101">\<discoveryEndpoint></span></span>

<span data-ttu-id="eca6e-102">Tento prvek konfigurace definuje standardní koncový bod s pevným kontraktem zjišťování.</span><span class="sxs-lookup"><span data-stu-id="eca6e-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="eca6e-103">Po přidání do konfigurace služby určuje, kde naslouchat pro zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="eca6e-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="eca6e-104">Po přidání do konfigurace klienta Určuje, kam se mají odesílat dotazy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="eca6e-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="eca6e-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eca6e-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eca6e-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="eca6e-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="eca6e-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="eca6e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="eca6e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="eca6e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca6e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eca6e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eca6e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eca6e-110">Attributes and elements</span></span>

<span data-ttu-id="eca6e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eca6e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eca6e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="eca6e-112">Attributes</span></span>

| <span data-ttu-id="eca6e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="eca6e-113">Attribute</span></span>        | <span data-ttu-id="eca6e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="eca6e-114">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="eca6e-115">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="eca6e-115">discoveryMode</span></span>    | <span data-ttu-id="eca6e-116">Řetězec, který určuje režim protokolu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="eca6e-116">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="eca6e-117">Platné hodnoty jsou "ad hoc" a "spravovaná".</span><span class="sxs-lookup"><span data-stu-id="eca6e-117">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="eca6e-118">V spravovaném režimu protokol spoléhá na proxy zjišťování, které funguje jako úložiště zjistitelných služeb.</span><span class="sxs-lookup"><span data-stu-id="eca6e-118">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="eca6e-119">Režim ad hoc vyžaduje, aby protokol používal k vyhledání dostupných služeb mechanismus vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="eca6e-119">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="eca6e-120">Další informace o této vlastnosti naleznete v tématu <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="eca6e-120">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="eca6e-121">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="eca6e-121">discoveryVersion</span></span> | <span data-ttu-id="eca6e-122">Řetězec, který určuje jednu ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="eca6e-122">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="eca6e-123">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="eca6e-123">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="eca6e-124">Tato hodnota je typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="eca6e-124">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="eca6e-125">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="eca6e-125">maxResponseDelay</span></span> | <span data-ttu-id="eca6e-126">Hodnota TimeSpan, která určuje maximální hodnotu pro prodlevu, po kterou bude protokol zjišťování čekat před odesláním určitých zpráv, jako je například shoda sondy nebo vyřešení shody.</span><span class="sxs-lookup"><span data-stu-id="eca6e-126">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="eca6e-127">Pokud jsou všechny ProbeMatches odesílány ve stejnou dobu, může dojít k zaplavení sítě.</span><span class="sxs-lookup"><span data-stu-id="eca6e-127">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="eca6e-128">Aby k tomu nedošlo, ProbeMatches se odesílají s náhodným zpožděním mezi jednotlivými ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="eca6e-128">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="eca6e-129">Náhodné zpoždění je v rozsahu 0 až k hodnotě nastavené tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="eca6e-129">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="eca6e-130">Pokud je tento atribut nastaven na hodnotu 0, zprávy ProbeMatches se odesílají v těsné smyčce bez jakéhokoli zpoždění.</span><span class="sxs-lookup"><span data-stu-id="eca6e-130">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="eca6e-131">V opačném případě se zprávy ProbeMatches odesílají s náhodným zpožděním tak, aby celková doba potřebná k odeslání všech ProbeMatches zpráv nepřekročila maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="eca6e-131">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="eca6e-132">Tato hodnota je relevantní jenom pro služby, které nepoužívají klienti.</span><span class="sxs-lookup"><span data-stu-id="eca6e-132">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="eca6e-133">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="eca6e-133">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="eca6e-134">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="eca6e-134">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="eca6e-135">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="eca6e-135">Child elements</span></span>

<span data-ttu-id="eca6e-136">Žádné</span><span class="sxs-lookup"><span data-stu-id="eca6e-136">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eca6e-137">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="eca6e-137">Parent elements</span></span>

| <span data-ttu-id="eca6e-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="eca6e-138">Element</span></span> | <span data-ttu-id="eca6e-139">Popis</span><span class="sxs-lookup"><span data-stu-id="eca6e-139">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="eca6e-140">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="eca6e-140">\<standardEndpoints></span></span>](standardendpoints.md) | <span data-ttu-id="eca6e-141">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="eca6e-141">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="eca6e-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="eca6e-142">Example</span></span>

<span data-ttu-id="eca6e-143">Následující příklad demonstruje službu, která naslouchá na zprávách zjišťování přes přenos přes síť s vícesměrovým vysíláním.</span><span class="sxs-lookup"><span data-stu-id="eca6e-143">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="eca6e-144">Příklad explicitně určuje verzi WS-Discovery z dubna 2005.</span><span class="sxs-lookup"><span data-stu-id="eca6e-144">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="eca6e-145">Standardní konfigurace koncového bodu je definována pro každou službu a nelze ji sdílet přes službu.</span><span class="sxs-lookup"><span data-stu-id="eca6e-145">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="eca6e-146">Pokud by měla mít stejný koncový bod zjišťování jiná služba, je nutné do oddílu této služby přidat stejnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="eca6e-146">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eca6e-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eca6e-147">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
