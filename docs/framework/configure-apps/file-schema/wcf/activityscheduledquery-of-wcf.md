---
title: '&lt;activityScheduledQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 4efd6ba13e8a54d3338c25b077477d4abdbe9ab5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="7eaf5-102">&lt;activityScheduledQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="7eaf5-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="7eaf5-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="7eaf5-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="7eaf5-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="7eaf5-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="7eaf5-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7eaf5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="7eaf5-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7eaf5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7eaf5-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="7eaf5-107">\<tracking></span></span>  
<span data-ttu-id="7eaf5-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7eaf5-108">\<trackingProfile></span></span>  
<span data-ttu-id="7eaf5-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="7eaf5-109">\<workflow></span></span>  
<span data-ttu-id="7eaf5-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="7eaf5-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="7eaf5-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="7eaf5-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eaf5-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eaf5-112">Syntax</span></span>  
  
```xml
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7eaf5-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7eaf5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7eaf5-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7eaf5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7eaf5-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="7eaf5-115">Attributes</span></span>  
  
|<span data-ttu-id="7eaf5-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="7eaf5-116">Attribute</span></span>|<span data-ttu-id="7eaf5-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7eaf5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7eaf5-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="7eaf5-118">activityName</span></span>|<span data-ttu-id="7eaf5-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="7eaf5-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="7eaf5-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="7eaf5-120">childActivityName</span></span>|<span data-ttu-id="7eaf5-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="7eaf5-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7eaf5-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7eaf5-122">Child Elements</span></span>  
 <span data-ttu-id="7eaf5-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="7eaf5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7eaf5-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7eaf5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7eaf5-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="7eaf5-125">Element</span></span>|<span data-ttu-id="7eaf5-126">Popis</span><span class="sxs-lookup"><span data-stu-id="7eaf5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7eaf5-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="7eaf5-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="7eaf5-128">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="7eaf5-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7eaf5-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="7eaf5-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>     
 <xref:System.Activities.Tracking.ActivityScheduledQuery>     
 [<span data-ttu-id="7eaf5-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="7eaf5-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="7eaf5-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="7eaf5-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
