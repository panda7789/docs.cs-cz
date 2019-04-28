---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: d1a3371872f5587a682b8242c29b71808508ca3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704050"
---
# <a name="discoveryendpoint"></a><span data-ttu-id="66d77-101">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="66d77-101">\<discoveryEndpoint></span></span>

<span data-ttu-id="66d77-102">Tento prvek konfigurace definuje standardní koncový bod s pevným kontraktem zjišťování.</span><span class="sxs-lookup"><span data-stu-id="66d77-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="66d77-103">Po přidání do konfigurace služby, se určuje, kde naslouchat zprávám zjišťování.</span><span class="sxs-lookup"><span data-stu-id="66d77-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="66d77-104">Po přidání do konfigurace klienta Určuje, kam má odesílat dotazy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="66d77-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="66d77-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="66d77-105">\<system.serviceModel></span></span>  
<span data-ttu-id="66d77-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="66d77-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66d77-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66d77-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66d77-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="66d77-108">Attributes and elements</span></span>

<span data-ttu-id="66d77-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="66d77-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66d77-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="66d77-110">Attributes</span></span>

| <span data-ttu-id="66d77-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="66d77-111">Attribute</span></span>        | <span data-ttu-id="66d77-112">Popis</span><span class="sxs-lookup"><span data-stu-id="66d77-112">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="66d77-113">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="66d77-113">discoveryMode</span></span>    | <span data-ttu-id="66d77-114">Řetězec, který určuje režim protokolu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="66d77-114">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="66d77-115">Platné hodnoty jsou "Ad hoc" a "Spravovaný".</span><span class="sxs-lookup"><span data-stu-id="66d77-115">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="66d77-116">Ve spravovaném režimu protokol spoléhá na Proxy zjišťování, která slouží jako úložiště zjistitelné služby.</span><span class="sxs-lookup"><span data-stu-id="66d77-116">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="66d77-117">Režimu ad hoc vyžaduje protokol UDP použití vícesměrového vysílání mechanismus pro vyhledání dostupných služeb.</span><span class="sxs-lookup"><span data-stu-id="66d77-117">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="66d77-118">Další informace o vlastnosti, naleznete v tématu <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="66d77-118">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="66d77-119">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="66d77-119">discoveryVersion</span></span> | <span data-ttu-id="66d77-120">Řetězec, který určuje jeden ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="66d77-120">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="66d77-121">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="66d77-121">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="66d77-122">Tato hodnota je typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="66d77-122">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="66d77-123">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="66d77-123">maxResponseDelay</span></span> | <span data-ttu-id="66d77-124">Časový interval hodnotu, která určuje maximální hodnotu zpoždění protokolu zjišťování bude čekat před odesláním některé zprávy, jako je například sběru dat nebo vyřešit shoda.</span><span class="sxs-lookup"><span data-stu-id="66d77-124">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="66d77-125">Pokud se všechny ProbeMatches odesílají ve stejnou dobu, může docházet k síti storm.</span><span class="sxs-lookup"><span data-stu-id="66d77-125">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="66d77-126">Chcete-li tomu zabránit, ProbeMatches odesílají pomocí náhodného zpoždění mezi každou ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="66d77-126">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="66d77-127">Náhodné zpoždění je v rozsahu od 0 do hodnoty nastavené v tomto atributu.</span><span class="sxs-lookup"><span data-stu-id="66d77-127">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="66d77-128">Pokud tento atribut je nastaven na hodnotu 0, jsou odesílány zprávy ProbeMatches v těsné smyčce bez jakéhokoli zpoždění.</span><span class="sxs-lookup"><span data-stu-id="66d77-128">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="66d77-129">V opačném případě případě odesílají zprávy ProbeMatches s některé náhodné zpoždění nepřekročí celkový čas potřebný k odeslání všech zpráv ProbeMatches maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="66d77-129">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="66d77-130">Tato hodnota platí pouze pro služby, se používají klienti.</span><span class="sxs-lookup"><span data-stu-id="66d77-130">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="66d77-131">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="66d77-131">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="66d77-132">Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="66d77-132">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="66d77-133">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="66d77-133">Child elements</span></span>

<span data-ttu-id="66d77-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="66d77-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66d77-135">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="66d77-135">Parent elements</span></span>

| <span data-ttu-id="66d77-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="66d77-136">Element</span></span> | <span data-ttu-id="66d77-137">Popis</span><span class="sxs-lookup"><span data-stu-id="66d77-137">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="66d77-138">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="66d77-138">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | <span data-ttu-id="66d77-139">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="66d77-139">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="66d77-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="66d77-140">Example</span></span>

<span data-ttu-id="66d77-141">Následující příklad ukazuje služba naslouchá na zprávy zjišťování přes rovnocenný přenos net vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="66d77-141">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="66d77-142">Příklad explicitně určuje WS-Discovery verze 2005. dubna.</span><span class="sxs-lookup"><span data-stu-id="66d77-142">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="66d77-143">Standardní koncový bod konfigurace je definována na službu a se nedají sdílet mezi službu.</span><span class="sxs-lookup"><span data-stu-id="66d77-143">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="66d77-144">Pokud jiná služba by měl mít stejný koncový bod zjišťování, stejnou konfiguraci musí být přidán do části této služby.</span><span class="sxs-lookup"><span data-stu-id="66d77-144">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66d77-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66d77-145">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
