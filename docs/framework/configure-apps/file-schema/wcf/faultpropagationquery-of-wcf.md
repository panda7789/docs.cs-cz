---
title: <faultPropagationQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855329"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="ed281-102">\<faultPropagationQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="ed281-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="ed281-103">Představuje dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="ed281-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ed281-104">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="ed281-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="ed281-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="ed281-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="ed281-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="ed281-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="ed281-107">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ed281-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="ed281-108">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed281-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ed281-109">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ed281-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ed281-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ed281-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="ed281-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="ed281-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="ed281-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ed281-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="ed281-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ed281-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="ed281-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<faultPropagationQueries >** ](faultpropagationqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ed281-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)</span></span>\
<span data-ttu-id="ed281-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQuery >**</span><span class="sxs-lookup"><span data-stu-id="ed281-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="ed281-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed281-116">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="ed281-117">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ed281-117">Attributes and elements</span></span>

<span data-ttu-id="ed281-118">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ed281-118">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ed281-119">Atributy</span><span class="sxs-lookup"><span data-stu-id="ed281-119">Attributes</span></span>

|<span data-ttu-id="ed281-120">Atribut</span><span class="sxs-lookup"><span data-stu-id="ed281-120">Attribute</span></span>|<span data-ttu-id="ed281-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ed281-121">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="ed281-122">Řetězec, který určuje název aktivity obslužné rutiny chyb, která rozšířila chybu.</span><span class="sxs-lookup"><span data-stu-id="ed281-122">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="ed281-123">Výchozí hodnota je \*, což znamená, že jsou vraceny záznamy o šíření chyb pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="ed281-123">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="ed281-124">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="ed281-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ed281-125">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="ed281-125">Child elements</span></span>

<span data-ttu-id="ed281-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="ed281-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ed281-127">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="ed281-127">Parent elements</span></span>

|<span data-ttu-id="ed281-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="ed281-128">Element</span></span>|<span data-ttu-id="ed281-129">Popis</span><span class="sxs-lookup"><span data-stu-id="ed281-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed281-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="ed281-130">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="ed281-131">Představuje seznam elementů konfigurace, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="ed281-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ed281-132">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="ed281-132">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ed281-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed281-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ed281-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ed281-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ed281-135">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="ed281-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
