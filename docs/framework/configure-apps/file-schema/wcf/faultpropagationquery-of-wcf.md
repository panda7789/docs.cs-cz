---
title: <faultPropagationQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: 6ba6478ca500c0a8ef150966a97898f8743ffdf8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925623"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="5031d-102">\<faultPropagationQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="5031d-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="5031d-103">Představuje dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="5031d-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5031d-104">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="5031d-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="5031d-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="5031d-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="5031d-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="5031d-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="5031d-107">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5031d-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="5031d-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5031d-108">\<system.serviceModel></span></span>\
<span data-ttu-id="5031d-109">\<sledování > </span><span class="sxs-lookup"><span data-stu-id="5031d-109">\<tracking></span></span>\
<span data-ttu-id="5031d-110">\<> profilů </span><span class="sxs-lookup"><span data-stu-id="5031d-110">\<profiles></span></span>\
<span data-ttu-id="5031d-111">\<Profil TrackingProfile > </span><span class="sxs-lookup"><span data-stu-id="5031d-111">\<trackingProfile></span></span>\
<span data-ttu-id="5031d-112">\<> pracovního postupu </span><span class="sxs-lookup"><span data-stu-id="5031d-112">\<workflow></span></span>\
<span data-ttu-id="5031d-113">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="5031d-113">\<faultPropagationQueries></span></span>\
<span data-ttu-id="5031d-114">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="5031d-114">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="5031d-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5031d-115">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="5031d-116">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5031d-116">Attributes and elements</span></span>

<span data-ttu-id="5031d-117">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5031d-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5031d-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="5031d-118">Attributes</span></span>

|<span data-ttu-id="5031d-119">Atribut</span><span class="sxs-lookup"><span data-stu-id="5031d-119">Attribute</span></span>|<span data-ttu-id="5031d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5031d-120">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="5031d-121">Řetězec, který určuje název aktivity obslužné rutiny chyb, která rozšířila chybu.</span><span class="sxs-lookup"><span data-stu-id="5031d-121">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="5031d-122">Výchozí hodnota je \*, což znamená, že jsou vraceny záznamy o šíření chyb pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="5031d-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="5031d-123">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="5031d-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5031d-124">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="5031d-124">Child elements</span></span>

<span data-ttu-id="5031d-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="5031d-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5031d-126">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="5031d-126">Parent elements</span></span>

|<span data-ttu-id="5031d-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="5031d-127">Element</span></span>|<span data-ttu-id="5031d-128">Popis</span><span class="sxs-lookup"><span data-stu-id="5031d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5031d-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="5031d-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="5031d-130">Představuje seznam elementů konfigurace, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="5031d-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5031d-131">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="5031d-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="5031d-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5031d-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5031d-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5031d-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5031d-134">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="5031d-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
