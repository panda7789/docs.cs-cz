---
title: '&lt;faultPropagationQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: a91a6f61b39a780ed48ad8d5f5e0dfb9ef60da39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538333"
---
# <a name="ltfaultpropagationquerygt"></a><span data-ttu-id="56c9e-102">&lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="56c9e-102">&lt;faultPropagationQuery&gt;</span></span>
<span data-ttu-id="56c9e-103">Představuje dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="56c9e-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="56c9e-104">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="56c9e-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="56c9e-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="56c9e-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="56c9e-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="56c9e-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="56c9e-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="56c9e-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="56c9e-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="56c9e-108">\<system.serviceModel></span></span>  
<span data-ttu-id="56c9e-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="56c9e-109">\<tracking></span></span>  
<span data-ttu-id="56c9e-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="56c9e-110">\<trackingProfile></span></span>  
<span data-ttu-id="56c9e-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="56c9e-111">\<workflow></span></span>  
<span data-ttu-id="56c9e-112">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="56c9e-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="56c9e-113">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="56c9e-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56c9e-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56c9e-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56c9e-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="56c9e-115">Attributes and Elements</span></span>  
 <span data-ttu-id="56c9e-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="56c9e-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56c9e-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="56c9e-117">Attributes</span></span>  
  
|<span data-ttu-id="56c9e-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="56c9e-118">Attribute</span></span>|<span data-ttu-id="56c9e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="56c9e-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="56c9e-120">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="56c9e-120">activityName</span></span>|<span data-ttu-id="56c9e-121">Řetězec, který určuje název aktivity obslužná rutina chyby, která propagována chybu.</span><span class="sxs-lookup"><span data-stu-id="56c9e-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="56c9e-122">Výchozí hodnota je \*, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="56c9e-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="56c9e-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="56c9e-123">faultHandlerActivityName</span></span>|<span data-ttu-id="56c9e-124">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="56c9e-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56c9e-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="56c9e-125">Child Elements</span></span>  
 <span data-ttu-id="56c9e-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="56c9e-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56c9e-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="56c9e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="56c9e-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="56c9e-128">Element</span></span>|<span data-ttu-id="56c9e-129">Popis</span><span class="sxs-lookup"><span data-stu-id="56c9e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56c9e-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="56c9e-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="56c9e-131">Představuje seznam konfigurační prvky, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="56c9e-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="56c9e-132">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="56c9e-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56c9e-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56c9e-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="56c9e-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="56c9e-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="56c9e-135">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="56c9e-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
