---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: aa4cd8f4d7dcfa438ede71c394f1d0b0ac6faa50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926554"
---
# <a name="announcementendpoint"></a><span data-ttu-id="11bb2-101">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="11bb2-101">\<announcementEndpoint></span></span>
<span data-ttu-id="11bb2-102">Tento prvek konfigurace definuje standardní koncový bod s pevným kontraktem oznámení.</span><span class="sxs-lookup"><span data-stu-id="11bb2-102">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="11bb2-103">Služba může volitelně oznámit svou dostupnost odesláním online nebo offline zprávy s oznámením, když je otevřený nebo uzavřený v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="11bb2-103">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="11bb2-104">Služba Windows Communication Foundation (WCF) určuje koncové body oznámení v [ \<prvku > serviceDiscovery](servicediscovery.md) a k provádění oznámení používá AnnouncementClient.</span><span class="sxs-lookup"><span data-stu-id="11bb2-104">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="11bb2-105">Klient, který chce naslouchat oznámením z jiné služby, ve skutečnosti funguje jako služba WCF; Proto je nutné nakonfigurovat koncové body oznámení pro tohoto klienta v [ \<části služby >](services.md) .</span><span class="sxs-lookup"><span data-stu-id="11bb2-105">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>  
  
<span data-ttu-id="11bb2-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="11bb2-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="11bb2-107">\<Oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="11bb2-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11bb2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11bb2-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11bb2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11bb2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="11bb2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11bb2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11bb2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="11bb2-111">Attributes</span></span>  
  
|<span data-ttu-id="11bb2-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="11bb2-112">Attribute</span></span>|<span data-ttu-id="11bb2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="11bb2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11bb2-114">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="11bb2-114">discoveryVersion</span></span>|<span data-ttu-id="11bb2-115">Řetězec, který určuje jednu ze dvou verzí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="11bb2-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="11bb2-116">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="11bb2-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="11bb2-117">Tato hodnota je typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="11bb2-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="11bb2-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="11bb2-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="11bb2-119">Hodnota TimeSpan, která určuje maximální hodnotu pro prodlevu, po kterou bude protokol zjišťování čekat před odesláním zprávy Hello.</span><span class="sxs-lookup"><span data-stu-id="11bb2-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="11bb2-120">Zprávy budou čekat na hodnotu náhodného času mezi 0 a hodnotou tohoto atributu před odesláním.</span><span class="sxs-lookup"><span data-stu-id="11bb2-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="11bb2-121">Tento atribut slouží k nastavení malé náhodné prodlevy, aby se zabránilo výpadkům sítě v případě, že dojde k vygenerování sítě, a všechny služby se vrátí zpět do režimu online ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="11bb2-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="11bb2-122">name</span><span class="sxs-lookup"><span data-stu-id="11bb2-122">name</span></span>|<span data-ttu-id="11bb2-123">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="11bb2-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="11bb2-124">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="11bb2-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11bb2-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11bb2-125">Child Elements</span></span>  
 <span data-ttu-id="11bb2-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="11bb2-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11bb2-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11bb2-127">Parent Elements</span></span>  
  
|<span data-ttu-id="11bb2-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="11bb2-128">Element</span></span>|<span data-ttu-id="11bb2-129">Popis</span><span class="sxs-lookup"><span data-stu-id="11bb2-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11bb2-130">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="11bb2-130">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="11bb2-131">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="11bb2-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="11bb2-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="11bb2-132">Example</span></span>  
 <span data-ttu-id="11bb2-133">Následující příklad znázorňuje klienta, který přijímá zprávy s oznámeními přes protokol HTTP a PEERNET.</span><span class="sxs-lookup"><span data-stu-id="11bb2-133">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11bb2-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11bb2-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
