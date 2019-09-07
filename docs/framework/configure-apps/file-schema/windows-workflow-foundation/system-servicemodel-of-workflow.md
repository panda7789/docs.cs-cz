---
title: < System. serviceModel > pracovního postupu
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 757a7a132a6e765e257097d251a110297c6a40bf
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398604"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="55676-102">\<System. serviceModel > pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="55676-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="55676-103">Tento oddíl konfigurace obsahuje všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="55676-103">This configuration section contains all the workflow configuration elements.</span></span>  

<span data-ttu-id="55676-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="55676-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="55676-105">&nbsp;&nbsp; **\<souborů. > ServiceModel**</span><span class="sxs-lookup"><span data-stu-id="55676-105">&nbsp;&nbsp;**\<system.ServiceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55676-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55676-106">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name="String">  
      <bufferReceive maxPendingMessagesPerChannel="Integer" />  
      <etwTracking profileName="String" />  
     <sendMessageChannelCache allowUnsafeCaching="Boolean" >          
        <channelSettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
        <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
     </sendMessageChannelCache>  
      <sqlWorkflowInstanceStore   
          connectionStringName="String"   
          hostLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionAction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
    </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <tracking>    
     <participants>   
      <add name="String"   
           profileName="String"  
           type="String" />   
     </participants>   
    <trackingProfile name="String">  
      <workflow activityDefinitionId="String">  
          <activityScheduledQueries>  
             <activityScheduledQuery activityName="String"  
                 childActivityName="String"/>  
          </activityScheduledQueries>  
             <activityStateQuery activityName="String" />  
                <arguments>  
                   <argument name="String"/>  
                </arguments>  
                <states>  
                   <state name="String"/>  
                </states>  
                <variables>  
                   <variable name="String"/>  
                </variables>  
          </activityStateQueries>  
          <bookmarkResumptionQueries>  
             <bookmarkResumptionQuery name="String" />  
          </bookmarkResumptionQueries>  
          <cancelRequestQueries>  
             <cancelRequestQuery activityName="String"  
                 childActivityName="String"/>  
          </cancelRequestQueries>  
          <customTrackingQueries>  
             <customTrackingQuery activityName="String"  
                 name="String"/>  
          </customTrackingQueries>  
          <faultPropagationQueries>  
             <faultPropagationQuery activityName="String"  
                 faultHandlerActivityName="String"/>  
          </faultPropagationQueries>  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                 <state name="String"/>  
              </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55676-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="55676-107">Attributes and Elements</span></span>  
 <span data-ttu-id="55676-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="55676-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55676-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="55676-109">Attributes</span></span>  
 <span data-ttu-id="55676-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="55676-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="55676-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="55676-111">Child Elements</span></span>  
  
|<span data-ttu-id="55676-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="55676-112">Element</span></span>|<span data-ttu-id="55676-113">Popis</span><span class="sxs-lookup"><span data-stu-id="55676-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55676-114">\<> chování</span><span class="sxs-lookup"><span data-stu-id="55676-114">\<behaviors></span></span>](behaviors-of-workflow.md)|<span data-ttu-id="55676-115">Tato část definuje kolekci **serviceBehaviors** .</span><span class="sxs-lookup"><span data-stu-id="55676-115">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="55676-116">Každý prvek v kolekci definuje chování elementů používané služby.</span><span class="sxs-lookup"><span data-stu-id="55676-116">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="55676-117">Každý prvek chování je identifikován podle jeho jedinečného atributu **Name** .</span><span class="sxs-lookup"><span data-stu-id="55676-117">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="55676-118">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="55676-118">\<tracking></span></span>](tracking.md)|<span data-ttu-id="55676-119">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="55676-119">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="55676-120">Další informace o sledování pracovního postupu a jeho konfiguraci najdete v tématu [sledování pracovních postupů a trasování](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [Konfigurace sledování pracovního postupu](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="55676-120">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="55676-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="55676-121">Parent Elements</span></span>  
  
|<span data-ttu-id="55676-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="55676-122">Element</span></span>|<span data-ttu-id="55676-123">Popis</span><span class="sxs-lookup"><span data-stu-id="55676-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55676-124">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="55676-124">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="55676-125">Kořenový element pro všechny elementy konfigurace v konfiguračním souboru .NET.</span><span class="sxs-lookup"><span data-stu-id="55676-125">The root element for all configuration elements in a .NET configuration file.</span></span>|
