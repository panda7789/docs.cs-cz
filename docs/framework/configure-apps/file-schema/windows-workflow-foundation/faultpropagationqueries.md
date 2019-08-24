---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: b8052138a729fcba7cb158d81a63126f59e0c4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69988735"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="42514-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="42514-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="42514-102">Představuje kolekci dotazů, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="42514-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="42514-103">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="42514-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="42514-104">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="42514-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="42514-105">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="42514-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="42514-106">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="42514-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="42514-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="42514-107">\<system.serviceModel></span></span>  
<span data-ttu-id="42514-108">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="42514-108">\<tracking></span></span>  
<span data-ttu-id="42514-109">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="42514-109">\<trackingProfile></span></span>  
<span data-ttu-id="42514-110">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="42514-110">\<workflow></span></span>  
<span data-ttu-id="42514-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="42514-111">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42514-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42514-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42514-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="42514-113">Attributes and Elements</span></span>  
 <span data-ttu-id="42514-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="42514-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42514-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="42514-115">Attributes</span></span>  
 <span data-ttu-id="42514-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="42514-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="42514-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="42514-117">Child Elements</span></span>  
  
|<span data-ttu-id="42514-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="42514-118">Element</span></span>|<span data-ttu-id="42514-119">Popis</span><span class="sxs-lookup"><span data-stu-id="42514-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42514-120">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="42514-120">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="42514-121">Dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="42514-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="42514-122">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="42514-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="42514-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="42514-123">Parent Elements</span></span>  
  
|<span data-ttu-id="42514-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="42514-124">Element</span></span>|<span data-ttu-id="42514-125">Popis</span><span class="sxs-lookup"><span data-stu-id="42514-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42514-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="42514-126">\<workflow></span></span>](workflow.md)|<span data-ttu-id="42514-127">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="42514-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42514-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42514-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="42514-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="42514-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="42514-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="42514-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
