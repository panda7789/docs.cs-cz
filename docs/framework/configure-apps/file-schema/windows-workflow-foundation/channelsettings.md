---
title: <channelSettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 94a4457f-f43f-458d-a47e-2d11103ee75e
ms.openlocfilehash: f6a57e2cc1e7c5e114fd38ee3534ab7c4e629b36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152271"
---
# <a name="channelsettings"></a><span data-ttu-id="b3594-101">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="b3594-101">\<channelSettings></span></span>
<span data-ttu-id="b3594-102">Určuje nastavení mezipaměti kanálu.</span><span class="sxs-lookup"><span data-stu-id="b3594-102">Specifies the settings of the channel cache.</span></span>  
  
<span data-ttu-id="b3594-103">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b3594-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b3594-104">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b3594-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="b3594-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b3594-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b3594-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b3594-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b3594-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b3594-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b3594-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sendMessageChannelCache>**](sendmessagechannelcache.md)</span><span class="sxs-lookup"><span data-stu-id="b3594-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sendMessageChannelCache>**](sendmessagechannelcache.md)</span></span>\
<span data-ttu-id="b3594-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelNastavení>**</span><span class="sxs-lookup"><span data-stu-id="b3594-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3594-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3594-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3594-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b3594-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b3594-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b3594-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3594-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="b3594-113">Attributes</span></span>  
  
|<span data-ttu-id="b3594-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="b3594-114">Attribute</span></span>|<span data-ttu-id="b3594-115">Popis</span><span class="sxs-lookup"><span data-stu-id="b3594-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3594-116">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="b3594-116">idleTimeout</span></span>|<span data-ttu-id="b3594-117">Časový interval hodnotu, která určuje maximální interval času, pro který objekt může zůstat nečinná v mezipaměti před vyřazení.</span><span class="sxs-lookup"><span data-stu-id="b3594-117">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="b3594-118">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="b3594-118">leaseTimeout</span></span>|<span data-ttu-id="b3594-119">Hodnota TimeSpan, která určuje časový interval, po kterém je objekt odebrán z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b3594-119">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="b3594-120">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="b3594-120">maxItemsInCache</span></span>|<span data-ttu-id="b3594-121">Celé číslo, která určuje maximální počet objektů, které lze uložit do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b3594-121">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3594-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b3594-122">Child Elements</span></span>  
 <span data-ttu-id="b3594-123">Žádné.</span><span class="sxs-lookup"><span data-stu-id="b3594-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3594-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b3594-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b3594-125">Element</span><span class="sxs-lookup"><span data-stu-id="b3594-125">Element</span></span>|<span data-ttu-id="b3594-126">Popis</span><span class="sxs-lookup"><span data-stu-id="b3594-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3594-127">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="b3594-127">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="b3594-128">Chování služby, které umožňuje přizpůsobení úrovní sdílení mezipaměti, nastavení mezipaměti kanálu ve výrobě a nastavení mezipaměti kanálu pro pracovní postupy, které odesílají zprávy koncovým bodům služby pomocí aktivit odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="b3594-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3594-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3594-129">Remarks</span></span>  
 <span data-ttu-id="b3594-130">Toto chování služby je určen pro pracovní postupy, které odesílání zpráv do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="b3594-130">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="b3594-131">Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b3594-131">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="b3594-132">Ve výchozím nastavení v pracovním postupu hostované <xref:System.ServiceModel.WorkflowServiceHost>, je mezipaměť používaná aplikací <xref:System.ServiceModel.Activities.Send> zasílání zpráv aktivity je sdílen na všechny instance pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost> (hostitele úroveň ukládání do mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="b3594-132">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="b3594-133">Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance).</span><span class="sxs-lookup"><span data-stu-id="b3594-133">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="b3594-134">Ve výchozím nastavení pro všechny aktivity odeslání do svého pracovního postupu, který má koncové body definované v konfiguraci je zakázáno ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b3594-134">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="b3594-135">Další informace o tom, jak změnit výchozí úrovně sdílení mezipaměti a nastavení mezipaměti pro uprostředkované kanály a mezipaměti kanálů, naleznete [v tématu Změna úrovní sdílení mezipaměti pro odesílání aktivit](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="b3594-135">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3594-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3594-136">Example</span></span>  
 <span data-ttu-id="b3594-137">V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b3594-137">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="b3594-138">Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby.</span><span class="sxs-lookup"><span data-stu-id="b3594-138">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="b3594-139">Následující příklad ukazuje obsah konfiguračního `MyChannelCacheBehavior` souboru, který obsahuje chování služby s vlastním nastavením mezipaměti výroby a mezipaměti kanálů.</span><span class="sxs-lookup"><span data-stu-id="b3594-139">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="b3594-140">Toto chování služby je `behaviorConfiguration` přidán do služby prostřednictvím atributu.</span><span class="sxs-lookup"><span data-stu-id="b3594-140">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>  
    <!-- List of other config sections here -->
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3594-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3594-141">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="b3594-142">Změna úrovní sdílení mezipaměti pro aktivity odesílání</span><span class="sxs-lookup"><span data-stu-id="b3594-142">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
