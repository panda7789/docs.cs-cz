---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: a920d60d703fe262bee96d75c420c526d54f88ab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210643"
---
# <a name="argument"></a><span data-ttu-id="b2c10-101">\<argument></span><span class="sxs-lookup"><span data-stu-id="b2c10-101">\<argument></span></span>
<span data-ttu-id="b2c10-102">Konfigurace element, který představuje argument přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="b2c10-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="b2c10-103">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b2c10-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b2c10-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b2c10-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b2c10-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="b2c10-105">\<tracking></span></span>  
<span data-ttu-id="b2c10-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b2c10-106">\<trackingProfile></span></span>  
<span data-ttu-id="b2c10-107">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="b2c10-107">\<workflow></span></span>  
<span data-ttu-id="b2c10-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="b2c10-108">\<activityStateQueries></span></span>  
<span data-ttu-id="b2c10-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="b2c10-109">\<activityStateQuery></span></span>  
<span data-ttu-id="b2c10-110">\<arguments></span><span class="sxs-lookup"><span data-stu-id="b2c10-110">\<arguments></span></span>  
<span data-ttu-id="b2c10-111">\<argument></span><span class="sxs-lookup"><span data-stu-id="b2c10-111">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c10-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2c10-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2c10-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b2c10-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b2c10-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b2c10-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2c10-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="b2c10-115">Attributes</span></span>  
  
|<span data-ttu-id="b2c10-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="b2c10-116">Attribute</span></span>|<span data-ttu-id="b2c10-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b2c10-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2c10-118">name</span><span class="sxs-lookup"><span data-stu-id="b2c10-118">name</span></span>|<span data-ttu-id="b2c10-119">Řetězec, který určuje název argumentu.</span><span class="sxs-lookup"><span data-stu-id="b2c10-119">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2c10-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b2c10-120">Child Elements</span></span>  
 <span data-ttu-id="b2c10-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="b2c10-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2c10-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b2c10-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b2c10-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="b2c10-123">Element</span></span>|<span data-ttu-id="b2c10-124">Popis</span><span class="sxs-lookup"><span data-stu-id="b2c10-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2c10-125">\<arguments></span><span class="sxs-lookup"><span data-stu-id="b2c10-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="b2c10-126">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="b2c10-126">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2c10-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2c10-127">Remarks</span></span>  
 <span data-ttu-id="b2c10-128">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b2c10-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="b2c10-129">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="b2c10-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="b2c10-130">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="b2c10-130">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="b2c10-131">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="b2c10-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="b2c10-132">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="b2c10-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b2c10-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2c10-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b2c10-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b2c10-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b2c10-135">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="b2c10-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
