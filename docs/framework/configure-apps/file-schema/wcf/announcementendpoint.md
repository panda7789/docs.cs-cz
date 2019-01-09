---
title: '&lt;AnnouncementEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: fe278da539af59a32edf5a626461dbec0ba3887d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151641"
---
# <a name="ltannouncementendpointgt"></a><span data-ttu-id="90e62-102">&lt;AnnouncementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="90e62-102">&lt;announcementEndpoint&gt;</span></span>
<span data-ttu-id="90e62-103">Tento prvek konfigurace definuje standardní koncový bod s pevným kontraktem oznámení.</span><span class="sxs-lookup"><span data-stu-id="90e62-103">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="90e62-104">Službu můžete volitelně oznámit její dostupnost odesláním zprávu online a offline oznámení při otevření nebo zavření v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="90e62-104">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="90e62-105">Služba Windows Communication Foundation (WCF) určuje koncových bodů oznámení v [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) prvku a používá AnnouncementClient provádět oznámení.</span><span class="sxs-lookup"><span data-stu-id="90e62-105">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="90e62-106">Klient přejí k naslouchání pro oznámení z jiné služby, ve skutečnosti funguje jako služba WCF; proto budete muset nakonfigurovat koncových bodů oznámení pro daného klienta v [ \<služby >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) oddílu.</span><span class="sxs-lookup"><span data-stu-id="90e62-106">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="90e62-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="90e62-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="90e62-108">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="90e62-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90e62-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90e62-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90e62-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="90e62-110">Attributes and Elements</span></span>  
 <span data-ttu-id="90e62-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="90e62-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90e62-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="90e62-112">Attributes</span></span>  
  
|<span data-ttu-id="90e62-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="90e62-113">Attribute</span></span>|<span data-ttu-id="90e62-114">Popis</span><span class="sxs-lookup"><span data-stu-id="90e62-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90e62-115">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="90e62-115">discoveryVersion</span></span>|<span data-ttu-id="90e62-116">Řetězec, který určuje jeden ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="90e62-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="90e62-117">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="90e62-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="90e62-118">Tato hodnota je typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="90e62-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="90e62-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="90e62-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="90e62-120">Časový interval hodnotu, která určuje maximální hodnotu zpoždění protokolu zjišťování bude čekat před odesláním uvítací zprávu.</span><span class="sxs-lookup"><span data-stu-id="90e62-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="90e62-121">Náhodný čas hodnotu mezi 0 a hodnota tohoto atributu bude čekat zprávy před odesláním.</span><span class="sxs-lookup"><span data-stu-id="90e62-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="90e62-122">Tento atribut slouží k nastavení malé náhodné zpoždění zabránil výstrahami sítě v případě, že se odesílá do sítě a všechny služby jsou zase online ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="90e62-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="90e62-123">name</span><span class="sxs-lookup"><span data-stu-id="90e62-123">name</span></span>|<span data-ttu-id="90e62-124">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="90e62-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="90e62-125">Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="90e62-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90e62-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="90e62-126">Child Elements</span></span>  
 <span data-ttu-id="90e62-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="90e62-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90e62-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="90e62-128">Parent Elements</span></span>  
  
|<span data-ttu-id="90e62-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="90e62-129">Element</span></span>|<span data-ttu-id="90e62-130">Popis</span><span class="sxs-lookup"><span data-stu-id="90e62-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90e62-131">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="90e62-131">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="90e62-132">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="90e62-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="90e62-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="90e62-133">Example</span></span>  
 <span data-ttu-id="90e62-134">Následující příklad ukazuje klienta prostřednictvím protokolu http a peernet naslouchání pro zprávy oznámení.</span><span class="sxs-lookup"><span data-stu-id="90e62-134">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90e62-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="90e62-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
