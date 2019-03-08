---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f3e281ff8a9de9be41dd6ad9d01ab52798d8e89e
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679356"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="a819f-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="a819f-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="a819f-102">Představuje dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="a819f-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a819f-103">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="a819f-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="a819f-104">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="a819f-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="a819f-105">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="a819f-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="a819f-106">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a819f-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="a819f-107">\<system.serviceModel>\\</span><span class="sxs-lookup"><span data-stu-id="a819f-107">\<system.serviceModel>\\</span></span>
<span data-ttu-id="a819f-108">\<sledování > \\</span><span class="sxs-lookup"><span data-stu-id="a819f-108">\<tracking>\\</span></span>
<span data-ttu-id="a819f-109">\<trackingProfile>\\</span><span class="sxs-lookup"><span data-stu-id="a819f-109">\<trackingProfile>\\</span></span>
<span data-ttu-id="a819f-110">\<pracovní postup > \\</span><span class="sxs-lookup"><span data-stu-id="a819f-110">\<workflow>\\</span></span>
<span data-ttu-id="a819f-111">\<faultPropagationQueries>\\</span><span class="sxs-lookup"><span data-stu-id="a819f-111">\<faultPropagationQueries>\\</span></span>
<span data-ttu-id="a819f-112">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="a819f-112">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="a819f-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a819f-113">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="a819f-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a819f-114">Attributes and Elements</span></span>

<span data-ttu-id="a819f-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a819f-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a819f-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="a819f-116">Attributes</span></span>

|<span data-ttu-id="a819f-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="a819f-117">Attribute</span></span>|<span data-ttu-id="a819f-118">Popis</span><span class="sxs-lookup"><span data-stu-id="a819f-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="a819f-119">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="a819f-119">activityName</span></span>|<span data-ttu-id="a819f-120">Řetězec, který určuje název aktivity obslužná rutina chyby, která chybu.</span><span class="sxs-lookup"><span data-stu-id="a819f-120">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="a819f-121">Výchozí hodnota je \*, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="a819f-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="a819f-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="a819f-122">faultHandlerActivityName</span></span>|<span data-ttu-id="a819f-123">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="a819f-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a819f-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a819f-124">Child Elements</span></span>

<span data-ttu-id="a819f-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="a819f-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a819f-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a819f-126">Parent Elements</span></span>

|<span data-ttu-id="a819f-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="a819f-127">Element</span></span>|<span data-ttu-id="a819f-128">Popis</span><span class="sxs-lookup"><span data-stu-id="a819f-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a819f-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="a819f-129">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="a819f-130">Představuje seznam konfigurační prvky, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="a819f-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a819f-131">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="a819f-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a819f-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a819f-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a819f-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a819f-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a819f-134">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="a819f-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
