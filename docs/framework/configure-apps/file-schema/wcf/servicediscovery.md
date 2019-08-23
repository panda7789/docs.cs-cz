---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: a99edd3a62a40c2efbc63a166b8c0b0d124e8a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936277"
---
# <a name="servicediscovery"></a><span data-ttu-id="99c38-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="99c38-101">\<serviceDiscovery></span></span>
<span data-ttu-id="99c38-102">Určuje zjistitelnost koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="99c38-102">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="99c38-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="99c38-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="99c38-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="99c38-104">\<behaviors></span></span>  
<span data-ttu-id="99c38-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="99c38-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="99c38-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="99c38-106">\<behavior></span></span>  
<span data-ttu-id="99c38-107">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="99c38-107">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c38-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99c38-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99c38-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="99c38-109">Attributes and Elements</span></span>  
 <span data-ttu-id="99c38-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="99c38-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99c38-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="99c38-111">Attributes</span></span>  
 <span data-ttu-id="99c38-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="99c38-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99c38-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="99c38-113">Child Elements</span></span>  
  
|<span data-ttu-id="99c38-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="99c38-114">Element</span></span>|<span data-ttu-id="99c38-115">Popis</span><span class="sxs-lookup"><span data-stu-id="99c38-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99c38-116">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="99c38-116">\<announcementEndpoint></span></span>](announcementendpoint.md)|<span data-ttu-id="99c38-117">Kolekce koncových bodů oznámení</span><span class="sxs-lookup"><span data-stu-id="99c38-117">A collection of announcement endpoints.</span></span> <span data-ttu-id="99c38-118">V této části můžete zadat koncové body, které se mají použít pro posílání zpráv s oznámením.</span><span class="sxs-lookup"><span data-stu-id="99c38-118">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="99c38-119">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="99c38-119">\<discoveryEndpoint></span></span>](discoveryendpoint.md)|<span data-ttu-id="99c38-120">Kolekce koncových bodů zjišťování.</span><span class="sxs-lookup"><span data-stu-id="99c38-120">A collection of discovery endpoints.</span></span> <span data-ttu-id="99c38-121">V této části můžete zadat koncové body, na kterých se mají zprávy zjišťování naslouchat.</span><span class="sxs-lookup"><span data-stu-id="99c38-121">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99c38-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="99c38-122">Parent Elements</span></span>  
  
|<span data-ttu-id="99c38-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="99c38-123">Element</span></span>|<span data-ttu-id="99c38-124">Popis</span><span class="sxs-lookup"><span data-stu-id="99c38-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99c38-125">\<> chování</span><span class="sxs-lookup"><span data-stu-id="99c38-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="99c38-126">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="99c38-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99c38-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99c38-127">Remarks</span></span>  
 <span data-ttu-id="99c38-128">Po přidání do konfigurace chování služby tento prvek konfigurace zpřístupňuje všechny koncové body této služby.</span><span class="sxs-lookup"><span data-stu-id="99c38-128">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="99c38-129">Funkce zjišťování těchto koncových bodů můžete dále konfigurovat pomocí [ \<](discoveryendpoint.md) podřízených elementů DiscoveryEndpoint > nebo [ \<announcementEndpoint >](announcementendpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="99c38-129">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="99c38-130">Pomocí části [> announcementEndpointmůžetenakonfigurovatoznámenízadánímkonfiguracekoncovéhobodu,kterásemápoužítkodesíláníoznámeníslužby(online/Helloaoffline/bye).\<](announcementendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="99c38-130">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="99c38-131">Pomocí části [> DiscoveryEndpointmůžeteručnězadatkoncovýbod,nakterémsemajízprávyzjišťovánínaslouchat.\<](discoveryendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="99c38-131">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99c38-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="99c38-132">Example</span></span>  
 <span data-ttu-id="99c38-133">Následující příklad konfigurace určuje, že CalculatorService bude zjistitelný a volitelně Určuje koncový bod oznámení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="99c38-133">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99c38-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99c38-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
