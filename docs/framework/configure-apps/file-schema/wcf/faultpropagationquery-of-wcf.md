---
title: '&lt;faultPropagationQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: cf582fce4e899e62daa4f34f193a0232ec19a135
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149030"
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="9772f-102">&lt;faultPropagationQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="9772f-102">&lt;faultPropagationQuery&gt; of WCF</span></span>

<span data-ttu-id="9772f-103">Představuje dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="9772f-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9772f-104">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="9772f-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="9772f-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="9772f-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="9772f-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="9772f-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="9772f-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9772f-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9772f-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9772f-108">\<system.serviceModel></span></span>  
<span data-ttu-id="9772f-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="9772f-109">\<tracking></span></span>  
<span data-ttu-id="9772f-110">\<profily ></span><span class="sxs-lookup"><span data-stu-id="9772f-110">\<profiles></span></span>  
<span data-ttu-id="9772f-111">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="9772f-111">\<trackingProfile></span></span>  
<span data-ttu-id="9772f-112">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9772f-112">\<workflow></span></span>  
<span data-ttu-id="9772f-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="9772f-113">\<faultPropagationQueries></span></span>  
<span data-ttu-id="9772f-114">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="9772f-114">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9772f-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9772f-115">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9772f-116">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9772f-116">Attributes and elements</span></span>

<span data-ttu-id="9772f-117">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9772f-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9772f-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="9772f-118">Attributes</span></span>  
  
|<span data-ttu-id="9772f-119">Atribut</span><span class="sxs-lookup"><span data-stu-id="9772f-119">Attribute</span></span>|<span data-ttu-id="9772f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="9772f-120">Description</span></span>|  
|---------------|-----------------|  
|`faultSourceActivityName`|<span data-ttu-id="9772f-121">Řetězec, který určuje název aktivity obslužná rutina chyby, která propagována chybu.</span><span class="sxs-lookup"><span data-stu-id="9772f-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="9772f-122">Výchozí hodnota je \*, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="9772f-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|`faultHandlerActivityName`|<span data-ttu-id="9772f-123">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="9772f-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9772f-124">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="9772f-124">Child elements</span></span>

<span data-ttu-id="9772f-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="9772f-125">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="9772f-126">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="9772f-126">Parent elements</span></span>  
  
|<span data-ttu-id="9772f-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="9772f-127">Element</span></span>|<span data-ttu-id="9772f-128">Popis</span><span class="sxs-lookup"><span data-stu-id="9772f-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9772f-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="9772f-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="9772f-130">Představuje seznam konfigurační prvky, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="9772f-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9772f-131">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="9772f-131">This event occurs each time a FaultHandler processes a fault.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="9772f-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9772f-132">See also</span></span>  
 
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9772f-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9772f-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9772f-134">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="9772f-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
