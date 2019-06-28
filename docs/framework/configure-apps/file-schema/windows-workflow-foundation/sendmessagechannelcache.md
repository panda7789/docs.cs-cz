---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: e4f77e95cbacc2d025b57dceed5b1bd0d2851e81
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422906"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="ab03b-101">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="ab03b-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="ab03b-102">Chování služby, který umožňuje vlastní nastavení mezipaměti sdílení úrovně, nastavení mezipaměti kanálu objekt pro vytváření a nastavení mezipaměti kanál pro pracovní postupy, které odesílání zpráv do koncových bodů služby pomocí odeslání zasílání zpráv aktivity.</span><span class="sxs-lookup"><span data-stu-id="ab03b-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="ab03b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ab03b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ab03b-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ab03b-104">\<behaviors></span></span>  
<span data-ttu-id="ab03b-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ab03b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="ab03b-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ab03b-106">\<behavior></span></span>  
<span data-ttu-id="ab03b-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="ab03b-107">\<sendMessageChannelCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab03b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab03b-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab03b-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ab03b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ab03b-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ab03b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab03b-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ab03b-111">Attributes</span></span>  
  
|<span data-ttu-id="ab03b-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="ab03b-112">Attribute</span></span>|<span data-ttu-id="ab03b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ab03b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab03b-114">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="ab03b-114">allowUnsafeCaching</span></span>|<span data-ttu-id="ab03b-115">Logická hodnota určující, zda chcete zapnout ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ab03b-115">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="ab03b-116">Pokud má služba pracovního postupu vlastní vazby nebo svého kódu vlastních chování, ukládání do mezipaměti může nezabezpečené a proto je ve výchozím nastavení zakázáno.</span><span class="sxs-lookup"><span data-stu-id="ab03b-116">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="ab03b-117">Nicméně, pokud chcete vypnout ukládání do mezipaměti na nastavte tuto vlastnost na **true**.</span><span class="sxs-lookup"><span data-stu-id="ab03b-117">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab03b-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ab03b-118">Child Elements</span></span>  
  
|<span data-ttu-id="ab03b-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab03b-119">Element</span></span>|<span data-ttu-id="ab03b-120">Popis</span><span class="sxs-lookup"><span data-stu-id="ab03b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab03b-121">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="ab03b-121">\<channelSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/channelsettings.md)|<span data-ttu-id="ab03b-122">Určuje nastavení mezipaměti kanálu.</span><span class="sxs-lookup"><span data-stu-id="ab03b-122">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="ab03b-123">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="ab03b-123">\<factorySettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/factorysettings.md)|<span data-ttu-id="ab03b-124">Určuje nastavení mezipaměti objekt pro vytváření kanálu.</span><span class="sxs-lookup"><span data-stu-id="ab03b-124">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab03b-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ab03b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ab03b-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab03b-126">Element</span></span>|<span data-ttu-id="ab03b-127">Popis</span><span class="sxs-lookup"><span data-stu-id="ab03b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab03b-128">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ab03b-128">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="ab03b-129">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="ab03b-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab03b-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab03b-130">Remarks</span></span>  
 <span data-ttu-id="ab03b-131">Toto chování služby je určen pro pracovní postupy, které odesílání zpráv do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="ab03b-131">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="ab03b-132">Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ab03b-132">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="ab03b-133">Ve výchozím nastavení v pracovním postupu hostované <xref:System.ServiceModel.WorkflowServiceHost>, je mezipaměť používaná aplikací <xref:System.ServiceModel.Activities.Send> zasílání zpráv aktivity je sdílen na všechny instance pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost> (hostitele úroveň ukládání do mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="ab03b-133">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="ab03b-134">Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance).</span><span class="sxs-lookup"><span data-stu-id="ab03b-134">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="ab03b-135">Ve výchozím nastavení pro všechny aktivity odeslání do svého pracovního postupu, který má koncové body definované v konfiguraci je zakázáno ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ab03b-135">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="ab03b-136">Další informace o tom, jak změnit výchozí mezipaměti sdílení úrovně a nastavení mezipaměti pro objekt pro vytváření kanálů a mezipaměti kanálu najdete v tématu [změna úrovní sdílení mezipaměti pro aktivity odesílání](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="ab03b-136">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab03b-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab03b-137">Example</span></span>  
 <span data-ttu-id="ab03b-138">V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ab03b-138">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="ab03b-139">Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby.</span><span class="sxs-lookup"><span data-stu-id="ab03b-139">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="ab03b-140">Následující příklad ukazuje obsah, který obsahuje konfigurační soubor `MyChannelCacheBehavior` služeb chování s nastavením vlastní objekt pro vytváření mezipaměti a kanál mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ab03b-140">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="ab03b-141">Toto chování služby se přidá do této služby prostřednictvím `behaviorConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="ab03b-141">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ab03b-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab03b-142">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="ab03b-143">Změna úrovní sdílení mezipaměti pro aktivity odesílání</span><span class="sxs-lookup"><span data-stu-id="ab03b-143">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
