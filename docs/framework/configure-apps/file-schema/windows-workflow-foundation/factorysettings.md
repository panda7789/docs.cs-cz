---
title: <factorySettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: 8ee874d4f92ee398dc9752d3c1d1f22610b17097
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422914"
---
# <a name="factorysettings"></a><span data-ttu-id="137c2-101">\<factorySettings ></span><span class="sxs-lookup"><span data-stu-id="137c2-101">\<factorySettings></span></span>
<span data-ttu-id="137c2-102">Určuje nastavení mezipaměti objekt pro vytváření kanálu.</span><span class="sxs-lookup"><span data-stu-id="137c2-102">Specifies the settings of the channel factory cache.</span></span>  
  
<span data-ttu-id="137c2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="137c2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="137c2-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="137c2-104">\<behaviors></span></span>  
<span data-ttu-id="137c2-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="137c2-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="137c2-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="137c2-106">\<behavior></span></span>  
<span data-ttu-id="137c2-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="137c2-107">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="137c2-108">\<factorySettings ></span><span class="sxs-lookup"><span data-stu-id="137c2-108">\<factorySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137c2-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="137c2-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="137c2-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="137c2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="137c2-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="137c2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="137c2-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="137c2-112">Attributes</span></span>  
  
|<span data-ttu-id="137c2-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="137c2-113">Attribute</span></span>|<span data-ttu-id="137c2-114">Popis</span><span class="sxs-lookup"><span data-stu-id="137c2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="137c2-115">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="137c2-115">idleTimeout</span></span>|<span data-ttu-id="137c2-116">Časový interval hodnotu, která určuje maximální interval času, pro který objekt může zůstat nečinná v mezipaměti před vyřazení.</span><span class="sxs-lookup"><span data-stu-id="137c2-116">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="137c2-117">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="137c2-117">leaseTimeout</span></span>|<span data-ttu-id="137c2-118">Časový interval hodnotu, která určuje dobu, po jejímž uplynutí je objekt odebrat z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="137c2-118">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="137c2-119">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="137c2-119">maxItemsInCache</span></span>|<span data-ttu-id="137c2-120">Celé číslo, která určuje maximální počet objektů, které lze uložit do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="137c2-120">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="137c2-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="137c2-121">Child Elements</span></span>  
 <span data-ttu-id="137c2-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="137c2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="137c2-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="137c2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="137c2-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="137c2-124">Element</span></span>|<span data-ttu-id="137c2-125">Popis</span><span class="sxs-lookup"><span data-stu-id="137c2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="137c2-126">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="137c2-126">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="137c2-127">Chování služby, který umožňuje vlastní nastavení mezipaměti sdílení úrovně, nastavení mezipaměti kanálu objekt pro vytváření a nastavení mezipaměti kanál pro pracovní postupy, které odesílání zpráv do koncových bodů služby pomocí odeslání zasílání zpráv aktivity.</span><span class="sxs-lookup"><span data-stu-id="137c2-127">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="137c2-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="137c2-128">Remarks</span></span>  
 <span data-ttu-id="137c2-129">Toto chování služby je určen pro pracovní postupy, které odesílání zpráv do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="137c2-129">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="137c2-130">Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="137c2-130">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="137c2-131">Ve výchozím nastavení v pracovním postupu hostované <xref:System.ServiceModel.WorkflowServiceHost>, je mezipaměť používaná aplikací <xref:System.ServiceModel.Activities.Send> zasílání zpráv aktivity je sdílen na všechny instance pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost> (hostitele úroveň ukládání do mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="137c2-131">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="137c2-132">Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance).</span><span class="sxs-lookup"><span data-stu-id="137c2-132">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="137c2-133">Ve výchozím nastavení pro všechny aktivity odeslání do svého pracovního postupu, který má koncové body definované v konfiguraci je zakázáno ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="137c2-133">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="137c2-134">Další informace o tom, jak změnit výchozí mezipaměti sdílení úrovně a nastavení mezipaměti pro objekt pro vytváření kanálů a mezipaměti kanálu najdete v tématu [změna úrovní sdílení mezipaměti pro aktivity odesílání](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="137c2-134">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="137c2-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="137c2-135">Example</span></span>  
 <span data-ttu-id="137c2-136">V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="137c2-136">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="137c2-137">Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby.</span><span class="sxs-lookup"><span data-stu-id="137c2-137">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="137c2-138">Následující příklad ukazuje obsah, který obsahuje konfigurační soubor `MyChannelCacheBehavior` služeb chování s nastavením vlastní objekt pro vytváření mezipaměti a kanál mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="137c2-138">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="137c2-139">Toto chování služby se přidá do této služby prostřednictvím `behaviorConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="137c2-139">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="137c2-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="137c2-140">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="137c2-141">Změna úrovní sdílení mezipaměti pro aktivity odesílání</span><span class="sxs-lookup"><span data-stu-id="137c2-141">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
