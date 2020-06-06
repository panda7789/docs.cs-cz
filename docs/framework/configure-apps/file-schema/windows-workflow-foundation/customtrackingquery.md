---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152206"
---
# \<customTrackingQuery>
<span data-ttu-id="53f7c-101">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="53f7c-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="53f7c-102">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="53f7c-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="53f7c-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="53f7c-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="53f7c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53f7c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53f7c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="53f7c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="53f7c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="53f7c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53f7c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="53f7c-107">Attributes</span></span>  
  
|<span data-ttu-id="53f7c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="53f7c-108">Attribute</span></span>|<span data-ttu-id="53f7c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="53f7c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53f7c-110">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="53f7c-110">activityName</span></span>|<span data-ttu-id="53f7c-111">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="53f7c-111">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="53f7c-112">name</span><span class="sxs-lookup"><span data-stu-id="53f7c-112">name</span></span>|<span data-ttu-id="53f7c-113">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="53f7c-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53f7c-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="53f7c-114">Child Elements</span></span>  
 <span data-ttu-id="53f7c-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="53f7c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53f7c-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="53f7c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="53f7c-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="53f7c-117">Element</span></span>|<span data-ttu-id="53f7c-118">Description</span><span class="sxs-lookup"><span data-stu-id="53f7c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="53f7c-119">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="53f7c-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53f7c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="53f7c-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="53f7c-121">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="53f7c-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="53f7c-122">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="53f7c-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
