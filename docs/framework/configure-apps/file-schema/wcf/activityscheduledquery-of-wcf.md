---
title: <activityScheduledQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 7787ada68210ff832ff3fd1ec93c9d346e4d2eaa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926930"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="1d9ab-102">\<activityScheduledQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="1d9ab-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="1d9ab-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="1d9ab-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="1d9ab-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="1d9ab-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="1d9ab-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="1d9ab-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="1d9ab-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1d9ab-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1d9ab-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="1d9ab-107">\<tracking></span></span>  
<span data-ttu-id="1d9ab-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="1d9ab-108">\<profiles></span></span>  
<span data-ttu-id="1d9ab-109">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="1d9ab-109">\<trackingProfile></span></span>  
<span data-ttu-id="1d9ab-110">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1d9ab-110">\<workflow></span></span>  
<span data-ttu-id="1d9ab-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="1d9ab-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="1d9ab-112">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="1d9ab-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d9ab-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d9ab-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d9ab-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1d9ab-114">Attributes and elements</span></span>  

<span data-ttu-id="1d9ab-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1d9ab-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d9ab-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="1d9ab-116">Attributes</span></span>  
  
|<span data-ttu-id="1d9ab-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="1d9ab-117">Attribute</span></span>|<span data-ttu-id="1d9ab-118">Popis</span><span class="sxs-lookup"><span data-stu-id="1d9ab-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="1d9ab-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="1d9ab-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="1d9ab-120">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="1d9ab-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d9ab-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="1d9ab-121">Child elements</span></span>

<span data-ttu-id="1d9ab-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="1d9ab-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="1d9ab-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="1d9ab-123">Parent elements</span></span>  
  
|<span data-ttu-id="1d9ab-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="1d9ab-124">Element</span></span>|<span data-ttu-id="1d9ab-125">Popis</span><span class="sxs-lookup"><span data-stu-id="1d9ab-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d9ab-126">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="1d9ab-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="1d9ab-127">Kolekce dotazů, které se používají ke sledování aktivity naplánované pro provádění nadřazenou aktivitou.</span><span class="sxs-lookup"><span data-stu-id="1d9ab-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d9ab-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d9ab-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="1d9ab-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1d9ab-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1d9ab-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="1d9ab-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
