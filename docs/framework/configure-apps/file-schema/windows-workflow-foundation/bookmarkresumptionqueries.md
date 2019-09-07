---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 563e0cbd3f50887e1c9e3d47a3c9502acc13b2c9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398857"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="4a781-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="4a781-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="4a781-102">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4a781-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="4a781-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="4a781-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="4a781-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="4a781-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4a781-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4a781-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4a781-106">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4a781-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="4a781-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="4a781-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="4a781-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="4a781-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="4a781-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4a781-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="4a781-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQueries >**</span><span class="sxs-lookup"><span data-stu-id="4a781-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="4a781-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a781-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a781-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4a781-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4a781-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4a781-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a781-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="4a781-114">Attributes</span></span>  
 <span data-ttu-id="4a781-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="4a781-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4a781-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4a781-116">Child Elements</span></span>  
  
|<span data-ttu-id="4a781-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="4a781-117">Element</span></span>|<span data-ttu-id="4a781-118">Popis</span><span class="sxs-lookup"><span data-stu-id="4a781-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a781-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="4a781-119">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery.md)|<span data-ttu-id="4a781-120">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4a781-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="4a781-121">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="4a781-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a781-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4a781-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4a781-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="4a781-123">Element</span></span>|<span data-ttu-id="4a781-124">Popis</span><span class="sxs-lookup"><span data-stu-id="4a781-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a781-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="4a781-125">\<workflow></span></span>](workflow.md)|<span data-ttu-id="4a781-126">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="4a781-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a781-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a781-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4a781-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="4a781-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4a781-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="4a781-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
