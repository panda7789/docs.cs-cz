---
title: <behavior>pracovního <serviceBehaviors> postupu
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152317"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="cdfe6-102">\<chování> \<serviceBehaviors> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="cdfe6-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="cdfe6-103">Prvek **chování** obsahuje kolekci nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="cdfe6-104">Každé chování je indexováno **podle**názvu .</span><span class="sxs-lookup"><span data-stu-id="cdfe6-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="cdfe6-105">Služby mohou propojit každé chování prostřednictvím tohoto názvu pomocí atributu **behaviorConfiguration** [ \<koncového bodu>](../wcf/endpoint-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="cdfe6-106">To umožňuje koncové body sdílení obvyklé chování konfigurace bez předefinování nastavení.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="cdfe6-107">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cdfe6-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cdfe6-108">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cdfe6-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="cdfe6-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cdfe6-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="cdfe6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cdfe6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="cdfe6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chování>**</span><span class="sxs-lookup"><span data-stu-id="cdfe6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdfe6-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdfe6-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdfe6-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cdfe6-113">Attributes and Elements</span></span>  
 <span data-ttu-id="cdfe6-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdfe6-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="cdfe6-115">Attributes</span></span>  
  
|<span data-ttu-id="cdfe6-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="cdfe6-116">Attribute</span></span>|<span data-ttu-id="cdfe6-117">Popis</span><span class="sxs-lookup"><span data-stu-id="cdfe6-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cdfe6-118">jméno</span><span class="sxs-lookup"><span data-stu-id="cdfe6-118">name</span></span>|<span data-ttu-id="cdfe6-119">Jedinečný řetězec, který obsahuje název konfigurace chování.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="cdfe6-120">Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdfe6-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cdfe6-121">Child Elements</span></span>  
  
|<span data-ttu-id="cdfe6-122">Element</span><span class="sxs-lookup"><span data-stu-id="cdfe6-122">Element</span></span>|<span data-ttu-id="cdfe6-123">Popis</span><span class="sxs-lookup"><span data-stu-id="cdfe6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdfe6-124">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="cdfe6-124">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="cdfe6-125">Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-125">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="cdfe6-126">\<směrování></span><span class="sxs-lookup"><span data-stu-id="cdfe6-126">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="cdfe6-127">Chování služby, které umožňuje službě využívat sledování <xref:System.Activities.Tracking.EtwTrackingParticipant>ETW pomocí .</span><span class="sxs-lookup"><span data-stu-id="cdfe6-127">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="cdfe6-128">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="cdfe6-128">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="cdfe6-129">Chování služby, které umožňuje přizpůsobení úrovní sdílení mezipaměti, nastavení mezipaměti kanálu ve výrobě a nastavení mezipaměti kanálu pro pracovní postupy, které odesílají zprávy koncovým bodům služby pomocí aktivit odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-129">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="cdfe6-130">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="cdfe6-130">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="cdfe6-131">Chování služby, které umožňuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> konfigurovat funkci, která podporuje uchování informací o stavu pro instance služby pracovního postupu do databáze SERVERU SQL Server 2005 nebo SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-131">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="cdfe6-132">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="cdfe6-132">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="cdfe6-133">Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-133">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="cdfe6-134">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="cdfe6-134">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="cdfe6-135">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-135">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="cdfe6-136">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="cdfe6-136">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="cdfe6-137">Chování služby, který umožňuje určit akci, která má provést při dojde k neošetřené výjimce v rámci pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-137">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdfe6-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cdfe6-138">Parent Elements</span></span>  
  
|<span data-ttu-id="cdfe6-139">Element</span><span class="sxs-lookup"><span data-stu-id="cdfe6-139">Element</span></span>|<span data-ttu-id="cdfe6-140">Popis</span><span class="sxs-lookup"><span data-stu-id="cdfe6-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdfe6-141">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="cdfe6-141">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="cdfe6-142">Kolekce elementů chování služby.</span><span class="sxs-lookup"><span data-stu-id="cdfe6-142">A collection of service behavior elements.</span></span>|
