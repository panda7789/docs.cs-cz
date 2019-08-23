---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: dc04405204be7c5484d47b4a3767f846b11abf9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945505"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="7d6b1-101">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="7d6b1-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="7d6b1-102">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="7d6b1-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="7d6b1-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="7d6b1-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="7d6b1-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="7d6b1-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7d6b1-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7d6b1-105">\<system.serviceModel></span></span>  
<span data-ttu-id="7d6b1-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="7d6b1-106">\<tracking></span></span>  
<span data-ttu-id="7d6b1-107">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7d6b1-107">\<trackingProfile></span></span>  
<span data-ttu-id="7d6b1-108">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="7d6b1-108">\<workflow></span></span>  
<span data-ttu-id="7d6b1-109">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="7d6b1-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="7d6b1-110">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="7d6b1-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d6b1-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d6b1-111">Syntax</span></span>  
  
```xml 
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d6b1-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7d6b1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7d6b1-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7d6b1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d6b1-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d6b1-114">Attributes</span></span>  
  
|<span data-ttu-id="7d6b1-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="7d6b1-115">Attribute</span></span>|<span data-ttu-id="7d6b1-116">Popis</span><span class="sxs-lookup"><span data-stu-id="7d6b1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d6b1-117">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="7d6b1-117">activityName</span></span>|<span data-ttu-id="7d6b1-118">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="7d6b1-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="7d6b1-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="7d6b1-119">childActivityName</span></span>|<span data-ttu-id="7d6b1-120">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="7d6b1-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d6b1-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7d6b1-121">Child Elements</span></span>  
 <span data-ttu-id="7d6b1-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="7d6b1-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d6b1-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7d6b1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7d6b1-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d6b1-124">Element</span></span>|<span data-ttu-id="7d6b1-125">Popis</span><span class="sxs-lookup"><span data-stu-id="7d6b1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d6b1-126">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="7d6b1-126">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="7d6b1-127">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="7d6b1-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d6b1-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d6b1-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7d6b1-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="7d6b1-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7d6b1-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="7d6b1-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
