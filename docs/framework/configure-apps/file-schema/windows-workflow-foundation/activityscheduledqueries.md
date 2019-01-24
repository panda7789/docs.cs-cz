---
title: '&lt;activityScheduledQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 2285dfae84f078483c03d85801051e29b79e74c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561839"
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="aba03-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="aba03-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="aba03-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="aba03-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="aba03-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="aba03-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="aba03-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="aba03-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="aba03-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="aba03-106">\<system.serviceModel></span></span>  
<span data-ttu-id="aba03-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="aba03-107">\<tracking></span></span>  
<span data-ttu-id="aba03-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="aba03-108">\<trackingProfile></span></span>  
<span data-ttu-id="aba03-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="aba03-109">\<workflow></span></span>  
<span data-ttu-id="aba03-110">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="aba03-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aba03-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aba03-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aba03-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aba03-112">Attributes and Elements</span></span>  
 <span data-ttu-id="aba03-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aba03-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aba03-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="aba03-114">Attributes</span></span>  
 <span data-ttu-id="aba03-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="aba03-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aba03-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aba03-116">Child Elements</span></span>  
  
|<span data-ttu-id="aba03-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="aba03-117">Element</span></span>|<span data-ttu-id="aba03-118">Popis</span><span class="sxs-lookup"><span data-stu-id="aba03-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aba03-119">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="aba03-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="aba03-120">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="aba03-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aba03-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aba03-121">Parent Elements</span></span>  
  
|<span data-ttu-id="aba03-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="aba03-122">Element</span></span>|<span data-ttu-id="aba03-123">Popis</span><span class="sxs-lookup"><span data-stu-id="aba03-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aba03-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="aba03-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="aba03-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="aba03-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aba03-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aba03-126">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="aba03-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="aba03-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="aba03-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="aba03-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
