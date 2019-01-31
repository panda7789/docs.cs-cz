---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 1a6899eaa04ad16192e07f4bc2ad1abe6e4aedd5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257363"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="5e7b5-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="5e7b5-101">\<faultPropagationQuery></span></span>
<span data-ttu-id="5e7b5-102">Představuje dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="5e7b5-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5e7b5-103">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="5e7b5-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="5e7b5-104">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="5e7b5-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="5e7b5-105">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="5e7b5-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="5e7b5-106">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5e7b5-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="5e7b5-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5e7b5-107">\<system.serviceModel></span></span>  
<span data-ttu-id="5e7b5-108">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="5e7b5-108">\<tracking></span></span>  
<span data-ttu-id="5e7b5-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5e7b5-109">\<trackingProfile></span></span>  
<span data-ttu-id="5e7b5-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="5e7b5-110">\<workflow></span></span>  
<span data-ttu-id="5e7b5-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="5e7b5-111">\<faultPropagationQueries></span></span>  
<span data-ttu-id="5e7b5-112">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="5e7b5-112">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e7b5-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e7b5-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e7b5-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5e7b5-114">Attributes and Elements</span></span>  
 <span data-ttu-id="5e7b5-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5e7b5-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e7b5-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="5e7b5-116">Attributes</span></span>  
  
|<span data-ttu-id="5e7b5-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="5e7b5-117">Attribute</span></span>|<span data-ttu-id="5e7b5-118">Popis</span><span class="sxs-lookup"><span data-stu-id="5e7b5-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e7b5-119">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="5e7b5-119">activityName</span></span>|<span data-ttu-id="5e7b5-120">Řetězec, který určuje název aktivity obslužná rutina chyby, která propagována chybu.</span><span class="sxs-lookup"><span data-stu-id="5e7b5-120">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="5e7b5-121">Výchozí hodnota je \*, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="5e7b5-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="5e7b5-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="5e7b5-122">faultHandlerActivityName</span></span>|<span data-ttu-id="5e7b5-123">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="5e7b5-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e7b5-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5e7b5-124">Child Elements</span></span>  
 <span data-ttu-id="5e7b5-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="5e7b5-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e7b5-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5e7b5-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5e7b5-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="5e7b5-127">Element</span></span>|<span data-ttu-id="5e7b5-128">Popis</span><span class="sxs-lookup"><span data-stu-id="5e7b5-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e7b5-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="5e7b5-129">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="5e7b5-130">Představuje seznam konfigurační prvky, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="5e7b5-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5e7b5-131">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="5e7b5-131">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e7b5-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e7b5-132">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5e7b5-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5e7b5-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5e7b5-134">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="5e7b5-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
