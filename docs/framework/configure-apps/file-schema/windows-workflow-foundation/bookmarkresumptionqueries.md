---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 186990577ec4eedc7cae3710c455816c3162fc94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109406"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="78134-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="78134-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="78134-102">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="78134-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="78134-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="78134-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="78134-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="78134-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="78134-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="78134-105">\<system.serviceModel></span></span>  
<span data-ttu-id="78134-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="78134-106">\<tracking></span></span>  
<span data-ttu-id="78134-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="78134-107">\<trackingProfile></span></span>  
<span data-ttu-id="78134-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="78134-108">\<workflow></span></span>  
<span data-ttu-id="78134-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="78134-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="78134-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="78134-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78134-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78134-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78134-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="78134-112">Attributes and Elements</span></span>  
 <span data-ttu-id="78134-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="78134-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78134-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="78134-114">Attributes</span></span>  
 <span data-ttu-id="78134-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="78134-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="78134-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="78134-116">Child Elements</span></span>  
  
|<span data-ttu-id="78134-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="78134-117">Element</span></span>|<span data-ttu-id="78134-118">Popis</span><span class="sxs-lookup"><span data-stu-id="78134-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78134-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="78134-119">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="78134-120">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="78134-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="78134-121">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="78134-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78134-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="78134-122">Parent Elements</span></span>  
  
|<span data-ttu-id="78134-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="78134-123">Element</span></span>|<span data-ttu-id="78134-124">Popis</span><span class="sxs-lookup"><span data-stu-id="78134-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78134-125">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="78134-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="78134-126">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="78134-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78134-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78134-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="78134-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="78134-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="78134-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="78134-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
