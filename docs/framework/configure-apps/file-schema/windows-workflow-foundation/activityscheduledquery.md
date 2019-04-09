---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: d49c6d933a09dce5d657746358f1a5f716ab639b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143361"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="bb3b6-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="bb3b6-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="bb3b6-102">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="bb3b6-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="bb3b6-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="bb3b6-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="bb3b6-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bb3b6-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="bb3b6-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bb3b6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="bb3b6-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="bb3b6-106">\<tracking></span></span>  
<span data-ttu-id="bb3b6-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="bb3b6-107">\<trackingProfile></span></span>  
<span data-ttu-id="bb3b6-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="bb3b6-108">\<workflow></span></span>  
<span data-ttu-id="bb3b6-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="bb3b6-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="bb3b6-110">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="bb3b6-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb3b6-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb3b6-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb3b6-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bb3b6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bb3b6-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bb3b6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb3b6-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="bb3b6-114">Attributes</span></span>  
  
|<span data-ttu-id="bb3b6-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="bb3b6-115">Attribute</span></span>|<span data-ttu-id="bb3b6-116">Popis</span><span class="sxs-lookup"><span data-stu-id="bb3b6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bb3b6-117">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="bb3b6-117">activityName</span></span>|<span data-ttu-id="bb3b6-118">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="bb3b6-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="bb3b6-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="bb3b6-119">childActivityName</span></span>|<span data-ttu-id="bb3b6-120">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="bb3b6-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb3b6-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bb3b6-121">Child Elements</span></span>  
 <span data-ttu-id="bb3b6-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="bb3b6-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb3b6-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bb3b6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bb3b6-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="bb3b6-124">Element</span></span>|<span data-ttu-id="bb3b6-125">Popis</span><span class="sxs-lookup"><span data-stu-id="bb3b6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb3b6-126">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="bb3b6-126">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="bb3b6-127">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="bb3b6-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb3b6-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb3b6-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bb3b6-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bb3b6-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bb3b6-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="bb3b6-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
