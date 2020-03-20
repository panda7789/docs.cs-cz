---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 09cbc43ae4db82dc80e6985131f8d6cc0c24b2ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152408"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="ed2eb-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="ed2eb-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="ed2eb-102">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="ed2eb-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="ed2eb-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="ed2eb-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="ed2eb-104">Další informace o sledování profilových dotazů naleznete v [tématu Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ed2eb-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ed2eb-105">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed2eb-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ed2eb-106">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ed2eb-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="ed2eb-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sledování>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="ed2eb-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="ed2eb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="ed2eb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="ed2eb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ed2eb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="ed2eb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)</span><span class="sxs-lookup"><span data-stu-id="ed2eb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)</span></span>\
<span data-ttu-id="ed2eb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span><span class="sxs-lookup"><span data-stu-id="ed2eb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed2eb-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed2eb-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed2eb-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ed2eb-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ed2eb-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ed2eb-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed2eb-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="ed2eb-115">Attributes</span></span>  
  
|<span data-ttu-id="ed2eb-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="ed2eb-116">Attribute</span></span>|<span data-ttu-id="ed2eb-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ed2eb-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed2eb-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="ed2eb-118">activityName</span></span>|<span data-ttu-id="ed2eb-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="ed2eb-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="ed2eb-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="ed2eb-120">childActivityName</span></span>|<span data-ttu-id="ed2eb-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="ed2eb-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed2eb-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ed2eb-122">Child Elements</span></span>  
 <span data-ttu-id="ed2eb-123">Žádné.</span><span class="sxs-lookup"><span data-stu-id="ed2eb-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed2eb-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ed2eb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ed2eb-125">Element</span><span class="sxs-lookup"><span data-stu-id="ed2eb-125">Element</span></span>|<span data-ttu-id="ed2eb-126">Popis</span><span class="sxs-lookup"><span data-stu-id="ed2eb-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed2eb-127">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="ed2eb-127">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="ed2eb-128">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="ed2eb-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed2eb-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed2eb-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ed2eb-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ed2eb-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ed2eb-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="ed2eb-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
