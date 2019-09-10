---
title: <bookmarkResumptionQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 36d169b78e78692c7b45c75d5d375bddbba1c66f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850102"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="2cf0c-102">\<bookmarkResumptionQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="2cf0c-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="2cf0c-103">Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="2cf0c-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="2cf0c-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="2cf0c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="2cf0c-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2cf0c-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2cf0c-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2cf0c-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2cf0c-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="2cf0c-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="2cf0c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="2cf0c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="2cf0c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="2cf0c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="2cf0c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="2cf0c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="2cf0c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="2cf0c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)</span></span>\
<span data-ttu-id="2cf0c-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="2cf0c-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf0c-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cf0c-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cf0c-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2cf0c-115">Attributes and elements</span></span>

<span data-ttu-id="2cf0c-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cf0c-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="2cf0c-117">Attributes</span></span>  
  
|<span data-ttu-id="2cf0c-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="2cf0c-118">Attribute</span></span>|<span data-ttu-id="2cf0c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="2cf0c-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="2cf0c-120">Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-120">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2cf0c-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="2cf0c-121">Child elements</span></span>

<span data-ttu-id="2cf0c-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="2cf0c-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="2cf0c-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="2cf0c-123">Parent elements</span></span>  
  
|<span data-ttu-id="2cf0c-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="2cf0c-124">Element</span></span>|<span data-ttu-id="2cf0c-125">Popis</span><span class="sxs-lookup"><span data-stu-id="2cf0c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cf0c-126">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="2cf0c-126">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="2cf0c-127">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-127">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2cf0c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2cf0c-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2cf0c-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="2cf0c-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2cf0c-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="2cf0c-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
