---
title: <customTrackingQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 204bbb6cf5ebcb30bf92b697885ecbbbd94385e0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855419"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="630af-102">\<customTrackingQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="630af-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="630af-103">Představuje dotaz, který se používá ke sledování událostí, které definujete v aktivitách kódu.</span><span class="sxs-lookup"><span data-stu-id="630af-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="630af-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="630af-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="630af-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="630af-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="630af-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="630af-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="630af-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="630af-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="630af-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="630af-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="630af-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="630af-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="630af-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="630af-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="630af-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="630af-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="630af-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customTrackingQueries >** ](customtrackingqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="630af-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)</span></span>\
<span data-ttu-id="630af-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQuery >**</span><span class="sxs-lookup"><span data-stu-id="630af-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="630af-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="630af-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="630af-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="630af-115">Attributes and elements</span></span>  

<span data-ttu-id="630af-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="630af-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="630af-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="630af-117">Attributes</span></span>  
  
|<span data-ttu-id="630af-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="630af-118">Attribute</span></span>|<span data-ttu-id="630af-119">Popis</span><span class="sxs-lookup"><span data-stu-id="630af-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="630af-120">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="630af-120">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="630af-121">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="630af-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="630af-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="630af-122">Child elements</span></span>

<span data-ttu-id="630af-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="630af-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="630af-124">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="630af-124">Parent elements</span></span>

|<span data-ttu-id="630af-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="630af-125">Element</span></span>|<span data-ttu-id="630af-126">Popis</span><span class="sxs-lookup"><span data-stu-id="630af-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="630af-127">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="630af-127">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="630af-128">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="630af-128">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="630af-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="630af-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="630af-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="630af-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="630af-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="630af-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
