---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: ad41c1afec0b46a404f8f24882587c1dfeb68a80
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267804"
---
# <a name="activitystatequeries"></a><span data-ttu-id="8fbad-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="8fbad-101">\<activityStateQueries></span></span>
<span data-ttu-id="8fbad-102">Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8fbad-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="8fbad-103">Můžete například sledovat, pokaždé, když dokončí "Odeslat E-Mail" aktivity v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8fbad-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="8fbad-104">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="8fbad-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="8fbad-105">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="8fbad-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="8fbad-106">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8fbad-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="8fbad-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8fbad-107">\<system.serviceModel></span></span>  
<span data-ttu-id="8fbad-108">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="8fbad-108">\<tracking></span></span>  
<span data-ttu-id="8fbad-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8fbad-109">\<trackingProfile></span></span>  
<span data-ttu-id="8fbad-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="8fbad-110">\<workflow></span></span>  
<span data-ttu-id="8fbad-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="8fbad-111">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fbad-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fbad-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fbad-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8fbad-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8fbad-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8fbad-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fbad-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="8fbad-115">Attributes</span></span>  
 <span data-ttu-id="8fbad-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="8fbad-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8fbad-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8fbad-117">Child Elements</span></span>  
  
|<span data-ttu-id="8fbad-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="8fbad-118">Element</span></span>|<span data-ttu-id="8fbad-119">Popis</span><span class="sxs-lookup"><span data-stu-id="8fbad-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fbad-120">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="8fbad-120">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="8fbad-121">Dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="8fbad-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="8fbad-122">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="8fbad-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8fbad-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8fbad-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8fbad-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="8fbad-124">Element</span></span>|<span data-ttu-id="8fbad-125">Popis</span><span class="sxs-lookup"><span data-stu-id="8fbad-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fbad-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="8fbad-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="8fbad-127">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8fbad-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fbad-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fbad-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8fbad-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="8fbad-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8fbad-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="8fbad-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
