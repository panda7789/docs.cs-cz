---
title: <faultPropagationQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: aeb964fc8c96c8cb9aeb316bb95f9565fc4a7f18
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918946"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="9b379-102">\<faultPropagationQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="9b379-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="9b379-103">Představuje kolekci dotazů, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="9b379-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9b379-104">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="9b379-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="9b379-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="9b379-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="9b379-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="9b379-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="9b379-107">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9b379-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9b379-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9b379-108">\<system.serviceModel></span></span>  
<span data-ttu-id="9b379-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="9b379-109">\<tracking></span></span>  
<span data-ttu-id="9b379-110">\<profiles></span><span class="sxs-lookup"><span data-stu-id="9b379-110">\<profiles></span></span>  
<span data-ttu-id="9b379-111">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="9b379-111">\<trackingProfile></span></span>  
<span data-ttu-id="9b379-112">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="9b379-112">\<workflow></span></span>  
<span data-ttu-id="9b379-113">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="9b379-113">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b379-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b379-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b379-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9b379-115">Attributes and elements</span></span>

<span data-ttu-id="9b379-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9b379-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="9b379-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="9b379-117">Attributes</span></span>

<span data-ttu-id="9b379-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="9b379-118">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="9b379-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="9b379-119">Child elements</span></span>

|<span data-ttu-id="9b379-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="9b379-120">Element</span></span>|<span data-ttu-id="9b379-121">Popis</span><span class="sxs-lookup"><span data-stu-id="9b379-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b379-122">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="9b379-122">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="9b379-123">Dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="9b379-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9b379-124">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="9b379-124">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9b379-125">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="9b379-125">Parent elements</span></span>  
  
|<span data-ttu-id="9b379-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="9b379-126">Element</span></span>|<span data-ttu-id="9b379-127">Popis</span><span class="sxs-lookup"><span data-stu-id="9b379-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b379-128">\<workflow></span><span class="sxs-lookup"><span data-stu-id="9b379-128">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="9b379-129">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9b379-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b379-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b379-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9b379-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9b379-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9b379-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="9b379-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
