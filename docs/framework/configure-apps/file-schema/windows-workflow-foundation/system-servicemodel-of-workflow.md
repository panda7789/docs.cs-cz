---
title: '&lt;system.serviceModel&gt; pracovního postupu'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 62047d68d559a34ead290cf18f77d032841210b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemservicemodelgt-of-workflow"></a><span data-ttu-id="2f2b4-102">&lt;system.serviceModel&gt; pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2f2b4-102">&lt;system.serviceModel&gt; of workflow</span></span>
<span data-ttu-id="2f2b4-103">Tento oddíl konfigurace obsahuje všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2f2b4-103">This configuration section contains all the workflow configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f2b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f2b4-104">Syntax</span></span>  
  
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
          honstLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionaction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f2b4-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2f2b4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2f2b4-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2f2b4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f2b4-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="2f2b4-107">Attributes</span></span>  
 <span data-ttu-id="2f2b4-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="2f2b4-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2f2b4-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2f2b4-109">Child Elements</span></span>  
  
|<span data-ttu-id="2f2b4-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="2f2b4-110">Element</span></span>|<span data-ttu-id="2f2b4-111">Popis</span><span class="sxs-lookup"><span data-stu-id="2f2b4-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f2b4-112">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2f2b4-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behaviors-of-workflow.md)|<span data-ttu-id="2f2b4-113">Tento oddíl definuje **serviceBehaviors** kolekce.</span><span class="sxs-lookup"><span data-stu-id="2f2b4-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="2f2b4-114">Každý prvek v kolekci definuje chování elementů používané služby.</span><span class="sxs-lookup"><span data-stu-id="2f2b4-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="2f2b4-115">Každý prvek chování je určený podle jeho jedinečné **název** atribut.</span><span class="sxs-lookup"><span data-stu-id="2f2b4-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="2f2b4-116">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="2f2b4-116">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="2f2b4-117">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2f2b4-117">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="2f2b4-118">Další informace v pracovním postupu sledování a jeho konfigurace najdete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [konfigurace sledování pro pracovní postup](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="2f2b4-118">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2f2b4-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2f2b4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2f2b4-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="2f2b4-120">Element</span></span>|<span data-ttu-id="2f2b4-121">Popis</span><span class="sxs-lookup"><span data-stu-id="2f2b4-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f2b4-122">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="2f2b4-122">\<configuration></span></span>|<span data-ttu-id="2f2b4-123">Kořenový element pro všechny elementy konfigurace v konfiguračním souboru .NET.</span><span class="sxs-lookup"><span data-stu-id="2f2b4-123">The root element for all configuration elements in a .NET configuration file.</span></span>|
