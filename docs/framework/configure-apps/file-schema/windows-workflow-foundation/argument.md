---
title: '&lt;argument&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: 3744781f844d4a1728ba1e9846b2b8c56c0ad8fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554596"
---
# <a name="ltargumentgt"></a><span data-ttu-id="040b8-102">&lt;argument&gt;</span><span class="sxs-lookup"><span data-stu-id="040b8-102">&lt;argument&gt;</span></span>
<span data-ttu-id="040b8-103">Konfigurace element, který představuje argument přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="040b8-103">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="040b8-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="040b8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="040b8-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="040b8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="040b8-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="040b8-106">\<tracking></span></span>  
<span data-ttu-id="040b8-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="040b8-107">\<trackingProfile></span></span>  
<span data-ttu-id="040b8-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="040b8-108">\<workflow></span></span>  
<span data-ttu-id="040b8-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="040b8-109">\<activityStateQueries></span></span>  
<span data-ttu-id="040b8-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="040b8-110">\<activityStateQuery></span></span>  
<span data-ttu-id="040b8-111">\<arguments></span><span class="sxs-lookup"><span data-stu-id="040b8-111">\<arguments></span></span>  
<span data-ttu-id="040b8-112">\<argument></span><span class="sxs-lookup"><span data-stu-id="040b8-112">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="040b8-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="040b8-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="040b8-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="040b8-114">Attributes and Elements</span></span>  
 <span data-ttu-id="040b8-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="040b8-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="040b8-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="040b8-116">Attributes</span></span>  
  
|<span data-ttu-id="040b8-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="040b8-117">Attribute</span></span>|<span data-ttu-id="040b8-118">Popis</span><span class="sxs-lookup"><span data-stu-id="040b8-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="040b8-119">name</span><span class="sxs-lookup"><span data-stu-id="040b8-119">name</span></span>|<span data-ttu-id="040b8-120">Řetězec, který určuje název argumentu.</span><span class="sxs-lookup"><span data-stu-id="040b8-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="040b8-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="040b8-121">Child Elements</span></span>  
 <span data-ttu-id="040b8-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="040b8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="040b8-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="040b8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="040b8-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="040b8-124">Element</span></span>|<span data-ttu-id="040b8-125">Popis</span><span class="sxs-lookup"><span data-stu-id="040b8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="040b8-126">\<arguments></span><span class="sxs-lookup"><span data-stu-id="040b8-126">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="040b8-127">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="040b8-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="040b8-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="040b8-128">Remarks</span></span>  
 <span data-ttu-id="040b8-129">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="040b8-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="040b8-130">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="040b8-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="040b8-131">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="040b8-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="040b8-132">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="040b8-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="040b8-133">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="040b8-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="040b8-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="040b8-134">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="040b8-135">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="040b8-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="040b8-136">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="040b8-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
