---
title: '&lt;faultPropagationQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 58196baafe92cd34986acbfae9e44ade3212cb33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltfaultpropagationqueriesgt"></a><span data-ttu-id="73adf-102">&lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="73adf-102">&lt;faultPropagationQueries&gt;</span></span>
<span data-ttu-id="73adf-103">Představuje kolekci dotazy, které se používají ke sledování ošetření chyb, které se vyskytují v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="73adf-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="73adf-104">K této události dochází pokaždé, když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="73adf-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="73adf-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="73adf-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="73adf-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="73adf-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="73adf-107">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="73adf-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="73adf-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="73adf-108">\<system.serviceModel></span></span>  
<span data-ttu-id="73adf-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="73adf-109">\<tracking></span></span>  
<span data-ttu-id="73adf-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="73adf-110">\<trackingProfile></span></span>  
<span data-ttu-id="73adf-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="73adf-111">\<workflow></span></span>  
<span data-ttu-id="73adf-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="73adf-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73adf-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73adf-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73adf-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="73adf-114">Attributes and Elements</span></span>  
 <span data-ttu-id="73adf-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="73adf-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73adf-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="73adf-116">Attributes</span></span>  
 <span data-ttu-id="73adf-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="73adf-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="73adf-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="73adf-118">Child Elements</span></span>  
  
|<span data-ttu-id="73adf-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="73adf-119">Element</span></span>|<span data-ttu-id="73adf-120">Popis</span><span class="sxs-lookup"><span data-stu-id="73adf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73adf-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="73adf-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="73adf-122">Dotaz, který se používá ke sledování ošetření chyb, které se vyskytují v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="73adf-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="73adf-123">K této události dochází pokaždé, když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="73adf-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73adf-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="73adf-124">Parent Elements</span></span>  
  
|<span data-ttu-id="73adf-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="73adf-125">Element</span></span>|<span data-ttu-id="73adf-126">Popis</span><span class="sxs-lookup"><span data-stu-id="73adf-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73adf-127">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="73adf-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="73adf-128">Konfigurace elementu, který obsahuje všechny dotazy pro konkrétní pracovní tok identifikovaný **activityDefinitionId** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="73adf-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73adf-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="73adf-129">See Also</span></span>  
 <span data-ttu-id="73adf-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="73adf-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="73adf-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="73adf-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="73adf-132">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="73adf-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="73adf-133">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="73adf-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
