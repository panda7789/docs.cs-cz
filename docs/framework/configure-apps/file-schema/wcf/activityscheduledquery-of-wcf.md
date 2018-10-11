---
title: '&lt;activityScheduledQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 9a53d72316dad0178f24e05656a4fb4531b88aec
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087762"
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="26e10-102">&lt;activityScheduledQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="26e10-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="26e10-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="26e10-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="26e10-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="26e10-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="26e10-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="26e10-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="26e10-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="26e10-106">\<system.serviceModel></span></span>  
<span data-ttu-id="26e10-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="26e10-107">\<tracking></span></span>  
<span data-ttu-id="26e10-108">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="26e10-108">\<trackingProfile></span></span>  
<span data-ttu-id="26e10-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="26e10-109">\<workflow></span></span>  
<span data-ttu-id="26e10-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="26e10-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="26e10-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="26e10-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26e10-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26e10-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26e10-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="26e10-113">Attributes and Elements</span></span>  
 <span data-ttu-id="26e10-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="26e10-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26e10-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="26e10-115">Attributes</span></span>  
  
|<span data-ttu-id="26e10-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="26e10-116">Attribute</span></span>|<span data-ttu-id="26e10-117">Popis</span><span class="sxs-lookup"><span data-stu-id="26e10-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26e10-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="26e10-118">activityName</span></span>|<span data-ttu-id="26e10-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="26e10-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="26e10-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="26e10-120">childActivityName</span></span>|<span data-ttu-id="26e10-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="26e10-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26e10-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="26e10-122">Child Elements</span></span>  
 <span data-ttu-id="26e10-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="26e10-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26e10-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="26e10-124">Parent Elements</span></span>  
  
|<span data-ttu-id="26e10-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="26e10-125">Element</span></span>|<span data-ttu-id="26e10-126">Popis</span><span class="sxs-lookup"><span data-stu-id="26e10-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26e10-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="26e10-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="26e10-128">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="26e10-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26e10-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="26e10-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>     
 <xref:System.Activities.Tracking.ActivityScheduledQuery>     
 [<span data-ttu-id="26e10-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="26e10-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="26e10-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="26e10-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
