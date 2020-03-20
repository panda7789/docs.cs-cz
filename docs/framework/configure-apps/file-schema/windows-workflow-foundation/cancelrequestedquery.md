---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e6840ce647625c36356cccd4651f17de32777e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152284"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="c0c80-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="c0c80-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="c0c80-102">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="c0c80-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c0c80-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="c0c80-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="c0c80-104">Další informace o sledování profilových dotazů naleznete v [tématu Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c0c80-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c0c80-105">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0c80-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c0c80-106">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c0c80-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="c0c80-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sledování>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="c0c80-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="c0c80-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="c0c80-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="c0c80-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c0c80-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="c0c80-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)</span><span class="sxs-lookup"><span data-stu-id="c0c80-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)</span></span>\
<span data-ttu-id="c0c80-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span><span class="sxs-lookup"><span data-stu-id="c0c80-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0c80-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0c80-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0c80-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c0c80-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c0c80-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c0c80-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0c80-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="c0c80-115">Attributes</span></span>  
  
|<span data-ttu-id="c0c80-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="c0c80-116">Attribute</span></span>|<span data-ttu-id="c0c80-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c0c80-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0c80-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="c0c80-118">activityName</span></span>|<span data-ttu-id="c0c80-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="c0c80-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="c0c80-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="c0c80-120">childActivityName</span></span>|<span data-ttu-id="c0c80-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="c0c80-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0c80-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c0c80-122">Child Elements</span></span>  
 <span data-ttu-id="c0c80-123">Žádné.</span><span class="sxs-lookup"><span data-stu-id="c0c80-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0c80-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c0c80-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c0c80-125">Element</span><span class="sxs-lookup"><span data-stu-id="c0c80-125">Element</span></span>|<span data-ttu-id="c0c80-126">Popis</span><span class="sxs-lookup"><span data-stu-id="c0c80-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0c80-127">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="c0c80-127">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="c0c80-128">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="c0c80-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c0c80-129">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="c0c80-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0c80-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0c80-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c0c80-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c0c80-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c0c80-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="c0c80-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
