---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399659"
---
# \<serviceDiscovery>
<span data-ttu-id="8e63a-101">Určuje zjistitelnost koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="8e63a-101">Specifies the discoverability of service endpoints.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="8e63a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e63a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e63a-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8e63a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="8e63a-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8e63a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e63a-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="8e63a-105">Attributes</span></span>  
 <span data-ttu-id="8e63a-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="8e63a-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8e63a-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8e63a-107">Child Elements</span></span>  
  
|<span data-ttu-id="8e63a-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="8e63a-108">Element</span></span>|<span data-ttu-id="8e63a-109">Description</span><span class="sxs-lookup"><span data-stu-id="8e63a-109">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="8e63a-110">Kolekce koncových bodů oznámení</span><span class="sxs-lookup"><span data-stu-id="8e63a-110">A collection of announcement endpoints.</span></span> <span data-ttu-id="8e63a-111">V této části můžete zadat koncové body, které se mají použít pro posílání zpráv s oznámením.</span><span class="sxs-lookup"><span data-stu-id="8e63a-111">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="8e63a-112">Kolekce koncových bodů zjišťování.</span><span class="sxs-lookup"><span data-stu-id="8e63a-112">A collection of discovery endpoints.</span></span> <span data-ttu-id="8e63a-113">V této části můžete zadat koncové body, na kterých se mají zprávy zjišťování naslouchat.</span><span class="sxs-lookup"><span data-stu-id="8e63a-113">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e63a-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8e63a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8e63a-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="8e63a-115">Element</span></span>|<span data-ttu-id="8e63a-116">Description</span><span class="sxs-lookup"><span data-stu-id="8e63a-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8e63a-117">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="8e63a-117">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e63a-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e63a-118">Remarks</span></span>  
 <span data-ttu-id="8e63a-119">Po přidání do konfigurace chování služby tento prvek konfigurace zpřístupňuje všechny koncové body této služby.</span><span class="sxs-lookup"><span data-stu-id="8e63a-119">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="8e63a-120">Funkce zjišťování těchto koncových bodů můžete dále konfigurovat pomocí [\<discoveryEndpoint>](discoveryendpoint.md) [\<announcementEndpoint>](announcementendpoint.md) podřízených elementů nebo.</span><span class="sxs-lookup"><span data-stu-id="8e63a-120">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="8e63a-121">Pomocí [\<announcementEndpoint>](announcementendpoint.md) části můžete nakonfigurovat oznámení zadáním konfigurace koncového bodu, která se bude používat k odesílání oznámení služby (online/Hello a offline/bye).</span><span class="sxs-lookup"><span data-stu-id="8e63a-121">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="8e63a-122">Pomocí [\<discoveryEndpoint>](discoveryendpoint.md) oddílu můžete ručně zadat koncový bod, na kterém se mají zprávy zjišťování naslouchat.</span><span class="sxs-lookup"><span data-stu-id="8e63a-122">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e63a-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e63a-123">Example</span></span>  
 <span data-ttu-id="8e63a-124">Následující příklad konfigurace určuje, že CalculatorService bude zjistitelný a volitelně Určuje koncový bod oznámení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="8e63a-124">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e63a-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e63a-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
