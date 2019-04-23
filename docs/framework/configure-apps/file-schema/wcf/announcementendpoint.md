---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: 4f3cf2748acc75b0ec83732664c5f97114f3663a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195121"
---
# <a name="announcementendpoint"></a><span data-ttu-id="be378-101">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="be378-101">\<announcementEndpoint></span></span>
<span data-ttu-id="be378-102">Tento prvek konfigurace definuje standardní koncový bod s pevným kontraktem oznámení.</span><span class="sxs-lookup"><span data-stu-id="be378-102">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="be378-103">Službu můžete volitelně oznámit její dostupnost odesláním zprávu online a offline oznámení při otevření nebo zavření v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="be378-103">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="be378-104">Služba Windows Communication Foundation (WCF) určuje koncových bodů oznámení v [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) prvku a používá AnnouncementClient provádět oznámení.</span><span class="sxs-lookup"><span data-stu-id="be378-104">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="be378-105">Klient přejí k naslouchání pro oznámení z jiné služby, ve skutečnosti funguje jako služba WCF; proto budete muset nakonfigurovat koncových bodů oznámení pro daného klienta v [ \<služby >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) oddílu.</span><span class="sxs-lookup"><span data-stu-id="be378-105">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="be378-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="be378-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="be378-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="be378-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be378-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be378-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be378-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="be378-109">Attributes and Elements</span></span>  
 <span data-ttu-id="be378-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="be378-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be378-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="be378-111">Attributes</span></span>  
  
|<span data-ttu-id="be378-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="be378-112">Attribute</span></span>|<span data-ttu-id="be378-113">Popis</span><span class="sxs-lookup"><span data-stu-id="be378-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be378-114">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="be378-114">discoveryVersion</span></span>|<span data-ttu-id="be378-115">Řetězec, který určuje jeden ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="be378-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="be378-116">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="be378-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="be378-117">Tato hodnota je typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="be378-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="be378-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="be378-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="be378-119">Časový interval hodnotu, která určuje maximální hodnotu zpoždění protokolu zjišťování bude čekat před odesláním uvítací zprávu.</span><span class="sxs-lookup"><span data-stu-id="be378-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="be378-120">Náhodný čas hodnotu mezi 0 a hodnota tohoto atributu bude čekat zprávy před odesláním.</span><span class="sxs-lookup"><span data-stu-id="be378-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="be378-121">Tento atribut slouží k nastavení malé náhodné zpoždění zabránil výstrahami sítě v případě, že se odesílá do sítě a všechny služby jsou zase online ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="be378-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="be378-122">name</span><span class="sxs-lookup"><span data-stu-id="be378-122">name</span></span>|<span data-ttu-id="be378-123">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="be378-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="be378-124">Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="be378-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be378-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="be378-125">Child Elements</span></span>  
 <span data-ttu-id="be378-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="be378-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="be378-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="be378-127">Parent Elements</span></span>  
  
|<span data-ttu-id="be378-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="be378-128">Element</span></span>|<span data-ttu-id="be378-129">Popis</span><span class="sxs-lookup"><span data-stu-id="be378-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be378-130">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="be378-130">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="be378-131">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="be378-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="be378-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="be378-132">Example</span></span>  
 <span data-ttu-id="be378-133">Následující příklad ukazuje klienta prostřednictvím protokolu http a peernet naslouchání pro zprávy oznámení.</span><span class="sxs-lookup"><span data-stu-id="be378-133">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="httpAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="basicHttpBinding"
              address="announcements" />
    <endpoint name="peerNetAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  ...
  </service>
</services>

<standardEndpoints>
  <announcementEndpoint>
    <standardEndpoint name="httpAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
    <standardEndpoint name="peerNetAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
  </announcementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="be378-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be378-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
