---
title: "&lt;activityStateQueries&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ec6cb2d077f95f53a2ee0daf8e2819ae91cb13b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="5e90d-102">&lt;activityStateQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="5e90d-102">&lt;activityStateQueries&gt; of WCF</span></span>
<span data-ttu-id="5e90d-103">Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5e90d-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="5e90d-104">Například můžete udržovat přehled o každém dokončení aktivity "Odeslat E-Mail" v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5e90d-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="5e90d-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="5e90d-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="5e90d-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="5e90d-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="5e90d-107">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5e90d-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="5e90d-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="5e90d-108">\<system.serviceModel></span></span>  
<span data-ttu-id="5e90d-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="5e90d-109">\<tracking></span></span>  
<span data-ttu-id="5e90d-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="5e90d-110">\<trackingProfile></span></span>  
<span data-ttu-id="5e90d-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="5e90d-111">\<workflow></span></span>  
<span data-ttu-id="5e90d-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="5e90d-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e90d-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e90d-113">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e90d-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5e90d-114">Attributes and Elements</span></span>  
 <span data-ttu-id="5e90d-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5e90d-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e90d-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="5e90d-116">Attributes</span></span>  
 <span data-ttu-id="5e90d-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="5e90d-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5e90d-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5e90d-118">Child Elements</span></span>  
  
|<span data-ttu-id="5e90d-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="5e90d-119">Element</span></span>|<span data-ttu-id="5e90d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5e90d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e90d-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="5e90d-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="5e90d-122">Dotaz, který se používá ke sledování ošetření chyb, které se vyskytují v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="5e90d-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5e90d-123">K této události dochází pokaždé, když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="5e90d-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e90d-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5e90d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5e90d-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="5e90d-125">Element</span></span>|<span data-ttu-id="5e90d-126">Popis</span><span class="sxs-lookup"><span data-stu-id="5e90d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e90d-127">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="5e90d-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="5e90d-128">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5e90d-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e90d-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e90d-129">See Also</span></span>  
 <span data-ttu-id="5e90d-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="5e90d-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span></span>    
 <span data-ttu-id="5e90d-131"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="5e90d-131"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>    
 [<span data-ttu-id="5e90d-132">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="5e90d-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="5e90d-133">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="5e90d-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
