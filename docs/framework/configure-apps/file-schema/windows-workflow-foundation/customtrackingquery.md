---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 695fccf88ac0d8a672e710ccc632ea58dd2fc693
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398772"
---
# <a name="customtrackingquery"></a><span data-ttu-id="ec33d-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="ec33d-101">\<customTrackingQuery></span></span>
<span data-ttu-id="ec33d-102">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="ec33d-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ec33d-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="ec33d-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="ec33d-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="ec33d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ec33d-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ec33d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ec33d-106">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ec33d-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="ec33d-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="ec33d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="ec33d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="ec33d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="ec33d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ec33d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="ec33d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customTrackingQueries >** ](customtrackingqueries.md)</span><span class="sxs-lookup"><span data-stu-id="ec33d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span></span>\
<span data-ttu-id="ec33d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQuery >**</span><span class="sxs-lookup"><span data-stu-id="ec33d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec33d-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec33d-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec33d-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ec33d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ec33d-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ec33d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec33d-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="ec33d-115">Attributes</span></span>  
  
|<span data-ttu-id="ec33d-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="ec33d-116">Attribute</span></span>|<span data-ttu-id="ec33d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ec33d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec33d-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="ec33d-118">activityName</span></span>|<span data-ttu-id="ec33d-119">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="ec33d-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="ec33d-120">name</span><span class="sxs-lookup"><span data-stu-id="ec33d-120">name</span></span>|<span data-ttu-id="ec33d-121">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="ec33d-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec33d-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ec33d-122">Child Elements</span></span>  
 <span data-ttu-id="ec33d-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="ec33d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec33d-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ec33d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ec33d-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="ec33d-125">Element</span></span>|<span data-ttu-id="ec33d-126">Popis</span><span class="sxs-lookup"><span data-stu-id="ec33d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec33d-127">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="ec33d-127">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="ec33d-128">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="ec33d-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec33d-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec33d-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ec33d-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ec33d-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ec33d-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="ec33d-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
