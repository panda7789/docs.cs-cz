---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: ed08f5533cd6b3839775d061452cb17110cc627e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398903"
---
# \<argument>
<span data-ttu-id="5d90d-101">Konfigurace element, který představuje argument přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="5d90d-101">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="5d90d-102">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5d90d-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<arguments>**](arguments.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<argument>**  
  
## <a name="syntax"></a><span data-ttu-id="5d90d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d90d-103">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d90d-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5d90d-104">Attributes and Elements</span></span>  
 <span data-ttu-id="5d90d-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5d90d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d90d-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="5d90d-106">Attributes</span></span>  
  
|<span data-ttu-id="5d90d-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="5d90d-107">Attribute</span></span>|<span data-ttu-id="5d90d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="5d90d-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d90d-109">name</span><span class="sxs-lookup"><span data-stu-id="5d90d-109">name</span></span>|<span data-ttu-id="5d90d-110">Řetězec, který určuje název argumentu.</span><span class="sxs-lookup"><span data-stu-id="5d90d-110">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d90d-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5d90d-111">Child Elements</span></span>  
 <span data-ttu-id="5d90d-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="5d90d-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d90d-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5d90d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5d90d-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="5d90d-114">Element</span></span>|<span data-ttu-id="5d90d-115">Description</span><span class="sxs-lookup"><span data-stu-id="5d90d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<arguments>](arguments.md)|<span data-ttu-id="5d90d-116">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="5d90d-116">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d90d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d90d-117">Remarks</span></span>  
 <span data-ttu-id="5d90d-118">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5d90d-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="5d90d-119">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="5d90d-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="5d90d-120">Můžete použít [\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) prvky a k extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="5d90d-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="5d90d-121">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při `Closed` vygenerování záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="5d90d-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="5d90d-122">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="5d90d-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d90d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d90d-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5d90d-124">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5d90d-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5d90d-125">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="5d90d-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
