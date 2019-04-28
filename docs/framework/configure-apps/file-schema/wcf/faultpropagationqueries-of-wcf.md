---
title: <faultPropagationQueries> služby WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: bc016827c5bb243bc83dbb53c1eda7eec1bfd8c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704008"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="abb89-102">\<faultPropagationQueries > služby WCF</span><span class="sxs-lookup"><span data-stu-id="abb89-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="abb89-103">Představuje kolekci dotazů, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="abb89-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="abb89-104">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="abb89-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="abb89-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="abb89-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="abb89-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="abb89-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="abb89-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="abb89-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="abb89-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="abb89-108">\<system.serviceModel></span></span>  
<span data-ttu-id="abb89-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="abb89-109">\<tracking></span></span>  
<span data-ttu-id="abb89-110">\<profiles></span><span class="sxs-lookup"><span data-stu-id="abb89-110">\<profiles></span></span>  
<span data-ttu-id="abb89-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="abb89-111">\<trackingProfile></span></span>  
<span data-ttu-id="abb89-112">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="abb89-112">\<workflow></span></span>  
<span data-ttu-id="abb89-113">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="abb89-113">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb89-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abb89-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abb89-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="abb89-115">Attributes and elements</span></span>

<span data-ttu-id="abb89-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="abb89-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="abb89-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="abb89-117">Attributes</span></span>

<span data-ttu-id="abb89-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="abb89-118">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="abb89-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="abb89-119">Child elements</span></span>

|<span data-ttu-id="abb89-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="abb89-120">Element</span></span>|<span data-ttu-id="abb89-121">Popis</span><span class="sxs-lookup"><span data-stu-id="abb89-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abb89-122">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="abb89-122">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="abb89-123">Dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="abb89-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="abb89-124">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="abb89-124">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="abb89-125">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="abb89-125">Parent elements</span></span>  
  
|<span data-ttu-id="abb89-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="abb89-126">Element</span></span>|<span data-ttu-id="abb89-127">Popis</span><span class="sxs-lookup"><span data-stu-id="abb89-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abb89-128">\<workflow></span><span class="sxs-lookup"><span data-stu-id="abb89-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="abb89-129">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="abb89-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="abb89-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abb89-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="abb89-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="abb89-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="abb89-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="abb89-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
