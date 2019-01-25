---
title: '&lt;activityScheduledQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 0e69c32a7c292fda90828396c402c95e4899600a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687437"
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="ffbe2-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="ffbe2-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="ffbe2-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="ffbe2-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="ffbe2-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="ffbe2-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="ffbe2-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ffbe2-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ffbe2-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ffbe2-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ffbe2-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="ffbe2-107">\<tracking></span></span>  
<span data-ttu-id="ffbe2-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ffbe2-108">\<trackingProfile></span></span>  
<span data-ttu-id="ffbe2-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="ffbe2-109">\<workflow></span></span>  
<span data-ttu-id="ffbe2-110">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="ffbe2-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="ffbe2-111">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="ffbe2-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffbe2-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffbe2-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffbe2-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ffbe2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ffbe2-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ffbe2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffbe2-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="ffbe2-115">Attributes</span></span>  
  
|<span data-ttu-id="ffbe2-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="ffbe2-116">Attribute</span></span>|<span data-ttu-id="ffbe2-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ffbe2-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ffbe2-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="ffbe2-118">activityName</span></span>|<span data-ttu-id="ffbe2-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="ffbe2-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="ffbe2-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="ffbe2-120">childActivityName</span></span>|<span data-ttu-id="ffbe2-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="ffbe2-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ffbe2-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ffbe2-122">Child Elements</span></span>  
 <span data-ttu-id="ffbe2-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="ffbe2-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ffbe2-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ffbe2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ffbe2-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="ffbe2-125">Element</span></span>|<span data-ttu-id="ffbe2-126">Popis</span><span class="sxs-lookup"><span data-stu-id="ffbe2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ffbe2-127">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="ffbe2-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="ffbe2-128">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="ffbe2-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffbe2-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffbe2-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ffbe2-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ffbe2-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ffbe2-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="ffbe2-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
