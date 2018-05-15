---
title: '&lt;chování&gt; z &lt;serviceBehaviors&gt; pracovního postupu'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 303cf3a8f954b20beaa76fb46294dbb37488fd61
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a><span data-ttu-id="b7713-102">&lt;chování&gt; z &lt;serviceBehaviors&gt; pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b7713-102">&lt;behavior&gt; of &lt;serviceBehaviors&gt; of workflow</span></span>
<span data-ttu-id="b7713-103">**Chování** element obsahuje kolekce nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="b7713-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="b7713-104">Každý chování je indexované podle jeho **název**.</span><span class="sxs-lookup"><span data-stu-id="b7713-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="b7713-105">Služby můžete propojit každý chování pomocí této konfigurace pomocí názvu **behaviorConfiguration**atribut [ \<endpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="b7713-105">Services can link to each behavior through this name using the **behaviorConfiguration**attribute of the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="b7713-106">To umožňuje koncové body sdílení obvyklé chování konfigurace bez předefinování nastavení.</span><span class="sxs-lookup"><span data-stu-id="b7713-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="b7713-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b7713-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="b7713-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b7713-108">\<behaviors></span></span>  
<span data-ttu-id="b7713-109">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b7713-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="b7713-110">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b7713-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7713-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7713-111">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String" 
                                  honstLockRenewalPeriod="TimeSpan" 
                                  instanceCompletionAction="DeleteNothing/DeleteAll" 
                                  instanceEncodingAction="None/GZip" 
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan" 
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7713-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b7713-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b7713-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b7713-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7713-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="b7713-114">Attributes</span></span>  
  
|<span data-ttu-id="b7713-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="b7713-115">Attribute</span></span>|<span data-ttu-id="b7713-116">Popis</span><span class="sxs-lookup"><span data-stu-id="b7713-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7713-117">name</span><span class="sxs-lookup"><span data-stu-id="b7713-117">name</span></span>|<span data-ttu-id="b7713-118">Jedinečný řetězec, který obsahuje název konfigurace chování.</span><span class="sxs-lookup"><span data-stu-id="b7713-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="b7713-119">Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element.</span><span class="sxs-lookup"><span data-stu-id="b7713-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7713-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b7713-120">Child Elements</span></span>  
  
|<span data-ttu-id="b7713-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="b7713-121">Element</span></span>|<span data-ttu-id="b7713-122">Popis</span><span class="sxs-lookup"><span data-stu-id="b7713-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7713-123">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="b7713-123">\<bufferReceive></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|<span data-ttu-id="b7713-124">Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b7713-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="b7713-125">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="b7713-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|<span data-ttu-id="b7713-126">Chování služby, která umožňuje službám využít trasování událostí pro Windows Sledování pomocí <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="b7713-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="b7713-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="b7713-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="b7713-128">Chování služby, která umožňuje přizpůsobení mezipaměti sdílení úrovní, nastavení objektu pro vytváření mezipaměti kanál a nastavení mezipaměti kanál pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí odesílání aktivity zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="b7713-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="b7713-129">\<sqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="b7713-129">\<sqlWorkflowInstanceStore></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|<span data-ttu-id="b7713-130">Chování služby, který umožňuje nakonfigurovat <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci, která podporuje zachování informací o stavu pro instance služby pracovního postupu do databáze systému SQL Server 2005 nebo SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="b7713-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="b7713-131">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="b7713-131">\<workflowIdle></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|<span data-ttu-id="b7713-132">Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.</span><span class="sxs-lookup"><span data-stu-id="b7713-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="b7713-133">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="b7713-133">\<workflowInstanceManagement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|<span data-ttu-id="b7713-134">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="b7713-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="b7713-135">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="b7713-135">\<workflowUnhandledException></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|<span data-ttu-id="b7713-136">Chování služby, který umožňuje určit akci, která má provést při dojde k neošetřené výjimce v rámci pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="b7713-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7713-137">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b7713-137">Parent Elements</span></span>  
  
|<span data-ttu-id="b7713-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="b7713-138">Element</span></span>|<span data-ttu-id="b7713-139">Popis</span><span class="sxs-lookup"><span data-stu-id="b7713-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7713-140">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b7713-140">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="b7713-141">Kolekce elementů chování služby.</span><span class="sxs-lookup"><span data-stu-id="b7713-141">A collection of service behavior elements.</span></span>|
