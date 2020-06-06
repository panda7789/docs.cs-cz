---
title: <customTrackingQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 204bbb6cf5ebcb30bf92b697885ecbbbd94385e0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855419"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="fb46c-102">\<customTrackingQuery>služby WCF</span><span class="sxs-lookup"><span data-stu-id="fb46c-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="fb46c-103">Představuje dotaz, který se používá ke sledování událostí, které definujete v aktivitách kódu.</span><span class="sxs-lookup"><span data-stu-id="fb46c-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="fb46c-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="fb46c-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="fb46c-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="fb46c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="fb46c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb46c-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb46c-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fb46c-107">Attributes and elements</span></span>  

<span data-ttu-id="fb46c-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fb46c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb46c-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="fb46c-109">Attributes</span></span>  
  
|<span data-ttu-id="fb46c-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="fb46c-110">Attribute</span></span>|<span data-ttu-id="fb46c-111">Popis</span><span class="sxs-lookup"><span data-stu-id="fb46c-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="fb46c-112">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="fb46c-112">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="fb46c-113">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="fb46c-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb46c-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="fb46c-114">Child elements</span></span>

<span data-ttu-id="fb46c-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="fb46c-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fb46c-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="fb46c-116">Parent elements</span></span>

|<span data-ttu-id="fb46c-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="fb46c-117">Element</span></span>|<span data-ttu-id="fb46c-118">Description</span><span class="sxs-lookup"><span data-stu-id="fb46c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQueries>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="fb46c-119">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="fb46c-119">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="fb46c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb46c-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fb46c-121">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="fb46c-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fb46c-122">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="fb46c-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
