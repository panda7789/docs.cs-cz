---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 398b018ce407aee0687c95037753f3affa07aa9b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398783"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="03d12-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="03d12-101">\<customTrackingQueries></span></span>
<span data-ttu-id="03d12-102">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="03d12-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="03d12-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="03d12-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="03d12-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="03d12-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="03d12-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="03d12-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="03d12-106">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="03d12-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="03d12-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="03d12-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="03d12-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="03d12-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="03d12-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="03d12-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="03d12-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQueries >**</span><span class="sxs-lookup"><span data-stu-id="03d12-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03d12-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03d12-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03d12-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03d12-112">Attributes and Elements</span></span>  
 <span data-ttu-id="03d12-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03d12-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03d12-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="03d12-114">Attributes</span></span>  
 <span data-ttu-id="03d12-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="03d12-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03d12-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03d12-116">Child Elements</span></span>  
  
|<span data-ttu-id="03d12-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="03d12-117">Element</span></span>|<span data-ttu-id="03d12-118">Popis</span><span class="sxs-lookup"><span data-stu-id="03d12-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03d12-119">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="03d12-119">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="03d12-120">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="03d12-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03d12-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03d12-121">Parent Elements</span></span>  
  
|<span data-ttu-id="03d12-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="03d12-122">Element</span></span>|<span data-ttu-id="03d12-123">Popis</span><span class="sxs-lookup"><span data-stu-id="03d12-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03d12-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="03d12-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="03d12-125">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="03d12-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03d12-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03d12-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="03d12-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="03d12-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="03d12-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="03d12-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
