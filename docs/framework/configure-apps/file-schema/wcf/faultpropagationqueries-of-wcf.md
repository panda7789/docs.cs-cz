---
title: "&lt;faultPropagationQueries&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e122e8c6194545a02f6db429d550eabed5d49b27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="9fb78-102">&lt;faultPropagationQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="9fb78-102">&lt;faultPropagationQueries&gt; of WCF</span></span>
<span data-ttu-id="9fb78-103">Představuje kolekci dotazy, které se používají ke sledování ošetření chyb, které se vyskytují v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="9fb78-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9fb78-104">K této události dochází pokaždé, když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="9fb78-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="9fb78-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="9fb78-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="9fb78-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="9fb78-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="9fb78-107">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9fb78-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="9fb78-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9fb78-108">\<system.serviceModel></span></span>  
<span data-ttu-id="9fb78-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="9fb78-109">\<tracking></span></span>  
<span data-ttu-id="9fb78-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="9fb78-110">\<trackingProfile></span></span>  
<span data-ttu-id="9fb78-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9fb78-111">\<workflow></span></span>  
<span data-ttu-id="9fb78-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="9fb78-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fb78-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fb78-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9fb78-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9fb78-114">Attributes and Elements</span></span>  
 <span data-ttu-id="9fb78-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9fb78-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9fb78-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="9fb78-116">Attributes</span></span>  
 <span data-ttu-id="9fb78-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="9fb78-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9fb78-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9fb78-118">Child Elements</span></span>  
  
|<span data-ttu-id="9fb78-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="9fb78-119">Element</span></span>|<span data-ttu-id="9fb78-120">Popis</span><span class="sxs-lookup"><span data-stu-id="9fb78-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9fb78-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="9fb78-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="9fb78-122">Dotaz, který se používá ke sledování ošetření chyb, které se vyskytují v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="9fb78-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9fb78-123">K této události dochází pokaždé, když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="9fb78-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9fb78-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9fb78-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9fb78-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="9fb78-125">Element</span></span>|<span data-ttu-id="9fb78-126">Popis</span><span class="sxs-lookup"><span data-stu-id="9fb78-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9fb78-127">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9fb78-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9fb78-128">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9fb78-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9fb78-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="9fb78-129">See Also</span></span>  
 <span data-ttu-id="9fb78-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9fb78-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="9fb78-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9fb78-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="9fb78-132">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="9fb78-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9fb78-133">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="9fb78-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
