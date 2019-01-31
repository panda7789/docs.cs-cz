---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: e6891144d613623b199e7279aa091d4d7cbe4445
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284554"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="9984d-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="9984d-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="9984d-102">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="9984d-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="9984d-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="9984d-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="9984d-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9984d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9984d-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9984d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9984d-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="9984d-106">\<tracking></span></span>  
<span data-ttu-id="9984d-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9984d-107">\<trackingProfile></span></span>  
<span data-ttu-id="9984d-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9984d-108">\<workflow></span></span>  
<span data-ttu-id="9984d-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="9984d-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9984d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9984d-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9984d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9984d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9984d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9984d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9984d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="9984d-113">Attributes</span></span>  
 <span data-ttu-id="9984d-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="9984d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9984d-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9984d-115">Child Elements</span></span>  
  
|<span data-ttu-id="9984d-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="9984d-116">Element</span></span>|<span data-ttu-id="9984d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="9984d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9984d-118">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="9984d-118">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="9984d-119">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="9984d-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9984d-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9984d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9984d-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="9984d-121">Element</span></span>|<span data-ttu-id="9984d-122">Popis</span><span class="sxs-lookup"><span data-stu-id="9984d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9984d-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="9984d-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9984d-124">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9984d-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9984d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9984d-125">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9984d-126">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9984d-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9984d-127">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="9984d-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
