---
title: <system.serviceModel> of workflow
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 005a274df9e9ab99227a3748b7a25c9d465d020f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768859"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="8d76f-102">\<system.serviceModel> of workflow</span><span class="sxs-lookup"><span data-stu-id="8d76f-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="8d76f-103">Tento oddíl konfigurace obsahuje všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8d76f-103">This configuration section contains all the workflow configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d76f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d76f-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d76f-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8d76f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8d76f-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8d76f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d76f-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="8d76f-107">Attributes</span></span>  
 <span data-ttu-id="8d76f-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="8d76f-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d76f-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8d76f-109">Child Elements</span></span>  
  
|<span data-ttu-id="8d76f-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="8d76f-110">Element</span></span>|<span data-ttu-id="8d76f-111">Popis</span><span class="sxs-lookup"><span data-stu-id="8d76f-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d76f-112">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="8d76f-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behaviors-of-workflow.md)|<span data-ttu-id="8d76f-113">Tento oddíl definuje **serviceBehaviors** kolekce.</span><span class="sxs-lookup"><span data-stu-id="8d76f-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="8d76f-114">Každý prvek v kolekci definuje chování elementů používané služby.</span><span class="sxs-lookup"><span data-stu-id="8d76f-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="8d76f-115">Každý prvek chování je identifikován jeho jedinečné **název** atribut.</span><span class="sxs-lookup"><span data-stu-id="8d76f-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="8d76f-116">\<tracking></span><span class="sxs-lookup"><span data-stu-id="8d76f-116">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="8d76f-117">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8d76f-117">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="8d76f-118">Další informace v sledování pracovních postupů a jeho konfiguraci najdete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [konfigurace sledování pracovního postupu](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8d76f-118">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d76f-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8d76f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8d76f-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="8d76f-120">Element</span></span>|<span data-ttu-id="8d76f-121">Popis</span><span class="sxs-lookup"><span data-stu-id="8d76f-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d76f-122">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="8d76f-122">\<configuration></span></span>|<span data-ttu-id="8d76f-123">Kořenový element pro všechny elementy konfigurace v konfiguračním souboru .NET.</span><span class="sxs-lookup"><span data-stu-id="8d76f-123">The root element for all configuration elements in a .NET configuration file.</span></span>|
