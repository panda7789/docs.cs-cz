---
title: <faultPropagationQuery> služby WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: e5793852d49a052d05f6cb2f4efbe166d67afc62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701044"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="5e73d-102">\<faultPropagationQuery > služby WCF</span><span class="sxs-lookup"><span data-stu-id="5e73d-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="5e73d-103">Představuje dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="5e73d-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5e73d-104">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="5e73d-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="5e73d-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="5e73d-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="5e73d-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="5e73d-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="5e73d-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5e73d-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="5e73d-108">\<system.serviceModel>\\</span><span class="sxs-lookup"><span data-stu-id="5e73d-108">\<system.serviceModel>\\</span></span>
<span data-ttu-id="5e73d-109">\<sledování > \\</span><span class="sxs-lookup"><span data-stu-id="5e73d-109">\<tracking>\\</span></span>
<span data-ttu-id="5e73d-110">\<profiles>\\</span><span class="sxs-lookup"><span data-stu-id="5e73d-110">\<profiles>\\</span></span>
<span data-ttu-id="5e73d-111">\<trackingProfile>\\</span><span class="sxs-lookup"><span data-stu-id="5e73d-111">\<trackingProfile>\\</span></span>
<span data-ttu-id="5e73d-112">\<pracovní postup > \\</span><span class="sxs-lookup"><span data-stu-id="5e73d-112">\<workflow>\\</span></span>
<span data-ttu-id="5e73d-113">\<faultPropagationQueries>\\</span><span class="sxs-lookup"><span data-stu-id="5e73d-113">\<faultPropagationQueries>\\</span></span>
<span data-ttu-id="5e73d-114">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="5e73d-114">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="5e73d-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e73d-115">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="5e73d-116">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5e73d-116">Attributes and elements</span></span>

<span data-ttu-id="5e73d-117">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5e73d-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5e73d-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="5e73d-118">Attributes</span></span>

|<span data-ttu-id="5e73d-119">Atribut</span><span class="sxs-lookup"><span data-stu-id="5e73d-119">Attribute</span></span>|<span data-ttu-id="5e73d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5e73d-120">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="5e73d-121">Řetězec, který určuje název aktivity obslužná rutina chyby, která chybu.</span><span class="sxs-lookup"><span data-stu-id="5e73d-121">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="5e73d-122">Výchozí hodnota je \*, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="5e73d-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="5e73d-123">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="5e73d-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5e73d-124">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="5e73d-124">Child elements</span></span>

<span data-ttu-id="5e73d-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="5e73d-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5e73d-126">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="5e73d-126">Parent elements</span></span>

|<span data-ttu-id="5e73d-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="5e73d-127">Element</span></span>|<span data-ttu-id="5e73d-128">Popis</span><span class="sxs-lookup"><span data-stu-id="5e73d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e73d-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="5e73d-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="5e73d-130">Představuje seznam konfigurační prvky, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="5e73d-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5e73d-131">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="5e73d-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="5e73d-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e73d-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5e73d-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5e73d-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5e73d-134">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="5e73d-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
