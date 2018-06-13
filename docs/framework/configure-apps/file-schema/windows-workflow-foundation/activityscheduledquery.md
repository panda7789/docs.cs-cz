---
title: '&lt;activityScheduledQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 0822d0ce7dd82ff396596a0ed2431a5f2084ad8f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755367"
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="814cf-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="814cf-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="814cf-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="814cf-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="814cf-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="814cf-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="814cf-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="814cf-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="814cf-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="814cf-106">\<system.serviceModel></span></span>  
<span data-ttu-id="814cf-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="814cf-107">\<tracking></span></span>  
<span data-ttu-id="814cf-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="814cf-108">\<trackingProfile></span></span>  
<span data-ttu-id="814cf-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="814cf-109">\<workflow></span></span>  
<span data-ttu-id="814cf-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="814cf-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="814cf-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="814cf-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="814cf-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="814cf-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="814cf-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="814cf-113">Attributes and Elements</span></span>  
 <span data-ttu-id="814cf-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="814cf-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="814cf-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="814cf-115">Attributes</span></span>  
  
|<span data-ttu-id="814cf-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="814cf-116">Attribute</span></span>|<span data-ttu-id="814cf-117">Popis</span><span class="sxs-lookup"><span data-stu-id="814cf-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="814cf-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="814cf-118">activityName</span></span>|<span data-ttu-id="814cf-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="814cf-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="814cf-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="814cf-120">childActivityName</span></span>|<span data-ttu-id="814cf-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="814cf-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="814cf-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="814cf-122">Child Elements</span></span>  
 <span data-ttu-id="814cf-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="814cf-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="814cf-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="814cf-124">Parent Elements</span></span>  
  
|<span data-ttu-id="814cf-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="814cf-125">Element</span></span>|<span data-ttu-id="814cf-126">Popis</span><span class="sxs-lookup"><span data-stu-id="814cf-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="814cf-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="814cf-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="814cf-128">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="814cf-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="814cf-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="814cf-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="814cf-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="814cf-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="814cf-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="814cf-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
