---
title: <activityScheduledQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 83e71e2038377ae4c1c3b17334eece3f30c919f6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920324"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="069c3-102">\<activityScheduledQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="069c3-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="069c3-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="069c3-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="069c3-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="069c3-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="069c3-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="069c3-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="069c3-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="069c3-106">\<system.serviceModel></span></span>  
<span data-ttu-id="069c3-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="069c3-107">\<tracking></span></span>  
<span data-ttu-id="069c3-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="069c3-108">\<profiles></span></span>  
<span data-ttu-id="069c3-109">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="069c3-109">\<trackingProfile></span></span>  
<span data-ttu-id="069c3-110">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="069c3-110">\<workflow></span></span>  
<span data-ttu-id="069c3-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="069c3-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="069c3-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="069c3-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="069c3-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="069c3-113">Attributes and elements</span></span>  

<span data-ttu-id="069c3-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="069c3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="069c3-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="069c3-115">Attributes</span></span>  

<span data-ttu-id="069c3-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="069c3-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="069c3-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="069c3-117">Child elements</span></span>  
  
|<span data-ttu-id="069c3-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="069c3-118">Element</span></span>|<span data-ttu-id="069c3-119">Popis</span><span class="sxs-lookup"><span data-stu-id="069c3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="069c3-120">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="069c3-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="069c3-121">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="069c3-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="069c3-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="069c3-122">Parent elements</span></span>  
  
|<span data-ttu-id="069c3-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="069c3-123">Element</span></span>|<span data-ttu-id="069c3-124">Popis</span><span class="sxs-lookup"><span data-stu-id="069c3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="069c3-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="069c3-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="069c3-126">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="069c3-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="069c3-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="069c3-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="069c3-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="069c3-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="069c3-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="069c3-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
