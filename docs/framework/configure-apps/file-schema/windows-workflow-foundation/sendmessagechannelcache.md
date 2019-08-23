---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: de53eb16d53d1e37209e36f2f6bfdc4bdfd84465
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947547"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="50135-101">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="50135-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="50135-102">Chování služby, které umožňuje přizpůsobení úrovní sdílení mezipaměti, nastavení mezipaměti objektu pro vytváření kanálu a nastavení mezipaměti kanálu pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí aktivit odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="50135-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="50135-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="50135-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="50135-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="50135-104">\<behaviors></span></span>  
<span data-ttu-id="50135-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="50135-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="50135-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="50135-106">\<behavior></span></span>  
<span data-ttu-id="50135-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="50135-107">\<sendMessageChannelCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50135-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50135-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50135-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="50135-109">Attributes and Elements</span></span>  
 <span data-ttu-id="50135-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="50135-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50135-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="50135-111">Attributes</span></span>  
  
|<span data-ttu-id="50135-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="50135-112">Attribute</span></span>|<span data-ttu-id="50135-113">Popis</span><span class="sxs-lookup"><span data-stu-id="50135-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50135-114">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="50135-114">allowUnsafeCaching</span></span>|<span data-ttu-id="50135-115">Logická hodnota určující, zda chcete zapnout ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="50135-115">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="50135-116">Pokud má služba pracovního postupu vlastní vazby nebo svého kódu vlastních chování, ukládání do mezipaměti může nezabezpečené a proto je ve výchozím nastavení zakázáno.</span><span class="sxs-lookup"><span data-stu-id="50135-116">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="50135-117">Pokud však chcete zapnout ukládání do mezipaměti v nastavení této vlastnosti na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="50135-117">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50135-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="50135-118">Child Elements</span></span>  
  
|<span data-ttu-id="50135-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="50135-119">Element</span></span>|<span data-ttu-id="50135-120">Popis</span><span class="sxs-lookup"><span data-stu-id="50135-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50135-121">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="50135-121">\<channelSettings></span></span>](channelsettings.md)|<span data-ttu-id="50135-122">Určuje nastavení mezipaměti kanálu.</span><span class="sxs-lookup"><span data-stu-id="50135-122">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="50135-123">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="50135-123">\<factorySettings></span></span>](factorysettings.md)|<span data-ttu-id="50135-124">Určuje nastavení mezipaměti objekt pro vytváření kanálu.</span><span class="sxs-lookup"><span data-stu-id="50135-124">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="50135-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="50135-125">Parent Elements</span></span>  
  
|<span data-ttu-id="50135-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="50135-126">Element</span></span>|<span data-ttu-id="50135-127">Popis</span><span class="sxs-lookup"><span data-stu-id="50135-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50135-128">\<chování > \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="50135-128">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="50135-129">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="50135-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50135-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50135-130">Remarks</span></span>  
 <span data-ttu-id="50135-131">Toto chování služby je určen pro pracovní postupy, které odesílání zpráv do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="50135-131">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="50135-132">Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="50135-132">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="50135-133">Ve výchozím nastavení v pracovním postupu hostované <xref:System.ServiceModel.WorkflowServiceHost>, je mezipaměť používaná aplikací <xref:System.ServiceModel.Activities.Send> zasílání zpráv aktivity je sdílen na všechny instance pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost> (hostitele úroveň ukládání do mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="50135-133">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="50135-134">Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance).</span><span class="sxs-lookup"><span data-stu-id="50135-134">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="50135-135">Ve výchozím nastavení pro všechny aktivity odeslání do svého pracovního postupu, který má koncové body definované v konfiguraci je zakázáno ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="50135-135">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="50135-136">Další informace o tom, jak změnit výchozí úroveň sdílení mezipaměti a nastavení mezipaměti pro objekt pro vytváření kanálu a mezipaměť kanálu, najdete v tématu [Změna úrovní sdílení mezipaměti pro aktivity odeslat](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="50135-136">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50135-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="50135-137">Example</span></span>  
 <span data-ttu-id="50135-138">V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="50135-138">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="50135-139">Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby.</span><span class="sxs-lookup"><span data-stu-id="50135-139">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="50135-140">Následující příklad ukazuje obsah konfiguračního souboru, který obsahuje `MyChannelCacheBehavior` chování služby s nastavením mezipaměti pro vlastní tovární nastavení a mezipamětí kanálu.</span><span class="sxs-lookup"><span data-stu-id="50135-140">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="50135-141">Toto chování služby se do služby přidá prostřednictvím `behaviorConfiguration` atributu.</span><span class="sxs-lookup"><span data-stu-id="50135-141">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="50135-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50135-142">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="50135-143">Změna úrovní sdílení mezipaměti pro aktivity odesílání</span><span class="sxs-lookup"><span data-stu-id="50135-143">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
