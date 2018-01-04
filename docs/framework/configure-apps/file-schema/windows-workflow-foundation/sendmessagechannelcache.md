---
title: '&lt;sendMessageChannelCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a2fe2fbeb82ea4412a85a4503a5ae950639a659
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsendmessagechannelcachegt"></a><span data-ttu-id="f8e25-102">&lt;sendMessageChannelCache&gt;</span><span class="sxs-lookup"><span data-stu-id="f8e25-102">&lt;sendMessageChannelCache&gt;</span></span>
<span data-ttu-id="f8e25-103">Chování služby, která umožňuje přizpůsobení mezipaměti sdílení úrovní, nastavení objektu pro vytváření mezipaměti kanál a nastavení mezipaměti kanál pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí odesílání aktivity zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="f8e25-103">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="f8e25-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f8e25-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f8e25-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f8e25-105">\<behaviors></span></span>  
<span data-ttu-id="f8e25-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f8e25-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f8e25-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f8e25-107">\<behavior></span></span>  
<span data-ttu-id="f8e25-108">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="f8e25-108">\<sendMessageChannelCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8e25-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8e25-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8e25-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f8e25-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f8e25-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f8e25-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8e25-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f8e25-112">Attributes</span></span>  
  
|<span data-ttu-id="f8e25-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f8e25-113">Attribute</span></span>|<span data-ttu-id="f8e25-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f8e25-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8e25-115">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="f8e25-115">allowUnsafeCaching</span></span>|<span data-ttu-id="f8e25-116">Logická hodnota určující, zda chcete zapnout ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f8e25-116">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="f8e25-117">Pokud má služba pracovního postupu vlastní vazby nebo svého kódu vlastních chování, ukládání do mezipaměti může nezabezpečené a proto je ve výchozím nastavení zakázáno.</span><span class="sxs-lookup"><span data-stu-id="f8e25-117">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="f8e25-118">Ale pokud chcete zapnout ukládání do mezipaměti na tuto vlastnost nastavit **true**.</span><span class="sxs-lookup"><span data-stu-id="f8e25-118">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8e25-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f8e25-119">Child Elements</span></span>  
  
|<span data-ttu-id="f8e25-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="f8e25-120">Element</span></span>|<span data-ttu-id="f8e25-121">Popis</span><span class="sxs-lookup"><span data-stu-id="f8e25-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8e25-122">\<channelSettings ></span><span class="sxs-lookup"><span data-stu-id="f8e25-122">\<channelSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/channelsettings.md)|<span data-ttu-id="f8e25-123">Určuje nastavení mezipaměti kanálu.</span><span class="sxs-lookup"><span data-stu-id="f8e25-123">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="f8e25-124">\<factorySettings ></span><span class="sxs-lookup"><span data-stu-id="f8e25-124">\<factorySettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/factorysettings.md)|<span data-ttu-id="f8e25-125">Určuje nastavení mezipaměti objekt pro vytváření kanálu.</span><span class="sxs-lookup"><span data-stu-id="f8e25-125">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8e25-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f8e25-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f8e25-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="f8e25-127">Element</span></span>|<span data-ttu-id="f8e25-128">Popis</span><span class="sxs-lookup"><span data-stu-id="f8e25-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8e25-129">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f8e25-129">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f8e25-130">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="f8e25-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8e25-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8e25-131">Remarks</span></span>  
 <span data-ttu-id="f8e25-132">Toto chování služby je určen pro pracovní postupy, které odesílání zpráv do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="f8e25-132">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="f8e25-133">Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="f8e25-133">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="f8e25-134">Ve výchozím nastavení v pracovním postupu hostované <xref:System.ServiceModel.WorkflowServiceHost>, je mezipaměť používaná aplikací <xref:System.ServiceModel.Activities.Send> zasílání zpráv aktivity je sdílen na všechny instance pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost> (hostitele úroveň ukládání do mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="f8e25-134">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="f8e25-135">Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance).</span><span class="sxs-lookup"><span data-stu-id="f8e25-135">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="f8e25-136">Ve výchozím nastavení pro všechny aktivity odeslání do svého pracovního postupu, který má koncové body definované v konfiguraci je zakázáno ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f8e25-136">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="f8e25-137">Změna úrovní sdílení mezipaměti výchozí a mezipaměti nastavení pro vytváření kanálů a kanál mezipaměti naleznete v tématu [změna úrovní sdílení mezipaměti pro aktivity odesílání](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="f8e25-137"> how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8e25-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8e25-138">Example</span></span>  
 <span data-ttu-id="f8e25-139">V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f8e25-139">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="f8e25-140">Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby.</span><span class="sxs-lookup"><span data-stu-id="f8e25-140">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="f8e25-141">Následující příklad ukazuje konfigurační soubor, který obsahuje obsah **MyChannelCacheBehavior** chování služby s vlastní objekt pro vytváření mezipaměti a kanál nastavení ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f8e25-141">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="f8e25-142">Toto chování služby se přidá do služby pomocí **behaviorConfiguarion** atribut.</span><span class="sxs-lookup"><span data-stu-id="f8e25-142">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8e25-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8e25-143">See Also</span></span>  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>  
 <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>  
 <xref:System.ServiceModel.Activities.Send>  
 [<span data-ttu-id="f8e25-144">Změna úrovní sdílení mezipaměti pro aktivity odesílání</span><span class="sxs-lookup"><span data-stu-id="f8e25-144">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
