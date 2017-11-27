---
title: '&lt;udpAnnoucementEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 85fcd6b81cca9f9b7a71ebdda96ef75e1dc1405a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltudpannoucementendpointgt"></a><span data-ttu-id="c1cc0-102">&lt;udpAnnoucementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="c1cc0-102">&lt;udpAnnoucementEndpoint&gt;</span></span>
<span data-ttu-id="c1cc0-103">Tento element konfigurace definuje standardní koncový bod, který je používán služby pro odeslání zpráv oznámení vazbu UDP.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-103">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="c1cc0-104">Má pevnou kontraktu a podporuje dvě verze zjišťování.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-104">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="c1cc0-105">Kromě toho má vazbu pevné UDP a adresu výchozí hodnotu podle specifikace WS-Discovery (WS-Discovery. dubna 2005 nebo WS-Discovery verze 1.1).</span><span class="sxs-lookup"><span data-stu-id="c1cc0-105">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="c1cc0-106">Můžete zadat adresu vícesměrového vysílání pro odesílání a přijímání zpráv oznámení.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-106">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="c1cc0-107">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c1cc0-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="c1cc0-108">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c1cc0-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1cc0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1cc0-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005" 
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1cc0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c1cc0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c1cc0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1cc0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c1cc0-112">Attributes</span></span>  
  
|<span data-ttu-id="c1cc0-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c1cc0-113">Attribute</span></span>|<span data-ttu-id="c1cc0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c1cc0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1cc0-115">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="c1cc0-115">discoveryVersion</span></span>|<span data-ttu-id="c1cc0-116">Řetězec, který určuje jeden z dvě verze protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="c1cc0-117">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="c1cc0-118">Tato hodnota je typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="c1cc0-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="c1cc0-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="c1cc0-120">Hodnota časového rozpětí, která určuje maximální hodnotu zpoždění protokol zjišťování bude čekat před odesláním zprávy Hello.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="c1cc0-121">Před odesláním zprávy vyčká na hodnotu náhodný čas mezi 0 a hodnota tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="c1cc0-122">Tento atribut slouží k nastavení malé, náhodné zpoždění, aby se zabránilo zahlcení sítě, když síť prochází a všechny služby dostane zpět online ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="c1cc0-123">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="c1cc0-123">multicastAddress</span></span>|<span data-ttu-id="c1cc0-124">Identifikátor URI, který určuje adresu vícesměrového vysílání pro odesílání a přijímání zpráv zjišťování.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-124">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="c1cc0-125">Výchozí hodnota je jako vyhovující specifikace protokolu adresy vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-125">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="c1cc0-126">name</span><span class="sxs-lookup"><span data-stu-id="c1cc0-126">name</span></span>|<span data-ttu-id="c1cc0-127">Řetězec, který určuje název konfigurace standardní koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-127">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="c1cc0-128">Název je používán `endpointConfiguration` atribut propojení koncový bod standardní konfiguraci koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-128">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1cc0-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c1cc0-129">Child Elements</span></span>  
  
|<span data-ttu-id="c1cc0-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="c1cc0-130">Element</span></span>|<span data-ttu-id="c1cc0-131">Popis</span><span class="sxs-lookup"><span data-stu-id="c1cc0-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1cc0-132">\<udpTransportSettings ></span><span class="sxs-lookup"><span data-stu-id="c1cc0-132">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="c1cc0-133">Kolekce nastavení, která vám umožní nakonfigurovat přenosu UDP pro koncový bod UDP.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-133">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1cc0-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c1cc0-134">Parent Elements</span></span>  
  
|<span data-ttu-id="c1cc0-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="c1cc0-135">Element</span></span>|<span data-ttu-id="c1cc0-136">Popis</span><span class="sxs-lookup"><span data-stu-id="c1cc0-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1cc0-137">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c1cc0-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="c1cc0-138">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-138">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c1cc0-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1cc0-139">Example</span></span>  
 <span data-ttu-id="c1cc0-140">Následující příklad ukazuje, klient naslouchání pro oznámení přes protokol UDP. přenos vícesměrového vysílání s výchozí adresa vícesměrového vysílání a UDP přenos vícesměrového vysílání se zadanou adresou vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="c1cc0-140">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
```xml  
<services>  
  <service name="ServiceAnnouncementListener">  
      <endpoint name="udpAnnouncementEndpointStandard"  
                kind="udpAnnouncementEndpoint"  
                bindingConfiguration="..." />  
      <endpoint name="udpAnnouncementEndpoint2"  
                kind="udpAnnouncementEndpoint"  
                endpointConfiguration="AnnouncementConfiguration3702"  
                bindingConfiguration="..." />  
...  
  </service>  
</services>  
<standardEndpoints>  
  <udpAnnouncementEndpoint>  
     <standardEndpoint name="AnnouncementConfiguration2"   
          version="WSDiscoveryApril2005"   
          multicastAddress="soap.udp://239.255.255.250:3703"/>          
  </udpAnnouncementEndpoint>  
</standardEndpoints>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1cc0-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1cc0-141">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
