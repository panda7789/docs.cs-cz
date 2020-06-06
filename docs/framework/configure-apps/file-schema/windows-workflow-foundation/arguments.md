---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: f06a2188ea3561437c1453d3a1cb23d42d767f53
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398916"
---
# \<arguments>
<span data-ttu-id="7f763-101">Představuje kolekci argumentů přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="7f763-101">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="7f763-102">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="7f763-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<arguments>**  
  
## <a name="syntax"></a><span data-ttu-id="7f763-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f763-103">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f763-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7f763-104">Attributes and Elements</span></span>  
 <span data-ttu-id="7f763-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7f763-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f763-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="7f763-106">Attributes</span></span>  
 <span data-ttu-id="7f763-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="7f763-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7f763-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7f763-108">Child Elements</span></span>  
  
|<span data-ttu-id="7f763-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f763-109">Element</span></span>|<span data-ttu-id="7f763-110">Description</span><span class="sxs-lookup"><span data-stu-id="7f763-110">Description</span></span>|  
|-------------|-----------------|  
|[\<argument>](argument.md)|<span data-ttu-id="7f763-111">Argument přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="7f763-111">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f763-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7f763-112">Parent Elements</span></span>  
  
|<span data-ttu-id="7f763-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f763-113">Element</span></span>|<span data-ttu-id="7f763-114">Description</span><span class="sxs-lookup"><span data-stu-id="7f763-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="7f763-115">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="7f763-115">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7f763-116">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="7f763-116">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f763-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f763-117">Remarks</span></span>  
 <span data-ttu-id="7f763-118">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7f763-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="7f763-119">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="7f763-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="7f763-120">Můžete použít [\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) prvky a k extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="7f763-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="7f763-121">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při `Closed` vygenerování záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="7f763-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="7f763-122">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="7f763-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f763-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f763-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7f763-124">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="7f763-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7f763-125">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="7f763-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
