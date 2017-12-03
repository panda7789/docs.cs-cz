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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 260b77789df6a03b640895ed158c94bfd1533f9b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="a3f93-102">&lt;activityScheduledQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="a3f93-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="a3f93-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="a3f93-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="a3f93-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="a3f93-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="a3f93-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a3f93-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="a3f93-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a3f93-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a3f93-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="a3f93-107">\<tracking></span></span>  
<span data-ttu-id="a3f93-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="a3f93-108">\<trackingProfile></span></span>  
<span data-ttu-id="a3f93-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="a3f93-109">\<workflow></span></span>  
<span data-ttu-id="a3f93-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="a3f93-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="a3f93-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="a3f93-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3f93-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3f93-112">Syntax</span></span>  
  
```xml
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3f93-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a3f93-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a3f93-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a3f93-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3f93-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="a3f93-115">Attributes</span></span>  
  
|<span data-ttu-id="a3f93-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="a3f93-116">Attribute</span></span>|<span data-ttu-id="a3f93-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a3f93-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3f93-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="a3f93-118">activityName</span></span>|<span data-ttu-id="a3f93-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="a3f93-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="a3f93-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="a3f93-120">childActivityName</span></span>|<span data-ttu-id="a3f93-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="a3f93-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3f93-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a3f93-122">Child Elements</span></span>  
 <span data-ttu-id="a3f93-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="a3f93-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3f93-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a3f93-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a3f93-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="a3f93-125">Element</span></span>|<span data-ttu-id="a3f93-126">Popis</span><span class="sxs-lookup"><span data-stu-id="a3f93-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3f93-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="a3f93-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="a3f93-128">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="a3f93-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3f93-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3f93-129">See Also</span></span>  
 <span data-ttu-id="a3f93-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span><span class="sxs-lookup"><span data-stu-id="a3f93-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span></span>     
 <span data-ttu-id="a3f93-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="a3f93-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="a3f93-132">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="a3f93-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a3f93-133">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="a3f93-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
