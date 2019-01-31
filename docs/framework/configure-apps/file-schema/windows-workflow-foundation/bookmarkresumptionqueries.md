---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 4277df5b4c36fa2f3571ba8441a7eb8aaf6d106a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261542"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="d8842-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="d8842-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="d8842-102">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d8842-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d8842-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="d8842-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="d8842-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d8842-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d8842-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d8842-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d8842-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="d8842-106">\<tracking></span></span>  
<span data-ttu-id="d8842-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d8842-107">\<trackingProfile></span></span>  
<span data-ttu-id="d8842-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="d8842-108">\<workflow></span></span>  
<span data-ttu-id="d8842-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="d8842-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="d8842-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="d8842-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8842-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8842-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8842-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d8842-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d8842-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d8842-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8842-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="d8842-114">Attributes</span></span>  
 <span data-ttu-id="d8842-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="d8842-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8842-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d8842-116">Child Elements</span></span>  
  
|<span data-ttu-id="d8842-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="d8842-117">Element</span></span>|<span data-ttu-id="d8842-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d8842-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8842-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="d8842-119">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="d8842-120">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d8842-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d8842-121">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="d8842-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8842-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d8842-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d8842-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="d8842-123">Element</span></span>|<span data-ttu-id="d8842-124">Popis</span><span class="sxs-lookup"><span data-stu-id="d8842-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8842-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d8842-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="d8842-126">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d8842-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8842-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8842-127">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d8842-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d8842-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d8842-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="d8842-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
