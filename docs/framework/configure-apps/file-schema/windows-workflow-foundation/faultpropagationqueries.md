---
title: '&lt;faultPropagationQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 5fd6ffc9560247089c7fbb60b0e5a7d3a417ea6f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltfaultpropagationqueriesgt"></a><span data-ttu-id="5bae2-102">&lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="5bae2-102">&lt;faultPropagationQueries&gt;</span></span>
<span data-ttu-id="5bae2-103">Představuje kolekci dotazy, které se používají ke sledování ošetření chyb, které se vyskytují v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="5bae2-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5bae2-104">K této události dochází pokaždé, když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="5bae2-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="5bae2-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="5bae2-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="5bae2-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="5bae2-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="5bae2-107">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5bae2-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="5bae2-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5bae2-108">\<system.serviceModel></span></span>  
<span data-ttu-id="5bae2-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="5bae2-109">\<tracking></span></span>  
<span data-ttu-id="5bae2-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="5bae2-110">\<trackingProfile></span></span>  
<span data-ttu-id="5bae2-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="5bae2-111">\<workflow></span></span>  
<span data-ttu-id="5bae2-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="5bae2-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bae2-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bae2-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bae2-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5bae2-114">Attributes and Elements</span></span>  
 <span data-ttu-id="5bae2-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5bae2-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bae2-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="5bae2-116">Attributes</span></span>  
 <span data-ttu-id="5bae2-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="5bae2-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5bae2-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5bae2-118">Child Elements</span></span>  
  
|<span data-ttu-id="5bae2-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="5bae2-119">Element</span></span>|<span data-ttu-id="5bae2-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5bae2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bae2-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="5bae2-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="5bae2-122">Dotaz, který se používá ke sledování ošetření chyb, které se vyskytují v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="5bae2-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5bae2-123">K této události dochází pokaždé, když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="5bae2-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5bae2-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5bae2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5bae2-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="5bae2-125">Element</span></span>|<span data-ttu-id="5bae2-126">Popis</span><span class="sxs-lookup"><span data-stu-id="5bae2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bae2-127">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="5bae2-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="5bae2-128">Konfigurace elementu, který obsahuje všechny dotazy pro konkrétní pracovní tok identifikovaný **activityDefinitionId** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5bae2-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bae2-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="5bae2-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="5bae2-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5bae2-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="5bae2-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="5bae2-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
