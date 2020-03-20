---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 6901244009956a499458858bf73f8fd83ec52e13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152258"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="dc98b-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="dc98b-101">\<customTrackingQueries></span></span>
<span data-ttu-id="dc98b-102">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="dc98b-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="dc98b-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="dc98b-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="dc98b-104">Další informace o sledování profilových dotazů naleznete v [tématu Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="dc98b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="dc98b-105">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dc98b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dc98b-106">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="dc98b-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="dc98b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sledování>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="dc98b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="dc98b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="dc98b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="dc98b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="dc98b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="dc98b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span><span class="sxs-lookup"><span data-stu-id="dc98b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc98b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc98b-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc98b-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dc98b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dc98b-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dc98b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc98b-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="dc98b-114">Attributes</span></span>  
 <span data-ttu-id="dc98b-115">Žádné.</span><span class="sxs-lookup"><span data-stu-id="dc98b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dc98b-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dc98b-116">Child Elements</span></span>  
  
|<span data-ttu-id="dc98b-117">Element</span><span class="sxs-lookup"><span data-stu-id="dc98b-117">Element</span></span>|<span data-ttu-id="dc98b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="dc98b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc98b-119">\<vlastní>trackingquery</span><span class="sxs-lookup"><span data-stu-id="dc98b-119">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="dc98b-120">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="dc98b-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc98b-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dc98b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="dc98b-122">Element</span><span class="sxs-lookup"><span data-stu-id="dc98b-122">Element</span></span>|<span data-ttu-id="dc98b-123">Popis</span><span class="sxs-lookup"><span data-stu-id="dc98b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc98b-124">\<>pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="dc98b-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="dc98b-125">Konfigurační prvek, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **activityDefinitionId.**</span><span class="sxs-lookup"><span data-stu-id="dc98b-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc98b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc98b-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dc98b-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="dc98b-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dc98b-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="dc98b-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
