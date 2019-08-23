---
title: <behavior><serviceBehaviors> pracovního postupu
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 91883c42aa7bc0aa8fa0c63c3c45184ba69225d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946082"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="3bf8f-102">\<chování > \<serviceBehaviors > pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3bf8f-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="3bf8f-103">Prvek **chování** obsahuje soubor nastavení chování služby.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="3bf8f-104">Každé chování je indexováno podle **názvu**.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="3bf8f-105">Služby mohou pomocí tohoto názvu propojit s každým chováním pomocí atributu [ \<behaviorConfiguration elementu Endpoint >](../wcf/endpoint-element.md) .</span><span class="sxs-lookup"><span data-stu-id="3bf8f-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="3bf8f-106">To umožňuje koncové body sdílení obvyklé chování konfigurace bez předefinování nastavení.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="3bf8f-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3bf8f-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="3bf8f-108">\<> chování</span><span class="sxs-lookup"><span data-stu-id="3bf8f-108">\<behaviors></span></span>  
<span data-ttu-id="3bf8f-109">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3bf8f-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="3bf8f-110">\<> chování</span><span class="sxs-lookup"><span data-stu-id="3bf8f-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bf8f-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bf8f-111">Syntax</span></span>  
  
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
                                  hostLockRenewalPeriod="TimeSpan" 
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bf8f-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3bf8f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3bf8f-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bf8f-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="3bf8f-114">Attributes</span></span>  
  
|<span data-ttu-id="3bf8f-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="3bf8f-115">Attribute</span></span>|<span data-ttu-id="3bf8f-116">Popis</span><span class="sxs-lookup"><span data-stu-id="3bf8f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bf8f-117">name</span><span class="sxs-lookup"><span data-stu-id="3bf8f-117">name</span></span>|<span data-ttu-id="3bf8f-118">Jedinečný řetězec, který obsahuje název konfigurace chování.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="3bf8f-119">Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bf8f-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3bf8f-120">Child Elements</span></span>  
  
|<span data-ttu-id="3bf8f-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="3bf8f-121">Element</span></span>|<span data-ttu-id="3bf8f-122">Popis</span><span class="sxs-lookup"><span data-stu-id="3bf8f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bf8f-123">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="3bf8f-123">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="3bf8f-124">Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="3bf8f-125">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="3bf8f-125">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="3bf8f-126">Chování služby, které umožňuje službě využívat sledování ETW pomocí <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="3bf8f-127">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="3bf8f-127">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="3bf8f-128">Chování služby, které umožňuje přizpůsobení úrovní sdílení mezipaměti, nastavení mezipaměti objektu pro vytváření kanálu a nastavení mezipaměti kanálu pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí aktivit odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="3bf8f-129">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="3bf8f-129">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="3bf8f-130">Chování služby, které umožňuje nakonfigurovat <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci, která podporuje informace o stavu pro instance služby pracovního postupu do databáze SQL Server 2005 nebo SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="3bf8f-131">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="3bf8f-131">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="3bf8f-132">Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="3bf8f-133">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="3bf8f-133">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="3bf8f-134">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="3bf8f-135">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="3bf8f-135">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="3bf8f-136">Chování služby, který umožňuje určit akci, která má provést při dojde k neošetřené výjimce v rámci pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3bf8f-137">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3bf8f-137">Parent Elements</span></span>  
  
|<span data-ttu-id="3bf8f-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="3bf8f-138">Element</span></span>|<span data-ttu-id="3bf8f-139">Popis</span><span class="sxs-lookup"><span data-stu-id="3bf8f-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bf8f-140">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3bf8f-140">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="3bf8f-141">Kolekce elementů chování služby.</span><span class="sxs-lookup"><span data-stu-id="3bf8f-141">A collection of service behavior elements.</span></span>|
