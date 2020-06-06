---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: b68c6d2e526eb22328806558d7c167b7f2ed0820
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151998"
---
# \<sendMessageChannelCache>
<span data-ttu-id="214ac-101">Chování služby, které umožňuje přizpůsobení úrovní sdílení mezipaměti, nastavení mezipaměti objektu pro vytváření kanálu a nastavení mezipaměti kanálu pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí aktivit odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="214ac-101">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**  
  
## <a name="syntax"></a><span data-ttu-id="214ac-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="214ac-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="214ac-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="214ac-103">Attributes and Elements</span></span>  
 <span data-ttu-id="214ac-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="214ac-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="214ac-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="214ac-105">Attributes</span></span>  
  
|<span data-ttu-id="214ac-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="214ac-106">Attribute</span></span>|<span data-ttu-id="214ac-107">Popis</span><span class="sxs-lookup"><span data-stu-id="214ac-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="214ac-108">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="214ac-108">allowUnsafeCaching</span></span>|<span data-ttu-id="214ac-109">Logická hodnota určující, zda chcete zapnout ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="214ac-109">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="214ac-110">Pokud má služba pracovního postupu vlastní vazby nebo svého kódu vlastních chování, ukládání do mezipaměti může nezabezpečené a proto je ve výchozím nastavení zakázáno.</span><span class="sxs-lookup"><span data-stu-id="214ac-110">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="214ac-111">Pokud však chcete zapnout ukládání do mezipaměti v nastavení této vlastnosti na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="214ac-111">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="214ac-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="214ac-112">Child Elements</span></span>  
  
|<span data-ttu-id="214ac-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="214ac-113">Element</span></span>|<span data-ttu-id="214ac-114">Description</span><span class="sxs-lookup"><span data-stu-id="214ac-114">Description</span></span>|  
|-------------|-----------------|  
|[\<channelSettings>](channelsettings.md)|<span data-ttu-id="214ac-115">Určuje nastavení mezipaměti kanálu.</span><span class="sxs-lookup"><span data-stu-id="214ac-115">Specifies the settings of the channel cache.</span></span>|  
|[\<factorySettings>](factorysettings.md)|<span data-ttu-id="214ac-116">Určuje nastavení mezipaměti objekt pro vytváření kanálu.</span><span class="sxs-lookup"><span data-stu-id="214ac-116">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="214ac-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="214ac-117">Parent Elements</span></span>  
  
|<span data-ttu-id="214ac-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="214ac-118">Element</span></span>|<span data-ttu-id="214ac-119">Description</span><span class="sxs-lookup"><span data-stu-id="214ac-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="214ac-120">\<behavior>tohoto\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="214ac-120">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="214ac-121">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="214ac-121">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="214ac-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="214ac-122">Remarks</span></span>  
 <span data-ttu-id="214ac-123">Toto chování služby je určen pro pracovní postupy, které odesílání zpráv do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="214ac-123">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="214ac-124">Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="214ac-124">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="214ac-125">Ve výchozím nastavení v pracovním postupu hostované <xref:System.ServiceModel.WorkflowServiceHost>, je mezipaměť používaná aplikací <xref:System.ServiceModel.Activities.Send> zasílání zpráv aktivity je sdílen na všechny instance pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost> (hostitele úroveň ukládání do mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="214ac-125">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="214ac-126">Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance).</span><span class="sxs-lookup"><span data-stu-id="214ac-126">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="214ac-127">Ve výchozím nastavení pro všechny aktivity odeslání do svého pracovního postupu, který má koncové body definované v konfiguraci je zakázáno ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="214ac-127">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="214ac-128">Další informace o tom, jak změnit výchozí úroveň sdílení mezipaměti a nastavení mezipaměti pro objekt pro vytváření kanálu a mezipaměť kanálu, najdete v tématu [Změna úrovní sdílení mezipaměti pro aktivity odeslat](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="214ac-128">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="214ac-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="214ac-129">Example</span></span>  
 <span data-ttu-id="214ac-130">V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="214ac-130">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="214ac-131">Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby.</span><span class="sxs-lookup"><span data-stu-id="214ac-131">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="214ac-132">Následující příklad ukazuje obsah konfiguračního souboru, který obsahuje `MyChannelCacheBehavior` chování služby s nastavením mezipaměti pro vlastní tovární nastavení a mezipamětí kanálu.</span><span class="sxs-lookup"><span data-stu-id="214ac-132">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="214ac-133">Toto chování služby se do služby přidá prostřednictvím `behaviorConfiguration` atributu.</span><span class="sxs-lookup"><span data-stu-id="214ac-133">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="214ac-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="214ac-134">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="214ac-135">Změna úrovní sdílení mezipaměti pro aktivity odesílání</span><span class="sxs-lookup"><span data-stu-id="214ac-135">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
