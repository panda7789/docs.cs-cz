---
title: "&lt;activityScheduledQuery&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3ab5fc54b80d91f89121f9acfd1f041672e11d4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="c5b51-102">&lt;activityScheduledQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="c5b51-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="c5b51-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="c5b51-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="c5b51-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="c5b51-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="c5b51-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c5b51-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="c5b51-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c5b51-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c5b51-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="c5b51-107">\<tracking></span></span>  
<span data-ttu-id="c5b51-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="c5b51-108">\<trackingProfile></span></span>  
<span data-ttu-id="c5b51-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="c5b51-109">\<workflow></span></span>  
<span data-ttu-id="c5b51-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="c5b51-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="c5b51-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="c5b51-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5b51-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5b51-112">Syntax</span></span>  
  
```xml
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5b51-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c5b51-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c5b51-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c5b51-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5b51-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="c5b51-115">Attributes</span></span>  
  
|<span data-ttu-id="c5b51-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="c5b51-116">Attribute</span></span>|<span data-ttu-id="c5b51-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c5b51-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5b51-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="c5b51-118">activityName</span></span>|<span data-ttu-id="c5b51-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="c5b51-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="c5b51-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="c5b51-120">childActivityName</span></span>|<span data-ttu-id="c5b51-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="c5b51-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5b51-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c5b51-122">Child Elements</span></span>  
 <span data-ttu-id="c5b51-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="c5b51-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5b51-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c5b51-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c5b51-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="c5b51-125">Element</span></span>|<span data-ttu-id="c5b51-126">Popis</span><span class="sxs-lookup"><span data-stu-id="c5b51-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5b51-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="c5b51-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="c5b51-128">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="c5b51-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5b51-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5b51-129">See Also</span></span>  
 <span data-ttu-id="c5b51-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span><span class="sxs-lookup"><span data-stu-id="c5b51-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span></span>     
 <span data-ttu-id="c5b51-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="c5b51-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="c5b51-132">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="c5b51-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c5b51-133">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="c5b51-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
