---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398720"
---
# \<faultPropagationQuery>

<span data-ttu-id="3b6ba-101">Představuje dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="3b6ba-101">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="3b6ba-102">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="3b6ba-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="3b6ba-103">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="3b6ba-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="3b6ba-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="3b6ba-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="3b6ba-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3b6ba-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**

## <a name="syntax"></a><span data-ttu-id="3b6ba-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b6ba-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="3b6ba-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3b6ba-107">Attributes and Elements</span></span>

<span data-ttu-id="3b6ba-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3b6ba-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3b6ba-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="3b6ba-109">Attributes</span></span>

|<span data-ttu-id="3b6ba-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="3b6ba-110">Attribute</span></span>|<span data-ttu-id="3b6ba-111">Popis</span><span class="sxs-lookup"><span data-stu-id="3b6ba-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="3b6ba-112">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="3b6ba-112">activityName</span></span>|<span data-ttu-id="3b6ba-113">Řetězec, který určuje název aktivity obslužné rutiny chyb, která rozšířila chybu.</span><span class="sxs-lookup"><span data-stu-id="3b6ba-113">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="3b6ba-114">Výchozí hodnota je \*, což znamená, že chyby šíření záznamy budou vráceny pro všechny aktivity.</span><span class="sxs-lookup"><span data-stu-id="3b6ba-114">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="3b6ba-115">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="3b6ba-115">faultHandlerActivityName</span></span>|<span data-ttu-id="3b6ba-116">Řetězec, který určuje název aktivity, který byl zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="3b6ba-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3b6ba-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3b6ba-117">Child Elements</span></span>

<span data-ttu-id="3b6ba-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="3b6ba-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3b6ba-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3b6ba-119">Parent Elements</span></span>

|<span data-ttu-id="3b6ba-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="3b6ba-120">Element</span></span>|<span data-ttu-id="3b6ba-121">Description</span><span class="sxs-lookup"><span data-stu-id="3b6ba-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="3b6ba-122">Představuje seznam elementů konfigurace, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="3b6ba-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="3b6ba-123">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="3b6ba-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3b6ba-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b6ba-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3b6ba-125">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="3b6ba-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3b6ba-126">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="3b6ba-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
