---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 89297b3a7d64f4300a735d8512230d441836c634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152304"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="76cc4-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="76cc4-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="76cc4-102">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="76cc4-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="76cc4-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="76cc4-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="76cc4-104">Další informace o sledování profilových dotazů naleznete v [tématu Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="76cc4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="76cc4-105">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="76cc4-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="76cc4-106">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="76cc4-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="76cc4-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sledování>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="76cc4-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="76cc4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="76cc4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="76cc4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="76cc4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="76cc4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span><span class="sxs-lookup"><span data-stu-id="76cc4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76cc4-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76cc4-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76cc4-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="76cc4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="76cc4-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="76cc4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76cc4-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="76cc4-114">Attributes</span></span>  
 <span data-ttu-id="76cc4-115">Žádné.</span><span class="sxs-lookup"><span data-stu-id="76cc4-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="76cc4-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="76cc4-116">Child Elements</span></span>  
  
|<span data-ttu-id="76cc4-117">Element</span><span class="sxs-lookup"><span data-stu-id="76cc4-117">Element</span></span>|<span data-ttu-id="76cc4-118">Popis</span><span class="sxs-lookup"><span data-stu-id="76cc4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76cc4-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="76cc4-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="76cc4-120">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="76cc4-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76cc4-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="76cc4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="76cc4-122">Element</span><span class="sxs-lookup"><span data-stu-id="76cc4-122">Element</span></span>|<span data-ttu-id="76cc4-123">Popis</span><span class="sxs-lookup"><span data-stu-id="76cc4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76cc4-124">\<>pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="76cc4-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="76cc4-125">Konfigurační prvek, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **activityDefinitionId.**</span><span class="sxs-lookup"><span data-stu-id="76cc4-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76cc4-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="76cc4-126">See also</span></span>

- [<span data-ttu-id="76cc4-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="76cc4-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="76cc4-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="76cc4-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
