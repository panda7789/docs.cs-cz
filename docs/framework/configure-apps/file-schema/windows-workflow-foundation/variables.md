---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 3ff568c267331538fb9be0e6cb40eebbca44d882
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375659"
---
# <a name="variables"></a><span data-ttu-id="8ced3-101">\<proměnné ></span><span class="sxs-lookup"><span data-stu-id="8ced3-101">\<variables></span></span>
<span data-ttu-id="8ced3-102">Představuje kolekci proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="8ced3-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="8ced3-103">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8ced3-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="8ced3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8ced3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8ced3-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="8ced3-105">\<tracking></span></span>  
<span data-ttu-id="8ced3-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8ced3-106">\<trackingProfile></span></span>  
<span data-ttu-id="8ced3-107">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="8ced3-107">\<workflow></span></span>  
<span data-ttu-id="8ced3-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="8ced3-108">\<activityStateQueries></span></span>  
<span data-ttu-id="8ced3-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="8ced3-109">\<activityStateQuery></span></span>  
<span data-ttu-id="8ced3-110">\<proměnné ></span><span class="sxs-lookup"><span data-stu-id="8ced3-110">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ced3-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ced3-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ced3-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8ced3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8ced3-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8ced3-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ced3-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="8ced3-114">Attributes</span></span>  
 <span data-ttu-id="8ced3-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="8ced3-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8ced3-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8ced3-116">Child Elements</span></span>  
  
|<span data-ttu-id="8ced3-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="8ced3-117">Element</span></span>|<span data-ttu-id="8ced3-118">Popis</span><span class="sxs-lookup"><span data-stu-id="8ced3-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ced3-119">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="8ced3-119">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="8ced3-120">Proměnná přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="8ced3-120">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ced3-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8ced3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8ced3-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="8ced3-122">Element</span></span>|<span data-ttu-id="8ced3-123">Popis</span><span class="sxs-lookup"><span data-stu-id="8ced3-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ced3-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="8ced3-124">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="8ced3-125">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="8ced3-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8ced3-126">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="8ced3-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ced3-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ced3-127">Remarks</span></span>  
 <span data-ttu-id="8ced3-128">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8ced3-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="8ced3-129">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="8ced3-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="8ced3-130">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="8ced3-130">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="8ced3-131">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="8ced3-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="8ced3-132">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="8ced3-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ced3-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ced3-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8ced3-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="8ced3-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8ced3-135">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="8ced3-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
