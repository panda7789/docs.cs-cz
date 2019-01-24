---
title: '&lt;activityStateQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: bfd19e00e79a95eb717ca9131e92b5ff5c600d5b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511979"
---
# <a name="ltactivitystatequeriesgt"></a><span data-ttu-id="05e1b-102">&lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="05e1b-102">&lt;activityStateQueries&gt;</span></span>
<span data-ttu-id="05e1b-103">Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="05e1b-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="05e1b-104">Můžete například sledovat, pokaždé, když dokončí "Odeslat E-Mail" aktivity v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="05e1b-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="05e1b-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="05e1b-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="05e1b-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="05e1b-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="05e1b-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="05e1b-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="05e1b-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="05e1b-108">\<system.serviceModel></span></span>  
<span data-ttu-id="05e1b-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="05e1b-109">\<tracking></span></span>  
<span data-ttu-id="05e1b-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="05e1b-110">\<trackingProfile></span></span>  
<span data-ttu-id="05e1b-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="05e1b-111">\<workflow></span></span>  
<span data-ttu-id="05e1b-112">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="05e1b-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05e1b-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05e1b-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05e1b-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="05e1b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="05e1b-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="05e1b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05e1b-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="05e1b-116">Attributes</span></span>  
 <span data-ttu-id="05e1b-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="05e1b-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05e1b-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="05e1b-118">Child Elements</span></span>  
  
|<span data-ttu-id="05e1b-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="05e1b-119">Element</span></span>|<span data-ttu-id="05e1b-120">Popis</span><span class="sxs-lookup"><span data-stu-id="05e1b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05e1b-121">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="05e1b-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="05e1b-122">Dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="05e1b-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="05e1b-123">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="05e1b-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05e1b-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="05e1b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="05e1b-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="05e1b-125">Element</span></span>|<span data-ttu-id="05e1b-126">Popis</span><span class="sxs-lookup"><span data-stu-id="05e1b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05e1b-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="05e1b-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="05e1b-128">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="05e1b-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05e1b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05e1b-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="05e1b-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="05e1b-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="05e1b-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="05e1b-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
