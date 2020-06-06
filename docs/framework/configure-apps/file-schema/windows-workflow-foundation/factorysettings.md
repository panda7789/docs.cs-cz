---
title: <factorySettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: afb129407bc9dff752375f6e9fd69c728a809b37
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152181"
---
# \<factorySettings>
<span data-ttu-id="f70b3-101">Určuje nastavení mezipaměti objekt pro vytváření kanálu.</span><span class="sxs-lookup"><span data-stu-id="f70b3-101">Specifies the settings of the channel factory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sendMessageChannelCache>**](sendmessagechannelcache.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<factorySettings>**  
  
## <a name="syntax"></a><span data-ttu-id="f70b3-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f70b3-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f70b3-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f70b3-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f70b3-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f70b3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f70b3-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="f70b3-105">Attributes</span></span>  
  
|<span data-ttu-id="f70b3-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="f70b3-106">Attribute</span></span>|<span data-ttu-id="f70b3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f70b3-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f70b3-108">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="f70b3-108">idleTimeout</span></span>|<span data-ttu-id="f70b3-109">Časový interval hodnotu, která určuje maximální interval času, pro který objekt může zůstat nečinná v mezipaměti před vyřazení.</span><span class="sxs-lookup"><span data-stu-id="f70b3-109">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="f70b3-110">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="f70b3-110">leaseTimeout</span></span>|<span data-ttu-id="f70b3-111">Hodnota TimeSpan, která určuje časový interval, po jehož uplynutí je objekt odstraněn z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f70b3-111">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="f70b3-112">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="f70b3-112">maxItemsInCache</span></span>|<span data-ttu-id="f70b3-113">Celé číslo, která určuje maximální počet objektů, které lze uložit do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f70b3-113">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f70b3-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f70b3-114">Child Elements</span></span>  
 <span data-ttu-id="f70b3-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="f70b3-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f70b3-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f70b3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f70b3-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="f70b3-117">Element</span></span>|<span data-ttu-id="f70b3-118">Description</span><span class="sxs-lookup"><span data-stu-id="f70b3-118">Description</span></span>|  
|-------------|-----------------|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|<span data-ttu-id="f70b3-119">Chování služby, které umožňuje přizpůsobení úrovní sdílení mezipaměti, nastavení mezipaměti objektu pro vytváření kanálu a nastavení mezipaměti kanálu pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí aktivit odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="f70b3-119">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f70b3-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f70b3-120">Remarks</span></span>  
 <span data-ttu-id="f70b3-121">Toto chování služby je určen pro pracovní postupy, které odesílání zpráv do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="f70b3-121">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="f70b3-122">Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="f70b3-122">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="f70b3-123">Ve výchozím nastavení v pracovním postupu hostované <xref:System.ServiceModel.WorkflowServiceHost>, je mezipaměť používaná aplikací <xref:System.ServiceModel.Activities.Send> zasílání zpráv aktivity je sdílen na všechny instance pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost> (hostitele úroveň ukládání do mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="f70b3-123">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="f70b3-124">Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance).</span><span class="sxs-lookup"><span data-stu-id="f70b3-124">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="f70b3-125">Ve výchozím nastavení pro všechny aktivity odeslání do svého pracovního postupu, který má koncové body definované v konfiguraci je zakázáno ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f70b3-125">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="f70b3-126">Další informace o tom, jak změnit výchozí úroveň sdílení mezipaměti a nastavení mezipaměti pro objekt pro vytváření kanálu a mezipaměť kanálu, najdete v tématu [Změna úrovní sdílení mezipaměti pro aktivity odeslat](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="f70b3-126">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f70b3-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="f70b3-127">Example</span></span>  
 <span data-ttu-id="f70b3-128">V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f70b3-128">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="f70b3-129">Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby.</span><span class="sxs-lookup"><span data-stu-id="f70b3-129">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="f70b3-130">Následující příklad ukazuje obsah konfiguračního souboru, který obsahuje `MyChannelCacheBehavior` chování služby s nastavením mezipaměti pro vlastní tovární nastavení a mezipamětí kanálu.</span><span class="sxs-lookup"><span data-stu-id="f70b3-130">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="f70b3-131">Toto chování služby se do služby přidá prostřednictvím `behaviorConfiguration` atributu.</span><span class="sxs-lookup"><span data-stu-id="f70b3-131">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f70b3-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="f70b3-132">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="f70b3-133">Změna úrovní sdílení mezipaměti pro aktivity odesílání</span><span class="sxs-lookup"><span data-stu-id="f70b3-133">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
