---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 3e48256ab1127d45e95c557aa9c2434419d9ea59
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397583"
---
# \<variables>
<span data-ttu-id="ee2ba-101">Představuje kolekci proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-101">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="ee2ba-102">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ee2ba-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variables>**  
  
## <a name="syntax"></a><span data-ttu-id="ee2ba-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee2ba-103">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee2ba-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ee2ba-104">Attributes and Elements</span></span>  
 <span data-ttu-id="ee2ba-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee2ba-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="ee2ba-106">Attributes</span></span>  
 <span data-ttu-id="ee2ba-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="ee2ba-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ee2ba-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ee2ba-108">Child Elements</span></span>  
  
|<span data-ttu-id="ee2ba-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="ee2ba-109">Element</span></span>|<span data-ttu-id="ee2ba-110">Description</span><span class="sxs-lookup"><span data-stu-id="ee2ba-110">Description</span></span>|  
|-------------|-----------------|  
|[\<variable>](variable.md)|<span data-ttu-id="ee2ba-111">Proměnná přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-111">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee2ba-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ee2ba-112">Parent Elements</span></span>  
  
|<span data-ttu-id="ee2ba-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="ee2ba-113">Element</span></span>|<span data-ttu-id="ee2ba-114">Description</span><span class="sxs-lookup"><span data-stu-id="ee2ba-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="ee2ba-115">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-115">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ee2ba-116">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-116">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee2ba-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee2ba-117">Remarks</span></span>  
 <span data-ttu-id="ee2ba-118">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="ee2ba-119">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="ee2ba-120">Můžete použít [\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) prvky a k extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="ee2ba-121">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při `Closed` vygenerování záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="ee2ba-122">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="ee2ba-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee2ba-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee2ba-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ee2ba-124">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ee2ba-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ee2ba-125">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="ee2ba-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
