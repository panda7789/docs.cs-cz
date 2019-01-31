---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: 3e9fc4f286e7aba6406ce61910da9e614e13ffca
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276559"
---
# <a name="arguments"></a><span data-ttu-id="5412a-101">\<arguments></span><span class="sxs-lookup"><span data-stu-id="5412a-101">\<arguments></span></span>
<span data-ttu-id="5412a-102">Představuje kolekci argumentů přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="5412a-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="5412a-103">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5412a-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="5412a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5412a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5412a-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="5412a-105">\<tracking></span></span>  
<span data-ttu-id="5412a-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5412a-106">\<trackingProfile></span></span>  
<span data-ttu-id="5412a-107">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="5412a-107">\<workflow></span></span>  
<span data-ttu-id="5412a-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="5412a-108">\<activityStateQueries></span></span>  
<span data-ttu-id="5412a-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="5412a-109">\<activityStateQuery></span></span>  
<span data-ttu-id="5412a-110">\<arguments></span><span class="sxs-lookup"><span data-stu-id="5412a-110">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5412a-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5412a-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5412a-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5412a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5412a-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5412a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5412a-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="5412a-114">Attributes</span></span>  
 <span data-ttu-id="5412a-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="5412a-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5412a-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5412a-116">Child Elements</span></span>  
  
|<span data-ttu-id="5412a-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="5412a-117">Element</span></span>|<span data-ttu-id="5412a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="5412a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5412a-119">\<argument></span><span class="sxs-lookup"><span data-stu-id="5412a-119">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="5412a-120">Argument přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="5412a-120">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5412a-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5412a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5412a-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="5412a-122">Element</span></span>|<span data-ttu-id="5412a-123">Popis</span><span class="sxs-lookup"><span data-stu-id="5412a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5412a-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="5412a-124">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="5412a-125">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="5412a-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5412a-126">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="5412a-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5412a-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5412a-127">Remarks</span></span>  
 <span data-ttu-id="5412a-128">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5412a-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="5412a-129">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="5412a-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="5412a-130">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="5412a-130">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="5412a-131">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="5412a-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="5412a-132">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="5412a-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5412a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5412a-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5412a-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5412a-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5412a-135">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="5412a-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
