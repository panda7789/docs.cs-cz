---
title: '&lt;faultPropagationQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: c3853c470a9243835e071d35008dfff5b885591d
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123316"
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="74004-102">&lt;faultPropagationQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="74004-102">&lt;faultPropagationQuery&gt; of WCF</span></span>

<span data-ttu-id="74004-103">Představuje dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="74004-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="74004-104">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="74004-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="74004-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="74004-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="74004-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="74004-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="74004-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="74004-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="74004-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="74004-108">\<system.serviceModel></span></span>  
<span data-ttu-id="74004-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="74004-109">\<tracking></span></span>  
<span data-ttu-id="74004-110">\<profily ></span><span class="sxs-lookup"><span data-stu-id="74004-110">\<profiles></span></span>  
<span data-ttu-id="74004-111">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="74004-111">\<trackingProfile></span></span>  
<span data-ttu-id="74004-112">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="74004-112">\<workflow></span></span>  
<span data-ttu-id="74004-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="74004-113">\<faultPropagationQueries></span></span>  
<span data-ttu-id="74004-114">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="74004-114">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74004-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74004-115">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74004-116">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="74004-116">Attributes and elements</span></span>

<span data-ttu-id="74004-117">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="74004-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="74004-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="74004-118">Attributes</span></span>  
  
|<span data-ttu-id="74004-119">Atribut</span><span class="sxs-lookup"><span data-stu-id="74004-119">Attribute</span></span>|<span data-ttu-id="74004-120">Popis</span><span class="sxs-lookup"><span data-stu-id="74004-120">Description</span></span>|  
|---------------|-----------------|  
|`faultSourceActivityName`|<span data-ttu-id="74004-121">Řetězec, který určuje název aktivity obslužná rutina chyby, která propagována chybu.</span><span class="sxs-lookup"><span data-stu-id="74004-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="74004-122">Výchozí hodnota je \*, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="74004-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|`faultHandlerActivityName`|<span data-ttu-id="74004-123">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="74004-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74004-124">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="74004-124">Child elements</span></span>

<span data-ttu-id="74004-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="74004-125">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="74004-126">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="74004-126">Parent elements</span></span>  
  
|<span data-ttu-id="74004-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="74004-127">Element</span></span>|<span data-ttu-id="74004-128">Popis</span><span class="sxs-lookup"><span data-stu-id="74004-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74004-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="74004-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="74004-130">Představuje seznam konfigurační prvky, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="74004-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="74004-131">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="74004-131">This event occurs each time a FaultHandler processes a fault.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="74004-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74004-132">See also</span></span>  
 
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="74004-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="74004-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="74004-134">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="74004-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
