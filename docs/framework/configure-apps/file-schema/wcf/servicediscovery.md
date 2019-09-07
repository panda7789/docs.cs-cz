---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399659"
---
# <a name="servicediscovery"></a><span data-ttu-id="96c40-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="96c40-101">\<serviceDiscovery></span></span>
<span data-ttu-id="96c40-102">Určuje zjistitelnost koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="96c40-102">Specifies the discoverability of service endpoints.</span></span>  
  
<span data-ttu-id="96c40-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="96c40-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="96c40-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="96c40-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="96c40-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="96c40-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="96c40-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="96c40-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="96c40-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="96c40-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="96c40-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceDiscovery >**</span><span class="sxs-lookup"><span data-stu-id="96c40-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96c40-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96c40-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96c40-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="96c40-110">Attributes and Elements</span></span>  
 <span data-ttu-id="96c40-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="96c40-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96c40-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="96c40-112">Attributes</span></span>  
 <span data-ttu-id="96c40-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="96c40-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="96c40-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="96c40-114">Child Elements</span></span>  
  
|<span data-ttu-id="96c40-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="96c40-115">Element</span></span>|<span data-ttu-id="96c40-116">Popis</span><span class="sxs-lookup"><span data-stu-id="96c40-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96c40-117">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="96c40-117">\<announcementEndpoint></span></span>](announcementendpoint.md)|<span data-ttu-id="96c40-118">Kolekce koncových bodů oznámení</span><span class="sxs-lookup"><span data-stu-id="96c40-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="96c40-119">V této části můžete zadat koncové body, které se mají použít pro posílání zpráv s oznámením.</span><span class="sxs-lookup"><span data-stu-id="96c40-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="96c40-120">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="96c40-120">\<discoveryEndpoint></span></span>](discoveryendpoint.md)|<span data-ttu-id="96c40-121">Kolekce koncových bodů zjišťování.</span><span class="sxs-lookup"><span data-stu-id="96c40-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="96c40-122">V této části můžete zadat koncové body, na kterých se mají zprávy zjišťování naslouchat.</span><span class="sxs-lookup"><span data-stu-id="96c40-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96c40-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="96c40-123">Parent Elements</span></span>  
  
|<span data-ttu-id="96c40-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="96c40-124">Element</span></span>|<span data-ttu-id="96c40-125">Popis</span><span class="sxs-lookup"><span data-stu-id="96c40-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96c40-126">\<> chování</span><span class="sxs-lookup"><span data-stu-id="96c40-126">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="96c40-127">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="96c40-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96c40-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96c40-128">Remarks</span></span>  
 <span data-ttu-id="96c40-129">Po přidání do konfigurace chování služby tento prvek konfigurace zpřístupňuje všechny koncové body této služby.</span><span class="sxs-lookup"><span data-stu-id="96c40-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="96c40-130">Funkce zjišťování těchto koncových bodů můžete dále konfigurovat pomocí [ \<](discoveryendpoint.md) podřízených elementů DiscoveryEndpoint > nebo [ \<announcementEndpoint >](announcementendpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="96c40-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="96c40-131">Pomocí části [> announcementEndpointmůžetenakonfigurovatoznámenízadánímkonfiguracekoncovéhobodu,kterásemápoužítkodesíláníoznámeníslužby(online/Helloaoffline/bye).\<](announcementendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="96c40-131">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="96c40-132">Pomocí části [> DiscoveryEndpointmůžeteručnězadatkoncovýbod,nakterémsemajízprávyzjišťovánínaslouchat.\<](discoveryendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="96c40-132">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96c40-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="96c40-133">Example</span></span>  
 <span data-ttu-id="96c40-134">Následující příklad konfigurace určuje, že CalculatorService bude zjistitelný a volitelně Určuje koncový bod oznámení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="96c40-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="96c40-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96c40-135">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
