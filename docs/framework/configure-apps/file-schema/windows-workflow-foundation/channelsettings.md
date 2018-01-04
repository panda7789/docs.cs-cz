---
title: '&lt;channelSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 94a4457f-f43f-458d-a47e-2d11103ee75e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f045665565a29f0248bf2e05bd1b285d59d6c375
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltchannelsettingsgt"></a><span data-ttu-id="81366-102">&lt;channelSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="81366-102">&lt;channelSettings&gt;</span></span>
<span data-ttu-id="81366-103">Určuje nastavení mezipaměti kanálu.</span><span class="sxs-lookup"><span data-stu-id="81366-103">Specifies the settings of the channel cache.</span></span>  
  
<span data-ttu-id="81366-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="81366-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="81366-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="81366-105">\<behaviors></span></span>  
<span data-ttu-id="81366-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="81366-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="81366-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="81366-107">\<behavior></span></span>  
<span data-ttu-id="81366-108">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="81366-108">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="81366-109">\<channelSettings ></span><span class="sxs-lookup"><span data-stu-id="81366-109">\<channelSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81366-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81366-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81366-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="81366-111">Attributes and Elements</span></span>  
 <span data-ttu-id="81366-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="81366-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81366-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="81366-113">Attributes</span></span>  
  
|<span data-ttu-id="81366-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="81366-114">Attribute</span></span>|<span data-ttu-id="81366-115">Popis</span><span class="sxs-lookup"><span data-stu-id="81366-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81366-116">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="81366-116">idleTimeout</span></span>|<span data-ttu-id="81366-117">Časový interval hodnotu, která určuje maximální interval času, pro který objekt může zůstat nečinná v mezipaměti před vyřazení.</span><span class="sxs-lookup"><span data-stu-id="81366-117">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="81366-118">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="81366-118">leaseTimeout</span></span>|<span data-ttu-id="81366-119">Hodnota časový interval, která udává interval času, po jejímž uplynutí je objekt odebrány z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="81366-119">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="81366-120">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="81366-120">maxItemsInCache</span></span>|<span data-ttu-id="81366-121">Celé číslo, která určuje maximální počet objektů, které lze uložit do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="81366-121">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81366-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="81366-122">Child Elements</span></span>  
 <span data-ttu-id="81366-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="81366-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81366-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="81366-124">Parent Elements</span></span>  
  
|<span data-ttu-id="81366-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="81366-125">Element</span></span>|<span data-ttu-id="81366-126">Popis</span><span class="sxs-lookup"><span data-stu-id="81366-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81366-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="81366-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="81366-128">Chování služby, která umožňuje přizpůsobení mezipaměti sdílení úrovní, nastavení objektu pro vytváření mezipaměti kanál a nastavení mezipaměti kanál pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí odesílání aktivity zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="81366-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81366-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81366-129">Remarks</span></span>  
 <span data-ttu-id="81366-130">Toto chování služby je určen pro pracovní postupy, které odesílání zpráv do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="81366-130">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="81366-131">Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="81366-131">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="81366-132">Ve výchozím nastavení v pracovním postupu hostované <xref:System.ServiceModel.WorkflowServiceHost>, je mezipaměť používaná aplikací <xref:System.ServiceModel.Activities.Send> zasílání zpráv aktivity je sdílen na všechny instance pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost> (hostitele úroveň ukládání do mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="81366-132">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="81366-133">Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance).</span><span class="sxs-lookup"><span data-stu-id="81366-133">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="81366-134">Ve výchozím nastavení pro všechny aktivity odeslání do svého pracovního postupu, který má koncové body definované v konfiguraci je zakázáno ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="81366-134">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="81366-135">Změna úrovní sdílení mezipaměti výchozí a mezipaměti nastavení pro vytváření kanálů a kanál mezipaměti naleznete v tématu [změna úrovní sdílení mezipaměti pro aktivity odesílání](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="81366-135"> how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81366-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="81366-136">Example</span></span>  
 <span data-ttu-id="81366-137">V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="81366-137">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="81366-138">Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby.</span><span class="sxs-lookup"><span data-stu-id="81366-138">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="81366-139">Následující příklad ukazuje konfigurační soubor, který obsahuje obsah **MyChannelCacheBehavior** chování služby s vlastní objekt pro vytváření mezipaměti a kanál nastavení ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="81366-139">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="81366-140">Toto chování služby se přidá do služby pomocí **behaviorConfiguarion** atribut.</span><span class="sxs-lookup"><span data-stu-id="81366-140">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81366-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="81366-141">See Also</span></span>  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>  
 <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.ChannelCacheSettings>  
 [<span data-ttu-id="81366-142">Změna úrovní sdílení mezipaměti pro aktivity odesílání</span><span class="sxs-lookup"><span data-stu-id="81366-142">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
