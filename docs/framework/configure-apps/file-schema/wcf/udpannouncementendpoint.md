---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 3ffb18fbd410922df4311180ef7af5153ba5c0f5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379816"
---
# <a name="udpannouncementendpoint"></a><span data-ttu-id="b3ff8-101">\<udpAnnouncementEndpoint></span><span class="sxs-lookup"><span data-stu-id="b3ff8-101">\<udpAnnouncementEndpoint></span></span>
<span data-ttu-id="b3ff8-102">Tento prvek konfigurace definuje standardní koncový bod služby používá k odeslání zpráv oznámení UDP vazby.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-102">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="b3ff8-103">Má pevnou kontrakt a podporuje dvě verze zjišťování.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-103">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="b3ff8-104">Kromě toho má pevnou vazbou UDP a adresu výchozí hodnotu podle specifikace WS-Discovery (WS-Discovery dubna 2005 nebo verze 1.1 WS-Discovery).</span><span class="sxs-lookup"><span data-stu-id="b3ff8-104">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="b3ff8-105">Můžete zadat adresu vícesměrového vysílání pro odesílání a příjem zpráv s oznámením.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-105">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="b3ff8-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b3ff8-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="b3ff8-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b3ff8-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3ff8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3ff8-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3ff8-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b3ff8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b3ff8-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3ff8-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b3ff8-111">Attributes</span></span>  
  
|<span data-ttu-id="b3ff8-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="b3ff8-112">Attribute</span></span>|<span data-ttu-id="b3ff8-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b3ff8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3ff8-114">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="b3ff8-114">discoveryVersion</span></span>|<span data-ttu-id="b3ff8-115">Řetězec, který určuje jeden ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="b3ff8-116">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="b3ff8-117">Tato hodnota je typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="b3ff8-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="b3ff8-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="b3ff8-119">Časový interval hodnotu, která určuje maximální hodnotu zpoždění protokolu zjišťování bude čekat před odesláním uvítací zprávu.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="b3ff8-120">Náhodný čas hodnotu mezi 0 a hodnota tohoto atributu bude čekat zprávy před odesláním.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="b3ff8-121">Tento atribut slouží k nastavení malé náhodné zpoždění zabránil výstrahami sítě v případě, že se odesílá do sítě a všechny služby jsou zase online ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="b3ff8-122">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="b3ff8-122">multicastAddress</span></span>|<span data-ttu-id="b3ff8-123">Identifikátor URI určující adresu vícesměrového vysílání pro odesílání a přijímání zpráv zjišťování.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-123">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="b3ff8-124">Výchozí hodnota je jako vyhovující specifikace protokolu adresu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-124">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="b3ff8-125">name</span><span class="sxs-lookup"><span data-stu-id="b3ff8-125">name</span></span>|<span data-ttu-id="b3ff8-126">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-126">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="b3ff8-127">Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-127">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3ff8-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b3ff8-128">Child Elements</span></span>  
  
|<span data-ttu-id="b3ff8-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="b3ff8-129">Element</span></span>|<span data-ttu-id="b3ff8-130">Popis</span><span class="sxs-lookup"><span data-stu-id="b3ff8-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3ff8-131">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="b3ff8-131">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="b3ff8-132">Kolekce nastavení, která vám umožní nakonfigurovat přenos UDP pro koncový bod protokolu UDP.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-132">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b3ff8-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b3ff8-133">Parent Elements</span></span>  
  
|<span data-ttu-id="b3ff8-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="b3ff8-134">Element</span></span>|<span data-ttu-id="b3ff8-135">Popis</span><span class="sxs-lookup"><span data-stu-id="b3ff8-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3ff8-136">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b3ff8-136">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="b3ff8-137">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-137">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b3ff8-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3ff8-138">Example</span></span>  
 <span data-ttu-id="b3ff8-139">Následující příklad ukazuje přes UDP naslouchání pro oznámení klienta vícesměrového vysílání přenos s výchozí adresy vícesměrového vysílání, UDP a vícesměrového vysílání přenosu pomocí zadané adresy vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="b3ff8-139">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3ff8-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3ff8-140">See also</span></span>
- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
