---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 8dabf8845126705d082d080b643688ed62883f39
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854915"
---
# \<udpAnnouncementEndpoint>
<span data-ttu-id="d888a-101">Tento prvek konfigurace definuje standardní koncový bod, který používají služby k posílání zpráv oznámení přes vazbu UDP.</span><span class="sxs-lookup"><span data-stu-id="d888a-101">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="d888a-102">Má pevnou smlouvu a podporuje dvě verze zjišťování.</span><span class="sxs-lookup"><span data-stu-id="d888a-102">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="d888a-103">Navíc má pevnou vazbu UDP a výchozí hodnotu adresy uvedené ve specifikacích WS-Discovery (WS-Discovery duben 2005 nebo WS-Discovery verze 1,1).</span><span class="sxs-lookup"><span data-stu-id="d888a-103">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="d888a-104">Můžete zadat adresu vícesměrového vysílání, která se má použít pro odesílání a příjem zpráv s oznámením.</span><span class="sxs-lookup"><span data-stu-id="d888a-104">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpAnnouncementEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="d888a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d888a-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d888a-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d888a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d888a-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d888a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d888a-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="d888a-108">Attributes</span></span>  
  
|<span data-ttu-id="d888a-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="d888a-109">Attribute</span></span>|<span data-ttu-id="d888a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d888a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d888a-111">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="d888a-111">discoveryVersion</span></span>|<span data-ttu-id="d888a-112">Řetězec, který určuje jednu ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="d888a-112">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="d888a-113">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="d888a-113">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="d888a-114">Tato hodnota je typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="d888a-114">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="d888a-115">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="d888a-115">maxAnnouncementDelay</span></span>|<span data-ttu-id="d888a-116">Hodnota TimeSpan, která určuje maximální hodnotu pro prodlevu, po kterou bude protokol zjišťování čekat před odesláním zprávy Hello.</span><span class="sxs-lookup"><span data-stu-id="d888a-116">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="d888a-117">Zprávy budou čekat na hodnotu náhodného času mezi 0 a hodnotou tohoto atributu před odesláním.</span><span class="sxs-lookup"><span data-stu-id="d888a-117">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="d888a-118">Tento atribut slouží k nastavení malé náhodné prodlevy, aby se zabránilo výpadkům sítě v případě, že dojde k vygenerování sítě, a všechny služby se vrátí zpět do režimu online ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="d888a-118">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="d888a-119">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="d888a-119">multicastAddress</span></span>|<span data-ttu-id="d888a-120">Identifikátor URI, který určuje adresu vícesměrového vysílání, která se má použít pro odesílání a příjem zpráv zjišťování.</span><span class="sxs-lookup"><span data-stu-id="d888a-120">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="d888a-121">Výchozí hodnota je adresa vícesměrového vysílání, která odpovídá specifikaci protokolu.</span><span class="sxs-lookup"><span data-stu-id="d888a-121">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="d888a-122">name</span><span class="sxs-lookup"><span data-stu-id="d888a-122">name</span></span>|<span data-ttu-id="d888a-123">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d888a-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="d888a-124">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="d888a-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d888a-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d888a-125">Child Elements</span></span>  
  
|<span data-ttu-id="d888a-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="d888a-126">Element</span></span>|<span data-ttu-id="d888a-127">Description</span><span class="sxs-lookup"><span data-stu-id="d888a-127">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="d888a-128">Kolekce nastavení, která umožňují nakonfigurovat přenos UDP pro koncový bod UDP.</span><span class="sxs-lookup"><span data-stu-id="d888a-128">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d888a-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d888a-129">Parent Elements</span></span>  
  
|<span data-ttu-id="d888a-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="d888a-130">Element</span></span>|<span data-ttu-id="d888a-131">Description</span><span class="sxs-lookup"><span data-stu-id="d888a-131">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="d888a-132">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="d888a-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d888a-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="d888a-133">Example</span></span>  
 <span data-ttu-id="d888a-134">Následující příklad ukazuje, že klient naslouchá oznámení prostřednictvím přenosu vícesměrového vysílání UDP s výchozí adresou vícesměrového vysílání a přenos vícesměrového vysílání UDP se zadanou adresou vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="d888a-134">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d888a-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="d888a-135">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
