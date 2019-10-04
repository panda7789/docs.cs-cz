---
title: '@no__t – 0 služby WCF'
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834008"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="a5423-102">@no__t 0bookmarkResumptionQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="a5423-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="a5423-103">Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a5423-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="a5423-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="a5423-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="a5423-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a5423-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="a5423-106">[ **\<configuration >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5423-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a5423-107">&nbsp; @ no__t-1[ **\<system. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a5423-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a5423-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<tracking >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a5423-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="a5423-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<profiles >** </span><span class="sxs-lookup"><span data-stu-id="a5423-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="a5423-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0trackingProfile >** ](trackingprofile-of-wcf.md)1</span><span class="sxs-lookup"><span data-stu-id="a5423-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\</span></span>
<span data-ttu-id="a5423-111">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2workflow >** ](workflow-of-wcf.md)3</span><span class="sxs-lookup"><span data-stu-id="a5423-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\</span></span>
<span data-ttu-id="a5423-112">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 @ no__t-10 @ no__t-11[ **&nbsp;4bookmarkResumptionQueries >** ](bookmarkresumptionqueries-of-wcf.md)5</span><span class="sxs-lookup"><span data-stu-id="a5423-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)\</span></span>
<span data-ttu-id="a5423-113">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 @ no__t-10 @ no__t-11 @ no__t-12 @ no__t-13 **&nbsp;5bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="a5423-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5423-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5423-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5423-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a5423-115">Attributes and elements</span></span>

<span data-ttu-id="a5423-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a5423-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5423-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="a5423-117">Attributes</span></span>  
  
|<span data-ttu-id="a5423-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="a5423-118">Attribute</span></span>|<span data-ttu-id="a5423-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a5423-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="a5423-120">Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="a5423-120">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5423-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="a5423-121">Child elements</span></span>

<span data-ttu-id="a5423-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="a5423-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="a5423-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="a5423-123">Parent elements</span></span>  
  
|<span data-ttu-id="a5423-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="a5423-124">Element</span></span>|<span data-ttu-id="a5423-125">Popis</span><span class="sxs-lookup"><span data-stu-id="a5423-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5423-126">@no__t – 1bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="a5423-126">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="a5423-127">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a5423-127">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5423-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5423-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a5423-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a5423-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a5423-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="a5423-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
