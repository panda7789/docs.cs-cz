---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 89de9ef10449fbae78a8c5b558101a2cf6477b07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945525"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="97be5-101">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="97be5-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="97be5-102">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="97be5-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="97be5-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="97be5-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="97be5-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="97be5-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="97be5-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="97be5-105">\<system.serviceModel></span></span>  
<span data-ttu-id="97be5-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="97be5-106">\<tracking></span></span>  
<span data-ttu-id="97be5-107">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="97be5-107">\<trackingProfile></span></span>  
<span data-ttu-id="97be5-108">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="97be5-108">\<workflow></span></span>  
<span data-ttu-id="97be5-109">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="97be5-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97be5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97be5-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97be5-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="97be5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="97be5-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="97be5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97be5-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="97be5-113">Attributes</span></span>  
 <span data-ttu-id="97be5-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="97be5-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="97be5-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="97be5-115">Child Elements</span></span>  
  
|<span data-ttu-id="97be5-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="97be5-116">Element</span></span>|<span data-ttu-id="97be5-117">Popis</span><span class="sxs-lookup"><span data-stu-id="97be5-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97be5-118">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="97be5-118">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="97be5-119">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="97be5-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97be5-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="97be5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="97be5-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="97be5-121">Element</span></span>|<span data-ttu-id="97be5-122">Popis</span><span class="sxs-lookup"><span data-stu-id="97be5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97be5-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="97be5-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="97be5-124">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="97be5-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97be5-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97be5-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="97be5-126">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="97be5-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="97be5-127">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="97be5-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
