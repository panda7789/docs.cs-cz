---
title: '&lt;serviceDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 78f1c7be1d8285cd2fdf79af1e1220a7e48b2893
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicediscoverygt"></a><span data-ttu-id="e9613-102">&lt;serviceDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="e9613-102">&lt;serviceDiscovery&gt;</span></span>
<span data-ttu-id="e9613-103">Určuje možnosti rozpoznání koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="e9613-103">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="e9613-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e9613-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e9613-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e9613-105">\<behaviors></span></span>  
<span data-ttu-id="e9613-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e9613-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e9613-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e9613-107">\<behavior></span></span>  
<span data-ttu-id="e9613-108">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="e9613-108">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9613-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9613-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9613-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e9613-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e9613-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e9613-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9613-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="e9613-112">Attributes</span></span>  
 <span data-ttu-id="e9613-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="e9613-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9613-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e9613-114">Child Elements</span></span>  
  
|<span data-ttu-id="e9613-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="e9613-115">Element</span></span>|<span data-ttu-id="e9613-116">Popis</span><span class="sxs-lookup"><span data-stu-id="e9613-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9613-117">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="e9613-117">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="e9613-118">Kolekce koncových bodů oznámení.</span><span class="sxs-lookup"><span data-stu-id="e9613-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="e9613-119">Pomocí této části můžete určovat koncové body k použití pro odesílání zpráv oznámení.</span><span class="sxs-lookup"><span data-stu-id="e9613-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="e9613-120">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="e9613-120">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="e9613-121">Kolekce zjišťování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="e9613-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="e9613-122">V této části použijte k určení koncových bodů, na kterém se má naslouchat pro zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="e9613-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9613-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e9613-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e9613-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="e9613-124">Element</span></span>|<span data-ttu-id="e9613-125">Popis</span><span class="sxs-lookup"><span data-stu-id="e9613-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9613-126">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e9613-126">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e9613-127">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="e9613-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9613-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9613-128">Remarks</span></span>  
 <span data-ttu-id="e9613-129">Když se přidá do konfigurace chování služby, tento element konfigurace zajistí koncové body služeb zjistitelný.</span><span class="sxs-lookup"><span data-stu-id="e9613-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="e9613-130">Funkce zjišťování těchto koncových bodů lze dále konfigurovat pomocí [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) nebo [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="e9613-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="e9613-131">Použít [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) část konfigurace hlášení zadáním konfigurace koncového bodu, která se má použít k odeslání oznámení týkající se služeb (nebo Hello je online a offline nebo Bye).</span><span class="sxs-lookup"><span data-stu-id="e9613-131">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="e9613-132">Použití [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) části ručně zadat koncový bod, ke kterému chcete přijímat zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="e9613-132">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9613-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9613-133">Example</span></span>  
 <span data-ttu-id="e9613-134">Následující příklad konfigurace určuje, že CalculatorService zjistitelné a volitelně specifikuje koncového bodu oznámení má být použit.</span><span class="sxs-lookup"><span data-stu-id="e9613-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e9613-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9613-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
