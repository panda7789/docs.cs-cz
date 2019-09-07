---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398720"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="beaeb-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="beaeb-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="beaeb-102">Představuje dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="beaeb-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="beaeb-103">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="beaeb-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="beaeb-104">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="beaeb-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="beaeb-105">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="beaeb-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="beaeb-106">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="beaeb-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="beaeb-107">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="beaeb-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="beaeb-108">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="beaeb-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="beaeb-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="beaeb-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="beaeb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="beaeb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="beaeb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="beaeb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="beaeb-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<faultPropagationQueries >** ](faultpropagationqueries.md)</span><span class="sxs-lookup"><span data-stu-id="beaeb-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)</span></span>\
<span data-ttu-id="beaeb-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQuery >**</span><span class="sxs-lookup"><span data-stu-id="beaeb-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**</span></span>

## <a name="syntax"></a><span data-ttu-id="beaeb-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="beaeb-114">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="beaeb-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="beaeb-115">Attributes and Elements</span></span>

<span data-ttu-id="beaeb-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="beaeb-116">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="beaeb-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="beaeb-117">Attributes</span></span>

|<span data-ttu-id="beaeb-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="beaeb-118">Attribute</span></span>|<span data-ttu-id="beaeb-119">Popis</span><span class="sxs-lookup"><span data-stu-id="beaeb-119">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="beaeb-120">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="beaeb-120">activityName</span></span>|<span data-ttu-id="beaeb-121">Řetězec, který určuje název aktivity obslužné rutiny chyb, která rozšířila chybu.</span><span class="sxs-lookup"><span data-stu-id="beaeb-121">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="beaeb-122">Výchozí hodnota je \*, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="beaeb-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="beaeb-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="beaeb-123">faultHandlerActivityName</span></span>|<span data-ttu-id="beaeb-124">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="beaeb-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="beaeb-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="beaeb-125">Child Elements</span></span>

<span data-ttu-id="beaeb-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="beaeb-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="beaeb-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="beaeb-127">Parent Elements</span></span>

|<span data-ttu-id="beaeb-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="beaeb-128">Element</span></span>|<span data-ttu-id="beaeb-129">Popis</span><span class="sxs-lookup"><span data-stu-id="beaeb-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="beaeb-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="beaeb-130">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="beaeb-131">Představuje seznam elementů konfigurace, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="beaeb-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="beaeb-132">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="beaeb-132">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="beaeb-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="beaeb-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="beaeb-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="beaeb-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="beaeb-135">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="beaeb-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
