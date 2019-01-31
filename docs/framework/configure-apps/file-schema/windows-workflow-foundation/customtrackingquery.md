---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 4e525bc4c77649a6c6d70ddb2408b6ecce4a0f09
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263759"
---
# <a name="customtrackingquery"></a><span data-ttu-id="ceabd-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="ceabd-101">\<customTrackingQuery></span></span>
<span data-ttu-id="ceabd-102">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="ceabd-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ceabd-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="ceabd-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="ceabd-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ceabd-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ceabd-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ceabd-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ceabd-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="ceabd-106">\<tracking></span></span>  
<span data-ttu-id="ceabd-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ceabd-107">\<trackingProfile></span></span>  
<span data-ttu-id="ceabd-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="ceabd-108">\<workflow></span></span>  
<span data-ttu-id="ceabd-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="ceabd-109">\<customTrackingQueries></span></span>  
<span data-ttu-id="ceabd-110">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="ceabd-110">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceabd-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ceabd-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ceabd-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ceabd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ceabd-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ceabd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ceabd-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="ceabd-114">Attributes</span></span>  
  
|<span data-ttu-id="ceabd-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="ceabd-115">Attribute</span></span>|<span data-ttu-id="ceabd-116">Popis</span><span class="sxs-lookup"><span data-stu-id="ceabd-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ceabd-117">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="ceabd-117">activityName</span></span>|<span data-ttu-id="ceabd-118">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="ceabd-118">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="ceabd-119">name</span><span class="sxs-lookup"><span data-stu-id="ceabd-119">name</span></span>|<span data-ttu-id="ceabd-120">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="ceabd-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ceabd-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ceabd-121">Child Elements</span></span>  
 <span data-ttu-id="ceabd-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="ceabd-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ceabd-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ceabd-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ceabd-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="ceabd-124">Element</span></span>|<span data-ttu-id="ceabd-125">Popis</span><span class="sxs-lookup"><span data-stu-id="ceabd-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ceabd-126">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="ceabd-126">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="ceabd-127">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="ceabd-127">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ceabd-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ceabd-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ceabd-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ceabd-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ceabd-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="ceabd-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
