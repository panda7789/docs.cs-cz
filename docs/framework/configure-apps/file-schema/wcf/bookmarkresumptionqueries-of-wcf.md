---
title: <bookmarkResumptionQueries> služby WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 4b11543e240b482d52c157083d1184db4f81bb04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673430"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="f3feb-102">\<bookmarkResumptionQueries > služby WCF</span><span class="sxs-lookup"><span data-stu-id="f3feb-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="f3feb-103">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f3feb-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="f3feb-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="f3feb-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="f3feb-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f3feb-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="f3feb-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f3feb-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f3feb-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="f3feb-107">\<tracking></span></span>  
<span data-ttu-id="f3feb-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="f3feb-108">\<profiles></span></span>  
<span data-ttu-id="f3feb-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f3feb-109">\<trackingProfile></span></span>  
<span data-ttu-id="f3feb-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="f3feb-110">\<workflow></span></span>  
<span data-ttu-id="f3feb-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="f3feb-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="f3feb-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="f3feb-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3feb-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3feb-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3feb-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3feb-114">Attributes and elements</span></span>  
  
<span data-ttu-id="f3feb-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3feb-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3feb-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3feb-116">Attributes</span></span>  
  
<span data-ttu-id="f3feb-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3feb-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f3feb-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="f3feb-118">Child elements</span></span>  
  
|<span data-ttu-id="f3feb-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3feb-119">Element</span></span>|<span data-ttu-id="f3feb-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f3feb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3feb-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="f3feb-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="f3feb-122">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f3feb-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="f3feb-123">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="f3feb-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3feb-124">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="f3feb-124">Parent elements</span></span>  
  
|<span data-ttu-id="f3feb-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3feb-125">Element</span></span>|<span data-ttu-id="f3feb-126">Popis</span><span class="sxs-lookup"><span data-stu-id="f3feb-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3feb-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f3feb-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f3feb-128">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f3feb-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3feb-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3feb-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f3feb-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="f3feb-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f3feb-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="f3feb-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
