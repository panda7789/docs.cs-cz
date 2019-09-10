---
title: <cancelRequestedQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850060"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="ebc04-102">\<cancelRequestedQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="ebc04-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="ebc04-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="ebc04-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ebc04-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="ebc04-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="ebc04-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ebc04-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="ebc04-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ebc04-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ebc04-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ebc04-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ebc04-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ebc04-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="ebc04-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="ebc04-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="ebc04-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ebc04-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="ebc04-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ebc04-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="ebc04-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cancelRequestedQueries >** ](cancelrequestedqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ebc04-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)</span></span>\
<span data-ttu-id="ebc04-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQuery >**</span><span class="sxs-lookup"><span data-stu-id="ebc04-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="ebc04-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebc04-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebc04-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ebc04-115">Attributes and elements</span></span>

<span data-ttu-id="ebc04-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ebc04-116">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ebc04-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="ebc04-117">Attributes</span></span>  
  
|<span data-ttu-id="ebc04-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="ebc04-118">Attribute</span></span>|<span data-ttu-id="ebc04-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ebc04-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="ebc04-120">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="ebc04-120">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="ebc04-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="ebc04-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebc04-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="ebc04-122">Child elements</span></span>

<span data-ttu-id="ebc04-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="ebc04-123">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="ebc04-124">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="ebc04-124">Parent elements</span></span>
  
|<span data-ttu-id="ebc04-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="ebc04-125">Element</span></span>|<span data-ttu-id="ebc04-126">Popis</span><span class="sxs-lookup"><span data-stu-id="ebc04-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ebc04-127">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="ebc04-127">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="ebc04-128">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="ebc04-128">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ebc04-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebc04-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ebc04-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ebc04-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ebc04-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="ebc04-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
