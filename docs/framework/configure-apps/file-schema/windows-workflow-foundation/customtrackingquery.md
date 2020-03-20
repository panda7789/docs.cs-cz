---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152206"
---
# <a name="customtrackingquery"></a><span data-ttu-id="d8913-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="d8913-101">\<customTrackingQuery></span></span>
<span data-ttu-id="d8913-102">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="d8913-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="d8913-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="d8913-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="d8913-104">Další informace o sledování profilových dotazů naleznete v [tématu Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d8913-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d8913-105">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d8913-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d8913-106">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d8913-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="d8913-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sledování>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="d8913-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="d8913-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="d8913-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="d8913-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d8913-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="d8913-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span><span class="sxs-lookup"><span data-stu-id="d8913-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span></span>\
<span data-ttu-id="d8913-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<vlastní>trackingquery**</span><span class="sxs-lookup"><span data-stu-id="d8913-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8913-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8913-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8913-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d8913-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d8913-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d8913-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8913-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="d8913-115">Attributes</span></span>  
  
|<span data-ttu-id="d8913-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="d8913-116">Attribute</span></span>|<span data-ttu-id="d8913-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d8913-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8913-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="d8913-118">activityName</span></span>|<span data-ttu-id="d8913-119">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="d8913-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="d8913-120">jméno</span><span class="sxs-lookup"><span data-stu-id="d8913-120">name</span></span>|<span data-ttu-id="d8913-121">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="d8913-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8913-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d8913-122">Child Elements</span></span>  
 <span data-ttu-id="d8913-123">Žádné.</span><span class="sxs-lookup"><span data-stu-id="d8913-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8913-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d8913-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d8913-125">Element</span><span class="sxs-lookup"><span data-stu-id="d8913-125">Element</span></span>|<span data-ttu-id="d8913-126">Popis</span><span class="sxs-lookup"><span data-stu-id="d8913-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8913-127">\<vlastní>trackingquery</span><span class="sxs-lookup"><span data-stu-id="d8913-127">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="d8913-128">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="d8913-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8913-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8913-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d8913-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d8913-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d8913-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="d8913-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
