---
title: '&lt;serviceDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 73943f5f962a6963809e2c65ce8593f6181559f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587330"
---
# <a name="ltservicediscoverygt"></a><span data-ttu-id="9ad88-102">&lt;serviceDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="9ad88-102">&lt;serviceDiscovery&gt;</span></span>
<span data-ttu-id="9ad88-103">Určuje zjistitelnost koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="9ad88-103">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="9ad88-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9ad88-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9ad88-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9ad88-105">\<behaviors></span></span>  
<span data-ttu-id="9ad88-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9ad88-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9ad88-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9ad88-107">\<behavior></span></span>  
<span data-ttu-id="9ad88-108">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="9ad88-108">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ad88-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ad88-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ad88-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9ad88-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9ad88-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9ad88-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ad88-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="9ad88-112">Attributes</span></span>  
 <span data-ttu-id="9ad88-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="9ad88-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ad88-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9ad88-114">Child Elements</span></span>  
  
|<span data-ttu-id="9ad88-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="9ad88-115">Element</span></span>|<span data-ttu-id="9ad88-116">Popis</span><span class="sxs-lookup"><span data-stu-id="9ad88-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ad88-117">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="9ad88-117">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="9ad88-118">Kolekce koncových bodů oznámení.</span><span class="sxs-lookup"><span data-stu-id="9ad88-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="9ad88-119">V této části můžete určovat koncové body pro odesílání zprávy oznámení.</span><span class="sxs-lookup"><span data-stu-id="9ad88-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="9ad88-120">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="9ad88-120">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="9ad88-121">Kolekce zjišťování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="9ad88-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="9ad88-122">V této části můžete určovat koncové body, na kterém chcete přijímat zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="9ad88-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ad88-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9ad88-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9ad88-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="9ad88-124">Element</span></span>|<span data-ttu-id="9ad88-125">Popis</span><span class="sxs-lookup"><span data-stu-id="9ad88-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ad88-126">\<behavior></span><span class="sxs-lookup"><span data-stu-id="9ad88-126">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="9ad88-127">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="9ad88-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ad88-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ad88-128">Remarks</span></span>  
 <span data-ttu-id="9ad88-129">Když se přidá do služby konfiguraci chování, tento prvek konfigurace je všechny koncové body služby zjistitelné.</span><span class="sxs-lookup"><span data-stu-id="9ad88-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="9ad88-130">Funkce zjišťování těchto koncových bodů lze dále konfigurovat pomocí [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) nebo [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="9ad88-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="9ad88-131">Použít [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) části a nakonfigurovat oznámení tak, že zadáte konfigurace koncového bodu, které se má používat k odesílání oznámení o službách (/ Hello je online a offline/Bye).</span><span class="sxs-lookup"><span data-stu-id="9ad88-131">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="9ad88-132">Použití [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) část ruční zadání koncového bodu, na kterém chcete přijímat zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="9ad88-132">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ad88-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ad88-133">Example</span></span>  
 <span data-ttu-id="9ad88-134">Následující příklad konfigurace určuje, že CalculatorService zjistitelné a volitelně Určuje koncový bod oznámení pro použití.</span><span class="sxs-lookup"><span data-stu-id="9ad88-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ad88-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ad88-135">See also</span></span>
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
