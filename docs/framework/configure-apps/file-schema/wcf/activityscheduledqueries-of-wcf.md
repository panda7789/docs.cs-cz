---
title: '&lt;activityScheduledQueries&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: d6bc2360ccdeebe291de495e6ee5c7e22f26590a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145572"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="f1f5c-102">&lt;activityScheduledQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="f1f5c-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="f1f5c-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="f1f5c-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="f1f5c-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="f1f5c-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="f1f5c-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f1f5c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f1f5c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f1f5c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f1f5c-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="f1f5c-107">\<tracking></span></span>  
<span data-ttu-id="f1f5c-108">\<profily ></span><span class="sxs-lookup"><span data-stu-id="f1f5c-108">\<profiles></span></span>  
<span data-ttu-id="f1f5c-109">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f1f5c-109">\<trackingProfile></span></span>  
<span data-ttu-id="f1f5c-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="f1f5c-110">\<workflow></span></span>  
<span data-ttu-id="f1f5c-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="f1f5c-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1f5c-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1f5c-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1f5c-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f1f5c-113">Attributes and elements</span></span>  

<span data-ttu-id="f1f5c-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f1f5c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1f5c-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="f1f5c-115">Attributes</span></span>  

<span data-ttu-id="f1f5c-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="f1f5c-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f1f5c-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="f1f5c-117">Child elements</span></span>  
  
|<span data-ttu-id="f1f5c-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1f5c-118">Element</span></span>|<span data-ttu-id="f1f5c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f1f5c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1f5c-120">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="f1f5c-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="f1f5c-121">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="f1f5c-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1f5c-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="f1f5c-122">Parent elements</span></span>  
  
|<span data-ttu-id="f1f5c-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1f5c-123">Element</span></span>|<span data-ttu-id="f1f5c-124">Popis</span><span class="sxs-lookup"><span data-stu-id="f1f5c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1f5c-125">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="f1f5c-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f1f5c-126">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f1f5c-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1f5c-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1f5c-127">See also</span></span>  

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="f1f5c-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="f1f5c-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f1f5c-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="f1f5c-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
