---
title: <faultPropagationQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855329"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="770e1-102">\<faultPropagationQuery>služby WCF</span><span class="sxs-lookup"><span data-stu-id="770e1-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="770e1-103">Představuje dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="770e1-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="770e1-104">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="770e1-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="770e1-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="770e1-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="770e1-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="770e1-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="770e1-107">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="770e1-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**  

## <a name="syntax"></a><span data-ttu-id="770e1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="770e1-108">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="770e1-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="770e1-109">Attributes and elements</span></span>

<span data-ttu-id="770e1-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="770e1-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="770e1-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="770e1-111">Attributes</span></span>

|<span data-ttu-id="770e1-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="770e1-112">Attribute</span></span>|<span data-ttu-id="770e1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="770e1-113">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="770e1-114">Řetězec, který určuje název aktivity obslužné rutiny chyb, která rozšířila chybu.</span><span class="sxs-lookup"><span data-stu-id="770e1-114">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="770e1-115">Výchozí hodnota je \* , což znamená, že jsou vraceny záznamy o šíření chyb pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="770e1-115">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="770e1-116">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="770e1-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="770e1-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="770e1-117">Child elements</span></span>

<span data-ttu-id="770e1-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="770e1-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="770e1-119">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="770e1-119">Parent elements</span></span>

|<span data-ttu-id="770e1-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="770e1-120">Element</span></span>|<span data-ttu-id="770e1-121">Description</span><span class="sxs-lookup"><span data-stu-id="770e1-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="770e1-122">Představuje seznam elementů konfigurace, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="770e1-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="770e1-123">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="770e1-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="770e1-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="770e1-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="770e1-125">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="770e1-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="770e1-126">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="770e1-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
