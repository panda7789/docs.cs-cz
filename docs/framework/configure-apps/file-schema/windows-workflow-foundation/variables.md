---
title: '&lt;Proměnné&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: c3861eb02d7b19bde6932c67c3d5d19b82fd8fcf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520535"
---
# <a name="ltvariablesgt"></a><span data-ttu-id="20b35-102">&lt;Proměnné&gt;</span><span class="sxs-lookup"><span data-stu-id="20b35-102">&lt;variables&gt;</span></span>
<span data-ttu-id="20b35-103">Představuje kolekci proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="20b35-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="20b35-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="20b35-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="20b35-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="20b35-105">\<system.serviceModel></span></span>  
<span data-ttu-id="20b35-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="20b35-106">\<tracking></span></span>  
<span data-ttu-id="20b35-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="20b35-107">\<trackingProfile></span></span>  
<span data-ttu-id="20b35-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="20b35-108">\<workflow></span></span>  
<span data-ttu-id="20b35-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="20b35-109">\<activityStateQueries></span></span>  
<span data-ttu-id="20b35-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="20b35-110">\<activityStateQuery></span></span>  
<span data-ttu-id="20b35-111">\<proměnné ></span><span class="sxs-lookup"><span data-stu-id="20b35-111">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20b35-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20b35-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20b35-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="20b35-113">Attributes and Elements</span></span>  
 <span data-ttu-id="20b35-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="20b35-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20b35-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="20b35-115">Attributes</span></span>  
 <span data-ttu-id="20b35-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="20b35-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="20b35-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="20b35-117">Child Elements</span></span>  
  
|<span data-ttu-id="20b35-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="20b35-118">Element</span></span>|<span data-ttu-id="20b35-119">Popis</span><span class="sxs-lookup"><span data-stu-id="20b35-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20b35-120">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="20b35-120">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="20b35-121">Proměnná přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="20b35-121">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20b35-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="20b35-122">Parent Elements</span></span>  
  
|<span data-ttu-id="20b35-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="20b35-123">Element</span></span>|<span data-ttu-id="20b35-124">Popis</span><span class="sxs-lookup"><span data-stu-id="20b35-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20b35-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="20b35-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="20b35-126">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="20b35-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="20b35-127">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="20b35-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20b35-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20b35-128">Remarks</span></span>  
 <span data-ttu-id="20b35-129">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b35-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="20b35-130">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="20b35-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="20b35-131">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="20b35-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="20b35-132">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="20b35-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="20b35-133">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="20b35-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20b35-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20b35-134">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="20b35-135">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="20b35-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="20b35-136">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="20b35-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
