---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f77a613f4eb0456a0085096aa478d37c78122217
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946305"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="059ef-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="059ef-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="059ef-102">Představuje dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="059ef-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="059ef-103">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="059ef-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="059ef-104">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="059ef-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="059ef-105">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="059ef-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="059ef-106">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="059ef-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="059ef-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="059ef-107">\<system.serviceModel></span></span>\
<span data-ttu-id="059ef-108">\<sledování > </span><span class="sxs-lookup"><span data-stu-id="059ef-108">\<tracking></span></span>\
<span data-ttu-id="059ef-109">\<Profil TrackingProfile > </span><span class="sxs-lookup"><span data-stu-id="059ef-109">\<trackingProfile></span></span>\
<span data-ttu-id="059ef-110">\<> pracovního postupu </span><span class="sxs-lookup"><span data-stu-id="059ef-110">\<workflow></span></span>\
<span data-ttu-id="059ef-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="059ef-111">\<faultPropagationQueries></span></span>\
<span data-ttu-id="059ef-112">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="059ef-112">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="059ef-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="059ef-113">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="059ef-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="059ef-114">Attributes and Elements</span></span>

<span data-ttu-id="059ef-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="059ef-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="059ef-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="059ef-116">Attributes</span></span>

|<span data-ttu-id="059ef-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="059ef-117">Attribute</span></span>|<span data-ttu-id="059ef-118">Popis</span><span class="sxs-lookup"><span data-stu-id="059ef-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="059ef-119">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="059ef-119">activityName</span></span>|<span data-ttu-id="059ef-120">Řetězec, který určuje název aktivity obslužné rutiny chyb, která rozšířila chybu.</span><span class="sxs-lookup"><span data-stu-id="059ef-120">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="059ef-121">Výchozí hodnota je \*, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="059ef-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="059ef-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="059ef-122">faultHandlerActivityName</span></span>|<span data-ttu-id="059ef-123">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="059ef-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="059ef-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="059ef-124">Child Elements</span></span>

<span data-ttu-id="059ef-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="059ef-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="059ef-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="059ef-126">Parent Elements</span></span>

|<span data-ttu-id="059ef-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="059ef-127">Element</span></span>|<span data-ttu-id="059ef-128">Popis</span><span class="sxs-lookup"><span data-stu-id="059ef-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="059ef-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="059ef-129">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="059ef-130">Představuje seznam elementů konfigurace, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="059ef-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="059ef-131">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="059ef-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="059ef-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="059ef-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="059ef-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="059ef-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="059ef-134">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="059ef-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
