---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: b2a81a42a17474bdb0124bec6d3c3eeefa514411
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398851"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="cc10f-101">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="cc10f-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="cc10f-102">Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cc10f-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="cc10f-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="cc10f-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="cc10f-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="cc10f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="cc10f-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cc10f-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cc10f-106">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cc10f-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="cc10f-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="cc10f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="cc10f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="cc10f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="cc10f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cc10f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="cc10f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries.md)</span><span class="sxs-lookup"><span data-stu-id="cc10f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)</span></span>\
<span data-ttu-id="cc10f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="cc10f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc10f-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc10f-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc10f-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cc10f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="cc10f-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cc10f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc10f-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="cc10f-115">Attributes</span></span>  
  
|<span data-ttu-id="cc10f-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="cc10f-116">Attribute</span></span>|<span data-ttu-id="cc10f-117">Popis</span><span class="sxs-lookup"><span data-stu-id="cc10f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc10f-118">name</span><span class="sxs-lookup"><span data-stu-id="cc10f-118">name</span></span>|<span data-ttu-id="cc10f-119">Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="cc10f-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc10f-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cc10f-120">Child Elements</span></span>  
 <span data-ttu-id="cc10f-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="cc10f-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc10f-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cc10f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cc10f-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="cc10f-123">Element</span></span>|<span data-ttu-id="cc10f-124">Popis</span><span class="sxs-lookup"><span data-stu-id="cc10f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc10f-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="cc10f-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="cc10f-126">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cc10f-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc10f-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc10f-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cc10f-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="cc10f-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cc10f-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="cc10f-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
