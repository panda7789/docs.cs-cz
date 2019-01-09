---
title: '&lt;activityScheduledQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: fd7830bc178de0693f0632cea3b390d792408ec1
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147873"
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="5aa5f-102">&lt;activityScheduledQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="5aa5f-102">&lt;activityScheduledQuery&gt; of WCF</span></span>

<span data-ttu-id="5aa5f-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="5aa5f-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="5aa5f-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="5aa5f-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="5aa5f-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5aa5f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="5aa5f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5aa5f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="5aa5f-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="5aa5f-107">\<tracking></span></span>  
<span data-ttu-id="5aa5f-108">\<profily ></span><span class="sxs-lookup"><span data-stu-id="5aa5f-108">\<profiles></span></span>  
<span data-ttu-id="5aa5f-109">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="5aa5f-109">\<trackingProfile></span></span>  
<span data-ttu-id="5aa5f-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="5aa5f-110">\<workflow></span></span>  
<span data-ttu-id="5aa5f-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="5aa5f-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="5aa5f-112">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="5aa5f-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aa5f-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5aa5f-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5aa5f-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5aa5f-114">Attributes and elements</span></span>  

<span data-ttu-id="5aa5f-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5aa5f-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5aa5f-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="5aa5f-116">Attributes</span></span>  
  
|<span data-ttu-id="5aa5f-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="5aa5f-117">Attribute</span></span>|<span data-ttu-id="5aa5f-118">Popis</span><span class="sxs-lookup"><span data-stu-id="5aa5f-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="5aa5f-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="5aa5f-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="5aa5f-120">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="5aa5f-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5aa5f-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="5aa5f-121">Child elements</span></span>

<span data-ttu-id="5aa5f-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="5aa5f-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="5aa5f-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="5aa5f-123">Parent elements</span></span>  
  
|<span data-ttu-id="5aa5f-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="5aa5f-124">Element</span></span>|<span data-ttu-id="5aa5f-125">Popis</span><span class="sxs-lookup"><span data-stu-id="5aa5f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5aa5f-126">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="5aa5f-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="5aa5f-127">Kolekce dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="5aa5f-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5aa5f-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5aa5f-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="5aa5f-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5aa5f-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5aa5f-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="5aa5f-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
