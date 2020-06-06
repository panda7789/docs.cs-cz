---
title: <state> z <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 391e552bce34d637a324c78702cb0e7121f2c999
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398653"
---
# <a name="state-of-states"></a><span data-ttu-id="b0717-102">\<state> z \<states></span><span class="sxs-lookup"><span data-stu-id="b0717-102">\<state> of \<states></span></span>
<span data-ttu-id="b0717-103">Konfigurace element, který obsahuje informace o stavu předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="b0717-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="b0717-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b0717-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="b0717-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0717-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0717-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b0717-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b0717-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b0717-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0717-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="b0717-108">Attributes</span></span>  
  
|<span data-ttu-id="b0717-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="b0717-109">Attribute</span></span>|<span data-ttu-id="b0717-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b0717-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b0717-111">name</span><span class="sxs-lookup"><span data-stu-id="b0717-111">name</span></span>|<span data-ttu-id="b0717-112">Řetězec, který určuje stav předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="b0717-112">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0717-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b0717-113">Child Elements</span></span>  
 <span data-ttu-id="b0717-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="b0717-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0717-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b0717-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b0717-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="b0717-116">Element</span></span>|<span data-ttu-id="b0717-117">Description</span><span class="sxs-lookup"><span data-stu-id="b0717-117">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-activitystatequery.md)|<span data-ttu-id="b0717-118">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="b0717-118">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0717-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0717-119">Remarks</span></span>  
 <span data-ttu-id="b0717-120">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b0717-120">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="b0717-121">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="b0717-121">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="b0717-122">Můžete použít [\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) prvky a k extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="b0717-122">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="b0717-123">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při `Closed` vygenerování záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="b0717-123">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="b0717-124">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="b0717-124">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0717-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0717-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b0717-126">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b0717-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b0717-127">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="b0717-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
