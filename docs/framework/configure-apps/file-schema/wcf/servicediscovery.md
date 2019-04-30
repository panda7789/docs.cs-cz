---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 54a9833f56927568af711a103bd3831b767711e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788411"
---
# <a name="servicediscovery"></a><span data-ttu-id="285a2-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="285a2-101">\<serviceDiscovery></span></span>
<span data-ttu-id="285a2-102">Určuje zjistitelnost koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="285a2-102">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="285a2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="285a2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="285a2-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="285a2-104">\<behaviors></span></span>  
<span data-ttu-id="285a2-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="285a2-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="285a2-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="285a2-106">\<behavior></span></span>  
<span data-ttu-id="285a2-107">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="285a2-107">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="285a2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="285a2-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="285a2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="285a2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="285a2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="285a2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="285a2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="285a2-111">Attributes</span></span>  
 <span data-ttu-id="285a2-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="285a2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="285a2-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="285a2-113">Child Elements</span></span>  
  
|<span data-ttu-id="285a2-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="285a2-114">Element</span></span>|<span data-ttu-id="285a2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="285a2-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="285a2-116">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="285a2-116">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="285a2-117">Kolekce koncových bodů oznámení.</span><span class="sxs-lookup"><span data-stu-id="285a2-117">A collection of announcement endpoints.</span></span> <span data-ttu-id="285a2-118">V této části můžete určovat koncové body pro odesílání zprávy oznámení.</span><span class="sxs-lookup"><span data-stu-id="285a2-118">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="285a2-119">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="285a2-119">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="285a2-120">Kolekce zjišťování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="285a2-120">A collection of discovery endpoints.</span></span> <span data-ttu-id="285a2-121">V této části můžete určovat koncové body, na kterém chcete přijímat zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="285a2-121">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="285a2-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="285a2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="285a2-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="285a2-123">Element</span></span>|<span data-ttu-id="285a2-124">Popis</span><span class="sxs-lookup"><span data-stu-id="285a2-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="285a2-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="285a2-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="285a2-126">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="285a2-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="285a2-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="285a2-127">Remarks</span></span>  
 <span data-ttu-id="285a2-128">Když se přidá do služby konfiguraci chování, tento prvek konfigurace je všechny koncové body služby zjistitelné.</span><span class="sxs-lookup"><span data-stu-id="285a2-128">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="285a2-129">Funkce zjišťování těchto koncových bodů lze dále konfigurovat pomocí [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) nebo [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="285a2-129">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="285a2-130">Použít [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) části a nakonfigurovat oznámení tak, že zadáte konfigurace koncového bodu, které se má používat k odesílání oznámení o službách (/ Hello je online a offline/Bye).</span><span class="sxs-lookup"><span data-stu-id="285a2-130">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="285a2-131">Použití [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) část ruční zadání koncového bodu, na kterém chcete přijímat zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="285a2-131">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="285a2-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="285a2-132">Example</span></span>  
 <span data-ttu-id="285a2-133">Následující příklad konfigurace určuje, že CalculatorService zjistitelné a volitelně Určuje koncový bod oznámení pro použití.</span><span class="sxs-lookup"><span data-stu-id="285a2-133">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="285a2-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="285a2-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
