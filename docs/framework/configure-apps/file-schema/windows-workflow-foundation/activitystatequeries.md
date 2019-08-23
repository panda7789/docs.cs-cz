---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 6e91078a24a950c6de027d57e3883e38f19447d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945453"
---
# <a name="activitystatequeries"></a><span data-ttu-id="be734-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="be734-101">\<activityStateQueries></span></span>
<span data-ttu-id="be734-102">Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="be734-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="be734-103">Například můžete chtít sledovat pokaždé, když se aktivita odeslat E-Mail dokončí v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="be734-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="be734-104">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="be734-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="be734-105">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="be734-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="be734-106">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="be734-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="be734-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="be734-107">\<system.serviceModel></span></span>  
<span data-ttu-id="be734-108">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="be734-108">\<tracking></span></span>  
<span data-ttu-id="be734-109">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="be734-109">\<trackingProfile></span></span>  
<span data-ttu-id="be734-110">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="be734-110">\<workflow></span></span>  
<span data-ttu-id="be734-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="be734-111">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be734-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be734-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be734-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="be734-113">Attributes and Elements</span></span>  
 <span data-ttu-id="be734-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="be734-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be734-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="be734-115">Attributes</span></span>  
 <span data-ttu-id="be734-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="be734-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="be734-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="be734-117">Child Elements</span></span>  
  
|<span data-ttu-id="be734-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="be734-118">Element</span></span>|<span data-ttu-id="be734-119">Popis</span><span class="sxs-lookup"><span data-stu-id="be734-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be734-120">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="be734-120">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="be734-121">Dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="be734-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="be734-122">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="be734-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be734-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="be734-123">Parent Elements</span></span>  
  
|<span data-ttu-id="be734-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="be734-124">Element</span></span>|<span data-ttu-id="be734-125">Popis</span><span class="sxs-lookup"><span data-stu-id="be734-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be734-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="be734-126">\<workflow></span></span>](workflow.md)|<span data-ttu-id="be734-127">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="be734-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be734-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be734-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="be734-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="be734-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="be734-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="be734-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
