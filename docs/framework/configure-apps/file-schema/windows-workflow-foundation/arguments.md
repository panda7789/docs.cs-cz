---
title: '&lt;arguments&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: 34695cd2fd62a0a10398fd73f014c093c3c5f61b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681661"
---
# <a name="ltargumentsgt"></a><span data-ttu-id="4f3c1-102">&lt;arguments&gt;</span><span class="sxs-lookup"><span data-stu-id="4f3c1-102">&lt;arguments&gt;</span></span>
<span data-ttu-id="4f3c1-103">Představuje kolekci argumentů přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="4f3c1-103">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="4f3c1-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4f3c1-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="4f3c1-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4f3c1-105">\<system.serviceModel></span></span>  
<span data-ttu-id="4f3c1-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="4f3c1-106">\<tracking></span></span>  
<span data-ttu-id="4f3c1-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4f3c1-107">\<trackingProfile></span></span>  
<span data-ttu-id="4f3c1-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="4f3c1-108">\<workflow></span></span>  
<span data-ttu-id="4f3c1-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="4f3c1-109">\<activityStateQueries></span></span>  
<span data-ttu-id="4f3c1-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="4f3c1-110">\<activityStateQuery></span></span>  
<span data-ttu-id="4f3c1-111">\<arguments></span><span class="sxs-lookup"><span data-stu-id="4f3c1-111">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f3c1-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f3c1-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f3c1-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4f3c1-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4f3c1-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4f3c1-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f3c1-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="4f3c1-115">Attributes</span></span>  
 <span data-ttu-id="4f3c1-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="4f3c1-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4f3c1-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4f3c1-117">Child Elements</span></span>  
  
|<span data-ttu-id="4f3c1-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="4f3c1-118">Element</span></span>|<span data-ttu-id="4f3c1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="4f3c1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f3c1-120">\<argument></span><span class="sxs-lookup"><span data-stu-id="4f3c1-120">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="4f3c1-121">Argument přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="4f3c1-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f3c1-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4f3c1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4f3c1-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="4f3c1-123">Element</span></span>|<span data-ttu-id="4f3c1-124">Popis</span><span class="sxs-lookup"><span data-stu-id="4f3c1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f3c1-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="4f3c1-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="4f3c1-126">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="4f3c1-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4f3c1-127">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="4f3c1-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f3c1-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f3c1-128">Remarks</span></span>  
 <span data-ttu-id="4f3c1-129">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4f3c1-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="4f3c1-130">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="4f3c1-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="4f3c1-131">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="4f3c1-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="4f3c1-132">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="4f3c1-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="4f3c1-133">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="4f3c1-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f3c1-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f3c1-134">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4f3c1-135">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="4f3c1-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4f3c1-136">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="4f3c1-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
