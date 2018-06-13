---
title: '&lt;AnnouncementEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: 15d60cd277b77fd52b2b77bfcdf4d0da1de7167a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351823"
---
# <a name="ltannouncementendpointgt"></a><span data-ttu-id="0c402-102">&lt;AnnouncementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="0c402-102">&lt;announcementEndpoint&gt;</span></span>
<span data-ttu-id="0c402-103">Tento element konfigurace definuje standardní koncový bod s pevnou oznámení kontrakt.</span><span class="sxs-lookup"><span data-stu-id="0c402-103">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="0c402-104">Služba může volitelně informovat jeho dostupnost zaslat e online a offline oznámení, pokud je otevřen nebo uzavřený v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0c402-104">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="0c402-105">Služba Windows Communication Foundation (WCF) určuje koncových bodů oznámení v [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elementu a používá AnnouncementClient k provedení hlášení.</span><span class="sxs-lookup"><span data-stu-id="0c402-105">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="0c402-106">Klient chtějí naslouchat oznámení z jiné služby skutečně funguje jako služby WCF; Proto je nutné konfigurovat koncových bodů oznámení pro daného klienta v [ \<služby >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) části.</span><span class="sxs-lookup"><span data-stu-id="0c402-106">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="0c402-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0c402-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="0c402-108">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0c402-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c402-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c402-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c402-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0c402-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0c402-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0c402-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c402-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0c402-112">Attributes</span></span>  
  
|<span data-ttu-id="0c402-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="0c402-113">Attribute</span></span>|<span data-ttu-id="0c402-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0c402-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c402-115">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="0c402-115">discoveryVersion</span></span>|<span data-ttu-id="0c402-116">Řetězec, který určuje jeden z dvě verze protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="0c402-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="0c402-117">Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="0c402-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="0c402-118">Tato hodnota je typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="0c402-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="0c402-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="0c402-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="0c402-120">Hodnota časového rozpětí, která určuje maximální hodnotu zpoždění protokol zjišťování bude čekat před odesláním zprávy Hello.</span><span class="sxs-lookup"><span data-stu-id="0c402-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="0c402-121">Před odesláním zprávy vyčká na hodnotu náhodný čas mezi 0 a hodnota tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="0c402-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="0c402-122">Tento atribut slouží k nastavení malé, náhodné zpoždění, aby se zabránilo zahlcení sítě, když síť prochází a všechny služby dostane zpět online ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="0c402-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="0c402-123">name</span><span class="sxs-lookup"><span data-stu-id="0c402-123">name</span></span>|<span data-ttu-id="0c402-124">Řetězec, který určuje název konfigurace standardní koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="0c402-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="0c402-125">Název je používán `endpointConfiguration` atribut propojení koncový bod standardní konfiguraci koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="0c402-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c402-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0c402-126">Child Elements</span></span>  
 <span data-ttu-id="0c402-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="0c402-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c402-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0c402-128">Parent Elements</span></span>  
  
|<span data-ttu-id="0c402-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="0c402-129">Element</span></span>|<span data-ttu-id="0c402-130">Popis</span><span class="sxs-lookup"><span data-stu-id="0c402-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c402-131">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0c402-131">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="0c402-132">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="0c402-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0c402-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c402-133">Example</span></span>  
 <span data-ttu-id="0c402-134">Následující příklad ukazuje klienta prostřednictvím protokolu http a peernet naslouchání pro zprávy oznámení.</span><span class="sxs-lookup"><span data-stu-id="0c402-134">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c402-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c402-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
