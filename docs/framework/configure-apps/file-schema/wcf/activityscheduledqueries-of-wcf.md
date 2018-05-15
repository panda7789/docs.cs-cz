---
title: '&lt;activityScheduledQueries&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 946406e5513a0fee6793071c397f61bf1fe71c65
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="92635-102">&lt;activityScheduledQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="92635-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="92635-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="92635-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="92635-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="92635-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="92635-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="92635-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="92635-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="92635-106">\<system.serviceModel></span></span>  
<span data-ttu-id="92635-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="92635-107">\<tracking></span></span>  
<span data-ttu-id="92635-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="92635-108">\<trackingProfile></span></span>  
<span data-ttu-id="92635-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="92635-109">\<workflow></span></span>  
<span data-ttu-id="92635-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="92635-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92635-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92635-111">Syntax</span></span>  
  
```xml  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92635-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="92635-112">Attributes and Elements</span></span>  
 <span data-ttu-id="92635-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="92635-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92635-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="92635-114">Attributes</span></span>  
 <span data-ttu-id="92635-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="92635-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="92635-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="92635-116">Child Elements</span></span>  
  
|<span data-ttu-id="92635-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="92635-117">Element</span></span>|<span data-ttu-id="92635-118">Popis</span><span class="sxs-lookup"><span data-stu-id="92635-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92635-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="92635-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="92635-120">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="92635-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92635-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="92635-121">Parent Elements</span></span>  
  
|<span data-ttu-id="92635-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="92635-122">Element</span></span>|<span data-ttu-id="92635-123">Popis</span><span class="sxs-lookup"><span data-stu-id="92635-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92635-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="92635-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="92635-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="92635-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92635-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="92635-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>     
 <xref:System.Activities.Tracking.ActivityScheduledQuery>     
 [<span data-ttu-id="92635-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="92635-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="92635-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="92635-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
