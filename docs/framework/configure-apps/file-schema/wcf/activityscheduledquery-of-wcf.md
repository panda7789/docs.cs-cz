---
title: <activityScheduledQuery> služby WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 5087d56092296f8c68b719ec0945993adeb3de0a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272900"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="0060b-102">\<activityScheduledQuery > služby WCF</span><span class="sxs-lookup"><span data-stu-id="0060b-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="0060b-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="0060b-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="0060b-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="0060b-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="0060b-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="0060b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="0060b-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0060b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="0060b-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="0060b-107">\<tracking></span></span>  
<span data-ttu-id="0060b-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="0060b-108">\<profiles></span></span>  
<span data-ttu-id="0060b-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="0060b-109">\<trackingProfile></span></span>  
<span data-ttu-id="0060b-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="0060b-110">\<workflow></span></span>  
<span data-ttu-id="0060b-111">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="0060b-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="0060b-112">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="0060b-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0060b-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0060b-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0060b-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0060b-114">Attributes and elements</span></span>  

<span data-ttu-id="0060b-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0060b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0060b-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="0060b-116">Attributes</span></span>  
  
|<span data-ttu-id="0060b-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="0060b-117">Attribute</span></span>|<span data-ttu-id="0060b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="0060b-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="0060b-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="0060b-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="0060b-120">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="0060b-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0060b-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="0060b-121">Child elements</span></span>

<span data-ttu-id="0060b-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="0060b-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="0060b-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="0060b-123">Parent elements</span></span>  
  
|<span data-ttu-id="0060b-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="0060b-124">Element</span></span>|<span data-ttu-id="0060b-125">Popis</span><span class="sxs-lookup"><span data-stu-id="0060b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0060b-126">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="0060b-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="0060b-127">Kolekce dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="0060b-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0060b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0060b-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="0060b-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="0060b-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0060b-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="0060b-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
