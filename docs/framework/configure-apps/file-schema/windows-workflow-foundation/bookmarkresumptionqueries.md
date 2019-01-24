---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: ae6a81123379ecd0e7fdc72f4e115a462f81eb90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555034"
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="348da-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="348da-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="348da-103">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="348da-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="348da-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="348da-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="348da-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="348da-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="348da-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="348da-106">\<system.serviceModel></span></span>  
<span data-ttu-id="348da-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="348da-107">\<tracking></span></span>  
<span data-ttu-id="348da-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="348da-108">\<trackingProfile></span></span>  
<span data-ttu-id="348da-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="348da-109">\<workflow></span></span>  
<span data-ttu-id="348da-110">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="348da-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="348da-111">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="348da-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="348da-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="348da-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="348da-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="348da-113">Attributes and Elements</span></span>  
 <span data-ttu-id="348da-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="348da-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="348da-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="348da-115">Attributes</span></span>  
 <span data-ttu-id="348da-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="348da-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="348da-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="348da-117">Child Elements</span></span>  
  
|<span data-ttu-id="348da-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="348da-118">Element</span></span>|<span data-ttu-id="348da-119">Popis</span><span class="sxs-lookup"><span data-stu-id="348da-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="348da-120">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="348da-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="348da-121">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="348da-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="348da-122">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="348da-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="348da-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="348da-123">Parent Elements</span></span>  
  
|<span data-ttu-id="348da-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="348da-124">Element</span></span>|<span data-ttu-id="348da-125">Popis</span><span class="sxs-lookup"><span data-stu-id="348da-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="348da-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="348da-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="348da-127">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="348da-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="348da-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="348da-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="348da-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="348da-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="348da-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="348da-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
