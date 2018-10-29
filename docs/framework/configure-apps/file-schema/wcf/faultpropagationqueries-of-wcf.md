---
title: '&lt;faultPropagationQueries&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 1db99a8d80fad5c0eca93777d87047b43371d048
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202117"
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="9008a-102">&lt;faultPropagationQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="9008a-102">&lt;faultPropagationQueries&gt; of WCF</span></span>

<span data-ttu-id="9008a-103">Představuje kolekci dotazů, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="9008a-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9008a-104">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="9008a-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="9008a-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="9008a-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="9008a-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="9008a-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="9008a-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9008a-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9008a-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9008a-108">\<system.serviceModel></span></span>  
<span data-ttu-id="9008a-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="9008a-109">\<tracking></span></span>  
<span data-ttu-id="9008a-110">\<profily ></span><span class="sxs-lookup"><span data-stu-id="9008a-110">\<profiles></span></span>  
<span data-ttu-id="9008a-111">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="9008a-111">\<trackingProfile></span></span>  
<span data-ttu-id="9008a-112">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9008a-112">\<workflow></span></span>  
<span data-ttu-id="9008a-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="9008a-113">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9008a-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9008a-114">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="9008a-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9008a-115">Attributes and elements</span></span>

<span data-ttu-id="9008a-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9008a-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="9008a-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="9008a-117">Attributes</span></span>

<span data-ttu-id="9008a-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="9008a-118">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="9008a-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="9008a-119">Child elements</span></span>

|<span data-ttu-id="9008a-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="9008a-120">Element</span></span>|<span data-ttu-id="9008a-121">Popis</span><span class="sxs-lookup"><span data-stu-id="9008a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9008a-122">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="9008a-122">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="9008a-123">Dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="9008a-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9008a-124">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="9008a-124">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9008a-125">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="9008a-125">Parent elements</span></span>  
  
|<span data-ttu-id="9008a-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="9008a-126">Element</span></span>|<span data-ttu-id="9008a-127">Popis</span><span class="sxs-lookup"><span data-stu-id="9008a-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9008a-128">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9008a-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9008a-129">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9008a-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9008a-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9008a-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9008a-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9008a-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9008a-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="9008a-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
