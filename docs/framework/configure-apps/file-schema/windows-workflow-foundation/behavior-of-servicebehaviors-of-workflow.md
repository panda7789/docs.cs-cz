---
title: <behavior><serviceBehaviors> pracovního postupu
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 65bde45ffdd4af166d5b44308162c23257659802
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398894"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="2fe89-102">\<chování > \<serviceBehaviors > pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2fe89-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="2fe89-103">Prvek **chování** obsahuje soubor nastavení chování služby.</span><span class="sxs-lookup"><span data-stu-id="2fe89-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="2fe89-104">Každé chování je indexováno podle **názvu**.</span><span class="sxs-lookup"><span data-stu-id="2fe89-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="2fe89-105">Služby mohou pomocí tohoto názvu propojit s každým chováním pomocí atributu [ \<behaviorConfiguration elementu Endpoint >](../wcf/endpoint-element.md) .</span><span class="sxs-lookup"><span data-stu-id="2fe89-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="2fe89-106">To umožňuje koncové body sdílení obvyklé chování konfigurace bez předefinování nastavení.</span><span class="sxs-lookup"><span data-stu-id="2fe89-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="2fe89-107">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2fe89-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2fe89-108">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2fe89-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="2fe89-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2fe89-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="2fe89-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2fe89-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="2fe89-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> chování**</span><span class="sxs-lookup"><span data-stu-id="2fe89-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fe89-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fe89-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fe89-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2fe89-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2fe89-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2fe89-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fe89-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="2fe89-115">Attributes</span></span>  
  
|<span data-ttu-id="2fe89-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="2fe89-116">Attribute</span></span>|<span data-ttu-id="2fe89-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2fe89-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2fe89-118">name</span><span class="sxs-lookup"><span data-stu-id="2fe89-118">name</span></span>|<span data-ttu-id="2fe89-119">Jedinečný řetězec, který obsahuje název konfigurace chování.</span><span class="sxs-lookup"><span data-stu-id="2fe89-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="2fe89-120">Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element.</span><span class="sxs-lookup"><span data-stu-id="2fe89-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fe89-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2fe89-121">Child Elements</span></span>  
  
|<span data-ttu-id="2fe89-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="2fe89-122">Element</span></span>|<span data-ttu-id="2fe89-123">Popis</span><span class="sxs-lookup"><span data-stu-id="2fe89-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fe89-124">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="2fe89-124">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="2fe89-125">Zpracování, která umožňuje služba pracovního postupu ke zpracování zpráv mimo pořadí příjmu chování služby, který povoluje službu, chcete-li použít do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2fe89-125">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="2fe89-126">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="2fe89-126">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="2fe89-127">Chování služby, které umožňuje službě využívat sledování ETW pomocí <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="2fe89-127">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="2fe89-128">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="2fe89-128">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="2fe89-129">Chování služby, které umožňuje přizpůsobení úrovní sdílení mezipaměti, nastavení mezipaměti objektu pro vytváření kanálu a nastavení mezipaměti kanálu pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí aktivit odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="2fe89-129">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="2fe89-130">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="2fe89-130">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="2fe89-131">Chování služby, které umožňuje nakonfigurovat <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci, která podporuje informace o stavu pro instance služby pracovního postupu do databáze SQL Server 2005 nebo SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="2fe89-131">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="2fe89-132">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="2fe89-132">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="2fe89-133">Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.</span><span class="sxs-lookup"><span data-stu-id="2fe89-133">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="2fe89-134">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="2fe89-134">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="2fe89-135">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="2fe89-135">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="2fe89-136">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="2fe89-136">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="2fe89-137">Chování služby, který umožňuje určit akci, která má provést při dojde k neošetřené výjimce v rámci pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="2fe89-137">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2fe89-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2fe89-138">Parent Elements</span></span>  
  
|<span data-ttu-id="2fe89-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="2fe89-139">Element</span></span>|<span data-ttu-id="2fe89-140">Popis</span><span class="sxs-lookup"><span data-stu-id="2fe89-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fe89-141">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2fe89-141">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="2fe89-142">Kolekce elementů chování služby.</span><span class="sxs-lookup"><span data-stu-id="2fe89-142">A collection of service behavior elements.</span></span>|
