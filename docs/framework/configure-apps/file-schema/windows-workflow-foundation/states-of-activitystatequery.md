---
title: '&lt;stavy&gt; z &lt;activityStateQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: db50155af22cd8a50158b940a88599df1a66ce1a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635855"
---
# <a name="ltstatesgt-of-ltactivitystatequerygt"></a><span data-ttu-id="1fb9c-102">&lt;stavy&gt; z &lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="1fb9c-102">&lt;states&gt; of &lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="1fb9c-103">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="1fb9c-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="1fb9c-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1fb9c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="1fb9c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1fb9c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="1fb9c-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="1fb9c-106">\<tracking></span></span>  
<span data-ttu-id="1fb9c-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1fb9c-107">\<trackingProfile></span></span>  
<span data-ttu-id="1fb9c-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="1fb9c-108">\<workflow></span></span>  
<span data-ttu-id="1fb9c-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="1fb9c-109">\<activityStateQueries></span></span>  
<span data-ttu-id="1fb9c-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="1fb9c-110">\<activityStateQuery></span></span>  
<span data-ttu-id="1fb9c-111">\<states></span><span class="sxs-lookup"><span data-stu-id="1fb9c-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fb9c-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fb9c-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fb9c-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1fb9c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1fb9c-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1fb9c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fb9c-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="1fb9c-115">Attributes</span></span>  
 <span data-ttu-id="1fb9c-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="1fb9c-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1fb9c-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1fb9c-117">Child Elements</span></span>  
  
|<span data-ttu-id="1fb9c-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="1fb9c-118">Element</span></span>|<span data-ttu-id="1fb9c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1fb9c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fb9c-120">\<state></span><span class="sxs-lookup"><span data-stu-id="1fb9c-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/state-of-states.md)|<span data-ttu-id="1fb9c-121">Konfigurace element, který obsahuje stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="1fb9c-121">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1fb9c-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1fb9c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1fb9c-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="1fb9c-123">Element</span></span>|<span data-ttu-id="1fb9c-124">Popis</span><span class="sxs-lookup"><span data-stu-id="1fb9c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fb9c-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="1fb9c-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="1fb9c-126">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="1fb9c-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="1fb9c-127">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="1fb9c-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fb9c-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1fb9c-128">Remarks</span></span>  
 <span data-ttu-id="1fb9c-129">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1fb9c-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="1fb9c-130">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="1fb9c-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="1fb9c-131">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="1fb9c-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="1fb9c-132">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="1fb9c-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="1fb9c-133">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="1fb9c-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1fb9c-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1fb9c-134">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1fb9c-135">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1fb9c-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1fb9c-136">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="1fb9c-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
