---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32b14f8fb3235040a51455f2099a403c8312c699
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855391"
---
# \<discoveryEndpoint>

<span data-ttu-id="06949-101">Tento prvek konfigurace definuje standardní koncový bod s pevným kontraktem zjišťování.</span><span class="sxs-lookup"><span data-stu-id="06949-101">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="06949-102">Po přidání do konfigurace služby určuje, kde naslouchat pro zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="06949-102">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="06949-103">Po přidání do konfigurace klienta Určuje, kam se mají odesílat dotazy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="06949-103">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="06949-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06949-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06949-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="06949-105">Attributes and elements</span></span>

<span data-ttu-id="06949-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="06949-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06949-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="06949-107">Attributes</span></span>

| <span data-ttu-id="06949-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="06949-108">Attribute</span></span>        | <span data-ttu-id="06949-109">Popis</span><span class="sxs-lookup"><span data-stu-id="06949-109">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="06949-110">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="06949-110">discoveryMode</span></span>    | <span data-ttu-id="06949-111">Řetězec, který určuje režim protokolu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="06949-111">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="06949-112">Platné hodnoty jsou "ad hoc" a "spravovaná".</span><span class="sxs-lookup"><span data-stu-id="06949-112">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="06949-113">V spravovaném režimu protokol spoléhá na proxy zjišťování, které funguje jako úložiště zjistitelných služeb.</span><span class="sxs-lookup"><span data-stu-id="06949-113">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="06949-114">Režim ad hoc vyžaduje, aby protokol používal k vyhledání dostupných služeb mechanismus vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="06949-114">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="06949-115">Další informace o této vlastnosti naleznete v tématu <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A> .</span><span class="sxs-lookup"><span data-stu-id="06949-115">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="06949-116">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="06949-116">discoveryVersion</span></span> | <span data-ttu-id="06949-117">Řetězec, který určuje jednu ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="06949-117">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="06949-118">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="06949-118">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="06949-119">Tato hodnota je typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="06949-119">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="06949-120">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="06949-120">maxResponseDelay</span></span> | <span data-ttu-id="06949-121">Hodnota TimeSpan, která určuje maximální hodnotu pro prodlevu, po kterou bude protokol zjišťování čekat před odesláním určitých zpráv, jako je například shoda sondy nebo vyřešení shody.</span><span class="sxs-lookup"><span data-stu-id="06949-121">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="06949-122">Pokud jsou všechny ProbeMatches odesílány ve stejnou dobu, může dojít k zaplavení sítě.</span><span class="sxs-lookup"><span data-stu-id="06949-122">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="06949-123">Aby k tomu nedošlo, ProbeMatches se odesílají s náhodným zpožděním mezi jednotlivými ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="06949-123">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="06949-124">Náhodné zpoždění je v rozsahu 0 až k hodnotě nastavené tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="06949-124">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="06949-125">Pokud je tento atribut nastaven na hodnotu 0, zprávy ProbeMatches se odesílají v těsné smyčce bez jakéhokoli zpoždění.</span><span class="sxs-lookup"><span data-stu-id="06949-125">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="06949-126">V opačném případě se zprávy ProbeMatches odesílají s náhodným zpožděním tak, aby celková doba potřebná k odeslání všech ProbeMatches zpráv nepřekročila maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="06949-126">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="06949-127">Tato hodnota je relevantní jenom pro služby, které nepoužívají klienti.</span><span class="sxs-lookup"><span data-stu-id="06949-127">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="06949-128">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="06949-128">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="06949-129">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="06949-129">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="06949-130">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="06949-130">Child elements</span></span>

<span data-ttu-id="06949-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="06949-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06949-132">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="06949-132">Parent elements</span></span>

| <span data-ttu-id="06949-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="06949-133">Element</span></span> | <span data-ttu-id="06949-134">Description</span><span class="sxs-lookup"><span data-stu-id="06949-134">Description</span></span> |  
| ------- | ----------- |  
| [\<standardEndpoints>](standardendpoints.md) | <span data-ttu-id="06949-135">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="06949-135">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="06949-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="06949-136">Example</span></span>

<span data-ttu-id="06949-137">Následující příklad demonstruje službu, která naslouchá na zprávách zjišťování přes přenos přes síť s vícesměrovým vysíláním.</span><span class="sxs-lookup"><span data-stu-id="06949-137">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="06949-138">Příklad explicitně určuje verzi WS-Discovery z dubna 2005.</span><span class="sxs-lookup"><span data-stu-id="06949-138">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="06949-139">Standardní konfigurace koncového bodu je definována pro každou službu a nelze ji sdílet přes službu.</span><span class="sxs-lookup"><span data-stu-id="06949-139">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="06949-140">Pokud by měla mít stejný koncový bod zjišťování jiná služba, je nutné do oddílu této služby přidat stejnou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="06949-140">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06949-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="06949-141">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
