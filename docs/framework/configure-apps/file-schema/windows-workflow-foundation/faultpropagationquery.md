---
title: '&lt;faultPropagationQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50dc2c4c5d4c1517d6ac3409dc4d932f67cbeb8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltfaultpropagationquerygt"></a><span data-ttu-id="fb8e8-102">&lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="fb8e8-102">&lt;faultPropagationQuery&gt;</span></span>
<span data-ttu-id="fb8e8-103">Představuje dotaz, který se používá ke sledování ošetření chyb, které se vyskytují v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="fb8e8-104">K této události dochází pokaždé, když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="fb8e8-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="fb8e8-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="fb8e8-107">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="fb8e8-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="fb8e8-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="fb8e8-108">\<system.serviceModel></span></span>  
<span data-ttu-id="fb8e8-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="fb8e8-109">\<tracking></span></span>  
<span data-ttu-id="fb8e8-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="fb8e8-110">\<trackingProfile></span></span>  
<span data-ttu-id="fb8e8-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="fb8e8-111">\<workflow></span></span>  
<span data-ttu-id="fb8e8-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="fb8e8-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="fb8e8-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="fb8e8-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb8e8-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb8e8-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb8e8-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fb8e8-115">Attributes and Elements</span></span>  
 <span data-ttu-id="fb8e8-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb8e8-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="fb8e8-117">Attributes</span></span>  
  
|<span data-ttu-id="fb8e8-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="fb8e8-118">Attribute</span></span>|<span data-ttu-id="fb8e8-119">Popis</span><span class="sxs-lookup"><span data-stu-id="fb8e8-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fb8e8-120">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="fb8e8-120">activityName</span></span>|<span data-ttu-id="fb8e8-121">Řetězec, který určuje název aktivity obslužná rutina chyby, která propagována chybu.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="fb8e8-122">Výchozí hodnota je *, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="fb8e8-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="fb8e8-123">faultHandlerActivityName</span></span>|<span data-ttu-id="fb8e8-124">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb8e8-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fb8e8-125">Child Elements</span></span>  
 <span data-ttu-id="fb8e8-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="fb8e8-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb8e8-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fb8e8-127">Parent Elements</span></span>  
  
|<span data-ttu-id="fb8e8-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="fb8e8-128">Element</span></span>|<span data-ttu-id="fb8e8-129">Popis</span><span class="sxs-lookup"><span data-stu-id="fb8e8-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb8e8-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="fb8e8-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="fb8e8-131">Představuje seznam konfigurační prvky, které se používají ke sledování ošetření chyb, které se vyskytují v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="fb8e8-132">K této události dochází pokaždé, když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="fb8e8-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb8e8-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb8e8-133">See Also</span></span>  
 <span data-ttu-id="fb8e8-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fb8e8-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="fb8e8-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fb8e8-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="fb8e8-136">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="fb8e8-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="fb8e8-137">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="fb8e8-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
