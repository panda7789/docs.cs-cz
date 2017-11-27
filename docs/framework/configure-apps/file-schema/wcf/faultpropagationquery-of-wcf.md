---
title: "&lt;faultPropagationQuery&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 650be6a52651f9f55a868d135fd7d0dfa84b967a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="95d7a-102">&lt;faultPropagationQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="95d7a-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="95d7a-103">Představuje dotaz, který se používá ke sledování ošetření chyb, které se vyskytují v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="95d7a-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="95d7a-104">K této události dochází pokaždé, když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="95d7a-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="95d7a-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="95d7a-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="95d7a-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="95d7a-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="95d7a-107">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="95d7a-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="95d7a-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="95d7a-108">\<system.serviceModel></span></span>  
<span data-ttu-id="95d7a-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="95d7a-109">\<tracking></span></span>  
<span data-ttu-id="95d7a-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="95d7a-110">\<trackingProfile></span></span>  
<span data-ttu-id="95d7a-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="95d7a-111">\<workflow></span></span>  
<span data-ttu-id="95d7a-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="95d7a-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="95d7a-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="95d7a-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95d7a-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95d7a-114">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95d7a-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="95d7a-115">Attributes and Elements</span></span>  
 <span data-ttu-id="95d7a-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="95d7a-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95d7a-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="95d7a-117">Attributes</span></span>  
  
|<span data-ttu-id="95d7a-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="95d7a-118">Attribute</span></span>|<span data-ttu-id="95d7a-119">Popis</span><span class="sxs-lookup"><span data-stu-id="95d7a-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95d7a-120">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="95d7a-120">activityName</span></span>|<span data-ttu-id="95d7a-121">Řetězec, který určuje název aktivity obslužná rutina chyby, která propagována chybu.</span><span class="sxs-lookup"><span data-stu-id="95d7a-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="95d7a-122">Výchozí hodnota je *, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="95d7a-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="95d7a-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="95d7a-123">faultHandlerActivityName</span></span>|<span data-ttu-id="95d7a-124">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="95d7a-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95d7a-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="95d7a-125">Child Elements</span></span>  
 <span data-ttu-id="95d7a-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="95d7a-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95d7a-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="95d7a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="95d7a-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="95d7a-128">Element</span></span>|<span data-ttu-id="95d7a-129">Popis</span><span class="sxs-lookup"><span data-stu-id="95d7a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95d7a-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="95d7a-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="95d7a-131">Představuje seznam konfigurační prvky, které se používají ke sledování ošetření chyb, které se vyskytují v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="95d7a-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="95d7a-132">K této události dochází pokaždé, když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="95d7a-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95d7a-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="95d7a-133">See Also</span></span>  
 <span data-ttu-id="95d7a-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="95d7a-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="95d7a-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="95d7a-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="95d7a-136">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="95d7a-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="95d7a-137">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="95d7a-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
