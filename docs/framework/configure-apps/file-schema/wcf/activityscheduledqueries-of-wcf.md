---
title: <activityScheduledQueries> služby WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 1c9c292080016d7a2d0014ed07be371c0e247621
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285776"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="daff5-102">\<activityScheduledQueries > služby WCF</span><span class="sxs-lookup"><span data-stu-id="daff5-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="daff5-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="daff5-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="daff5-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="daff5-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="daff5-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="daff5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="daff5-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="daff5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="daff5-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="daff5-107">\<tracking></span></span>  
<span data-ttu-id="daff5-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="daff5-108">\<profiles></span></span>  
<span data-ttu-id="daff5-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="daff5-109">\<trackingProfile></span></span>  
<span data-ttu-id="daff5-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="daff5-110">\<workflow></span></span>  
<span data-ttu-id="daff5-111">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="daff5-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daff5-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="daff5-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="daff5-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="daff5-113">Attributes and elements</span></span>  

<span data-ttu-id="daff5-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="daff5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="daff5-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="daff5-115">Attributes</span></span>  

<span data-ttu-id="daff5-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="daff5-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="daff5-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="daff5-117">Child elements</span></span>  
  
|<span data-ttu-id="daff5-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="daff5-118">Element</span></span>|<span data-ttu-id="daff5-119">Popis</span><span class="sxs-lookup"><span data-stu-id="daff5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="daff5-120">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="daff5-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="daff5-121">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="daff5-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="daff5-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="daff5-122">Parent elements</span></span>  
  
|<span data-ttu-id="daff5-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="daff5-123">Element</span></span>|<span data-ttu-id="daff5-124">Popis</span><span class="sxs-lookup"><span data-stu-id="daff5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="daff5-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="daff5-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="daff5-126">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="daff5-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="daff5-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="daff5-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="daff5-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="daff5-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="daff5-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="daff5-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
