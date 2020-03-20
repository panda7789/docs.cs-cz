---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: b68c6d2e526eb22328806558d7c167b7f2ed0820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151998"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="2634b-101">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="2634b-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="2634b-102">Chování služby, které umožňuje přizpůsobení úrovní sdílení mezipaměti, nastavení mezipaměti kanálu ve výrobě a nastavení mezipaměti kanálu pro pracovní postupy, které odesílají zprávy koncovým bodům služby pomocí aktivit odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="2634b-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="2634b-103">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2634b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2634b-104">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2634b-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="2634b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2634b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="2634b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2634b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="2634b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2634b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="2634b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**</span><span class="sxs-lookup"><span data-stu-id="2634b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2634b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2634b-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
        <factorySettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2634b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2634b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2634b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2634b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2634b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2634b-112">Attributes</span></span>  
  
|<span data-ttu-id="2634b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="2634b-113">Attribute</span></span>|<span data-ttu-id="2634b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2634b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2634b-115">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="2634b-115">allowUnsafeCaching</span></span>|<span data-ttu-id="2634b-116">Logická hodnota určující, zda chcete zapnout ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="2634b-116">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="2634b-117">Pokud má služba pracovního postupu vlastní vazby nebo svého kódu vlastních chování, ukládání do mezipaměti může nezabezpečené a proto je ve výchozím nastavení zakázáno.</span><span class="sxs-lookup"><span data-stu-id="2634b-117">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="2634b-118">Pokud však chcete zapnout ukládání do mezipaměti při nastavení této vlastnosti na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="2634b-118">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2634b-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2634b-119">Child Elements</span></span>  
  
|<span data-ttu-id="2634b-120">Element</span><span class="sxs-lookup"><span data-stu-id="2634b-120">Element</span></span>|<span data-ttu-id="2634b-121">Popis</span><span class="sxs-lookup"><span data-stu-id="2634b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2634b-122">\<channelNastavení></span><span class="sxs-lookup"><span data-stu-id="2634b-122">\<channelSettings></span></span>](channelsettings.md)|<span data-ttu-id="2634b-123">Určuje nastavení mezipaměti kanálu.</span><span class="sxs-lookup"><span data-stu-id="2634b-123">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="2634b-124">\<factoryNastavení></span><span class="sxs-lookup"><span data-stu-id="2634b-124">\<factorySettings></span></span>](factorysettings.md)|<span data-ttu-id="2634b-125">Určuje nastavení mezipaměti objekt pro vytváření kanálu.</span><span class="sxs-lookup"><span data-stu-id="2634b-125">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2634b-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2634b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="2634b-127">Element</span><span class="sxs-lookup"><span data-stu-id="2634b-127">Element</span></span>|<span data-ttu-id="2634b-128">Popis</span><span class="sxs-lookup"><span data-stu-id="2634b-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2634b-129">\<chování> \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2634b-129">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="2634b-130">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="2634b-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2634b-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2634b-131">Remarks</span></span>  
 <span data-ttu-id="2634b-132">Toto chování služby je určen pro pracovní postupy, které odesílání zpráv do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="2634b-132">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="2634b-133">Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="2634b-133">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="2634b-134">Ve výchozím nastavení v pracovním postupu hostované <xref:System.ServiceModel.WorkflowServiceHost>, je mezipaměť používaná aplikací <xref:System.ServiceModel.Activities.Send> zasílání zpráv aktivity je sdílen na všechny instance pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost> (hostitele úroveň ukládání do mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="2634b-134">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="2634b-135">Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance).</span><span class="sxs-lookup"><span data-stu-id="2634b-135">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="2634b-136">Ve výchozím nastavení pro všechny aktivity odeslání do svého pracovního postupu, který má koncové body definované v konfiguraci je zakázáno ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="2634b-136">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="2634b-137">Další informace o tom, jak změnit výchozí úrovně sdílení mezipaměti a nastavení mezipaměti pro uprostředkované kanály a mezipaměti kanálů, naleznete [v tématu Změna úrovní sdílení mezipaměti pro odesílání aktivit](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="2634b-137">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2634b-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="2634b-138">Example</span></span>  
 <span data-ttu-id="2634b-139">V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="2634b-139">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="2634b-140">Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby.</span><span class="sxs-lookup"><span data-stu-id="2634b-140">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="2634b-141">Následující příklad ukazuje obsah konfiguračního `MyChannelCacheBehavior` souboru, který obsahuje chování služby s vlastním nastavením mezipaměti výroby a mezipaměti kanálů.</span><span class="sxs-lookup"><span data-stu-id="2634b-141">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="2634b-142">Toto chování služby je `behaviorConfiguration` přidán do služby prostřednictvím atributu.</span><span class="sxs-lookup"><span data-stu-id="2634b-142">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2634b-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="2634b-143">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="2634b-144">Změna úrovní sdílení mezipaměti pro aktivity odesílání</span><span class="sxs-lookup"><span data-stu-id="2634b-144">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
