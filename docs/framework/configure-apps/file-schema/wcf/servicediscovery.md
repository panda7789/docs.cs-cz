---
title: '&lt;serviceDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 2b3061274ef670ccd672c3155ca7285d567834bd
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146898"
---
# <a name="ltservicediscoverygt"></a><span data-ttu-id="3d78c-102">&lt;serviceDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="3d78c-102">&lt;serviceDiscovery&gt;</span></span>
<span data-ttu-id="3d78c-103">Určuje zjistitelnost koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="3d78c-103">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="3d78c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3d78c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3d78c-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3d78c-105">\<behaviors></span></span>  
<span data-ttu-id="3d78c-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3d78c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="3d78c-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3d78c-107">\<behavior></span></span>  
<span data-ttu-id="3d78c-108">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="3d78c-108">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d78c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d78c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d78c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3d78c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3d78c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3d78c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d78c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3d78c-112">Attributes</span></span>  
 <span data-ttu-id="3d78c-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="3d78c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3d78c-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3d78c-114">Child Elements</span></span>  
  
|<span data-ttu-id="3d78c-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="3d78c-115">Element</span></span>|<span data-ttu-id="3d78c-116">Popis</span><span class="sxs-lookup"><span data-stu-id="3d78c-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d78c-117">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="3d78c-117">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="3d78c-118">Kolekce koncových bodů oznámení.</span><span class="sxs-lookup"><span data-stu-id="3d78c-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="3d78c-119">V této části můžete určovat koncové body pro odesílání zprávy oznámení.</span><span class="sxs-lookup"><span data-stu-id="3d78c-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="3d78c-120">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="3d78c-120">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="3d78c-121">Kolekce zjišťování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="3d78c-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="3d78c-122">V této části můžete určovat koncové body, na kterém chcete přijímat zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="3d78c-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d78c-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3d78c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3d78c-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3d78c-124">Element</span></span>|<span data-ttu-id="3d78c-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3d78c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d78c-126">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3d78c-126">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="3d78c-127">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="3d78c-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d78c-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d78c-128">Remarks</span></span>  
 <span data-ttu-id="3d78c-129">Když se přidá do služby konfiguraci chování, tento prvek konfigurace je všechny koncové body služby zjistitelné.</span><span class="sxs-lookup"><span data-stu-id="3d78c-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="3d78c-130">Funkce zjišťování těchto koncových bodů lze dále konfigurovat pomocí [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) nebo [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="3d78c-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="3d78c-131">Použít [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) části a nakonfigurovat oznámení tak, že zadáte konfigurace koncového bodu, které se má používat k odesílání oznámení o službách (/ Hello je online a offline/Bye).</span><span class="sxs-lookup"><span data-stu-id="3d78c-131">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="3d78c-132">Použití [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) část ruční zadání koncového bodu, na kterém chcete přijímat zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="3d78c-132">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d78c-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d78c-133">Example</span></span>  
 <span data-ttu-id="3d78c-134">Následující příklad konfigurace určuje, že CalculatorService zjistitelné a volitelně Určuje koncový bod oznámení pro použití.</span><span class="sxs-lookup"><span data-stu-id="3d78c-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d78c-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d78c-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
