---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: e43ba66e2c3ccfbb723b1eea8ef6774ad3f9f2aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790270"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="29b0f-101">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="29b0f-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="29b0f-102">Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="29b0f-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="29b0f-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="29b0f-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="29b0f-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="29b0f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="29b0f-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="29b0f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="29b0f-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="29b0f-106">\<tracking></span></span>  
<span data-ttu-id="29b0f-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="29b0f-107">\<trackingProfile></span></span>  
<span data-ttu-id="29b0f-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="29b0f-108">\<workflow></span></span>  
<span data-ttu-id="29b0f-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="29b0f-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="29b0f-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="29b0f-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b0f-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29b0f-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29b0f-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="29b0f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="29b0f-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="29b0f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29b0f-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="29b0f-114">Attributes</span></span>  
  
|<span data-ttu-id="29b0f-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="29b0f-115">Attribute</span></span>|<span data-ttu-id="29b0f-116">Popis</span><span class="sxs-lookup"><span data-stu-id="29b0f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29b0f-117">name</span><span class="sxs-lookup"><span data-stu-id="29b0f-117">name</span></span>|<span data-ttu-id="29b0f-118">Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="29b0f-118">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29b0f-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="29b0f-119">Child Elements</span></span>  
 <span data-ttu-id="29b0f-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="29b0f-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29b0f-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="29b0f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="29b0f-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="29b0f-122">Element</span></span>|<span data-ttu-id="29b0f-123">Popis</span><span class="sxs-lookup"><span data-stu-id="29b0f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29b0f-124">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="29b0f-124">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="29b0f-125">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="29b0f-125">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29b0f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29b0f-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="29b0f-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="29b0f-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="29b0f-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="29b0f-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
