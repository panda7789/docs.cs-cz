---
title: "&lt;activityScheduledQueries&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a857a86d45226e3dd3805a900612f55078c0bf3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="e91a9-102">&lt;activityScheduledQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="e91a9-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="e91a9-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="e91a9-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="e91a9-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="e91a9-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="e91a9-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e91a9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="e91a9-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e91a9-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e91a9-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="e91a9-107">\<tracking></span></span>  
<span data-ttu-id="e91a9-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e91a9-108">\<trackingProfile></span></span>  
<span data-ttu-id="e91a9-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="e91a9-109">\<workflow></span></span>  
<span data-ttu-id="e91a9-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="e91a9-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e91a9-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e91a9-111">Syntax</span></span>  
  
```xml  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e91a9-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e91a9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e91a9-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e91a9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e91a9-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="e91a9-114">Attributes</span></span>  
 <span data-ttu-id="e91a9-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="e91a9-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e91a9-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e91a9-116">Child Elements</span></span>  
  
|<span data-ttu-id="e91a9-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="e91a9-117">Element</span></span>|<span data-ttu-id="e91a9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="e91a9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e91a9-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="e91a9-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="e91a9-120">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="e91a9-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e91a9-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e91a9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e91a9-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="e91a9-122">Element</span></span>|<span data-ttu-id="e91a9-123">Popis</span><span class="sxs-lookup"><span data-stu-id="e91a9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e91a9-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="e91a9-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e91a9-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e91a9-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e91a9-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="e91a9-126">See Also</span></span>  
 <span data-ttu-id="e91a9-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="e91a9-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span></span>     
 <span data-ttu-id="e91a9-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="e91a9-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="e91a9-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e91a9-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e91a9-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="e91a9-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
