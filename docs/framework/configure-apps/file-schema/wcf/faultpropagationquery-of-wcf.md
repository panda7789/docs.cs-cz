---
title: '&lt;faultPropagationQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: df7119363e94a070bb898c984c12cf82755c3407
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087697"
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="909d1-102">&lt;faultPropagationQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="909d1-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="909d1-103">Představuje dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="909d1-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="909d1-104">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="909d1-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="909d1-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="909d1-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="909d1-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="909d1-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="909d1-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="909d1-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="909d1-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="909d1-108">\<system.serviceModel></span></span>  
<span data-ttu-id="909d1-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="909d1-109">\<tracking></span></span>  
<span data-ttu-id="909d1-110">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="909d1-110">\<trackingProfile></span></span>  
<span data-ttu-id="909d1-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="909d1-111">\<workflow></span></span>  
<span data-ttu-id="909d1-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="909d1-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="909d1-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="909d1-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="909d1-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="909d1-114">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String"/>
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="909d1-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="909d1-115">Attributes and Elements</span></span>  
 <span data-ttu-id="909d1-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="909d1-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="909d1-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="909d1-117">Attributes</span></span>  
  
|<span data-ttu-id="909d1-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="909d1-118">Attribute</span></span>|<span data-ttu-id="909d1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="909d1-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="909d1-120">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="909d1-120">activityName</span></span>|<span data-ttu-id="909d1-121">Řetězec, který určuje název aktivity obslužná rutina chyby, která propagována chybu.</span><span class="sxs-lookup"><span data-stu-id="909d1-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="909d1-122">Výchozí hodnota je \*, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="909d1-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="909d1-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="909d1-123">faultHandlerActivityName</span></span>|<span data-ttu-id="909d1-124">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="909d1-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="909d1-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="909d1-125">Child Elements</span></span>  
 <span data-ttu-id="909d1-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="909d1-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="909d1-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="909d1-127">Parent Elements</span></span>  
  
|<span data-ttu-id="909d1-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="909d1-128">Element</span></span>|<span data-ttu-id="909d1-129">Popis</span><span class="sxs-lookup"><span data-stu-id="909d1-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="909d1-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="909d1-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="909d1-131">Představuje seznam konfigurační prvky, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="909d1-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="909d1-132">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="909d1-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="909d1-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="909d1-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="909d1-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="909d1-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="909d1-135">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="909d1-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
