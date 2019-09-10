---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 8dabf8845126705d082d080b643688ed62883f39
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854915"
---
# <a name="udpannouncementendpoint"></a><span data-ttu-id="f4a37-101">\<udpAnnouncementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="f4a37-101">\<udpAnnouncementEndpoint></span></span>
<span data-ttu-id="f4a37-102">Tento prvek konfigurace definuje standardní koncový bod, který používají služby k posílání zpráv oznámení přes vazbu UDP.</span><span class="sxs-lookup"><span data-stu-id="f4a37-102">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="f4a37-103">Má pevnou smlouvu a podporuje dvě verze zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f4a37-103">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="f4a37-104">Navíc má pevnou vazbu UDP a výchozí hodnotu adresy uvedené ve specifikacích WS-Discovery (WS-Discovery duben 2005 nebo WS-Discovery verze 1,1).</span><span class="sxs-lookup"><span data-stu-id="f4a37-104">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="f4a37-105">Můžete zadat adresu vícesměrového vysílání, která se má použít pro odesílání a příjem zpráv s oznámením.</span><span class="sxs-lookup"><span data-stu-id="f4a37-105">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="f4a37-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f4a37-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f4a37-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f4a37-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f4a37-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="f4a37-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="f4a37-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpAnnouncementEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="f4a37-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpAnnouncementEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4a37-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4a37-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4a37-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f4a37-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f4a37-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f4a37-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4a37-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="f4a37-113">Attributes</span></span>  
  
|<span data-ttu-id="f4a37-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="f4a37-114">Attribute</span></span>|<span data-ttu-id="f4a37-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f4a37-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f4a37-116">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="f4a37-116">discoveryVersion</span></span>|<span data-ttu-id="f4a37-117">Řetězec, který určuje jednu ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="f4a37-117">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="f4a37-118">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="f4a37-118">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="f4a37-119">Tato hodnota je typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="f4a37-119">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="f4a37-120">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="f4a37-120">maxAnnouncementDelay</span></span>|<span data-ttu-id="f4a37-121">Hodnota TimeSpan, která určuje maximální hodnotu pro prodlevu, po kterou bude protokol zjišťování čekat před odesláním zprávy Hello.</span><span class="sxs-lookup"><span data-stu-id="f4a37-121">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="f4a37-122">Zprávy budou čekat na hodnotu náhodného času mezi 0 a hodnotou tohoto atributu před odesláním.</span><span class="sxs-lookup"><span data-stu-id="f4a37-122">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="f4a37-123">Tento atribut slouží k nastavení malé náhodné prodlevy, aby se zabránilo výpadkům sítě v případě, že dojde k vygenerování sítě, a všechny služby se vrátí zpět do režimu online ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="f4a37-123">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="f4a37-124">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="f4a37-124">multicastAddress</span></span>|<span data-ttu-id="f4a37-125">Identifikátor URI, který určuje adresu vícesměrového vysílání, která se má použít pro odesílání a příjem zpráv zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f4a37-125">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="f4a37-126">Výchozí hodnota je adresa vícesměrového vysílání, která odpovídá specifikaci protokolu.</span><span class="sxs-lookup"><span data-stu-id="f4a37-126">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="f4a37-127">name</span><span class="sxs-lookup"><span data-stu-id="f4a37-127">name</span></span>|<span data-ttu-id="f4a37-128">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f4a37-128">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="f4a37-129">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="f4a37-129">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4a37-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f4a37-130">Child Elements</span></span>  
  
|<span data-ttu-id="f4a37-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="f4a37-131">Element</span></span>|<span data-ttu-id="f4a37-132">Popis</span><span class="sxs-lookup"><span data-stu-id="f4a37-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4a37-133">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="f4a37-133">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="f4a37-134">Kolekce nastavení, která umožňují nakonfigurovat přenos UDP pro koncový bod UDP.</span><span class="sxs-lookup"><span data-stu-id="f4a37-134">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4a37-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f4a37-135">Parent Elements</span></span>  
  
|<span data-ttu-id="f4a37-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="f4a37-136">Element</span></span>|<span data-ttu-id="f4a37-137">Popis</span><span class="sxs-lookup"><span data-stu-id="f4a37-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4a37-138">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="f4a37-138">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="f4a37-139">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="f4a37-139">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f4a37-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4a37-140">Example</span></span>  
 <span data-ttu-id="f4a37-141">Následující příklad ukazuje, že klient naslouchá oznámení prostřednictvím přenosu vícesměrového vysílání UDP s výchozí adresou vícesměrového vysílání a přenos vícesměrového vysílání UDP se zadanou adresou vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="f4a37-141">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4a37-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4a37-142">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
