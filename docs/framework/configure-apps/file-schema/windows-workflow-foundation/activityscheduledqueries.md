---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 763754b95a7f39c7f35e05df28589b69352168e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152421"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="dd559-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="dd559-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="dd559-102">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="dd559-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="dd559-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="dd559-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="dd559-104">Další informace o sledování profilových dotazů naleznete v [tématu Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="dd559-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="dd559-105">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dd559-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dd559-106">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="dd559-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="dd559-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sledování>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="dd559-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="dd559-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="dd559-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="dd559-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="dd559-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="dd559-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span><span class="sxs-lookup"><span data-stu-id="dd559-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd559-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd559-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd559-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dd559-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dd559-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dd559-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd559-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="dd559-114">Attributes</span></span>  
 <span data-ttu-id="dd559-115">Žádné.</span><span class="sxs-lookup"><span data-stu-id="dd559-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dd559-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dd559-116">Child Elements</span></span>  
  
|<span data-ttu-id="dd559-117">Element</span><span class="sxs-lookup"><span data-stu-id="dd559-117">Element</span></span>|<span data-ttu-id="dd559-118">Popis</span><span class="sxs-lookup"><span data-stu-id="dd559-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd559-119">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="dd559-119">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="dd559-120">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="dd559-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd559-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dd559-121">Parent Elements</span></span>  
  
|<span data-ttu-id="dd559-122">Element</span><span class="sxs-lookup"><span data-stu-id="dd559-122">Element</span></span>|<span data-ttu-id="dd559-123">Popis</span><span class="sxs-lookup"><span data-stu-id="dd559-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd559-124">\<>pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="dd559-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="dd559-125">Konfigurační prvek, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **activityDefinitionId.**</span><span class="sxs-lookup"><span data-stu-id="dd559-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd559-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd559-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dd559-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="dd559-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dd559-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="dd559-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
