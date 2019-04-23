---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 402b938913575adfa9125b981dc2913680f07b73
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204039"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="c9b6f-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="c9b6f-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="c9b6f-102">Představuje kolekci dotazů, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="c9b6f-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c9b6f-103">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="c9b6f-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="c9b6f-104">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="c9b6f-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="c9b6f-105">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="c9b6f-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="c9b6f-106">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c9b6f-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c9b6f-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c9b6f-107">\<system.serviceModel></span></span>  
<span data-ttu-id="c9b6f-108">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="c9b6f-108">\<tracking></span></span>  
<span data-ttu-id="c9b6f-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c9b6f-109">\<trackingProfile></span></span>  
<span data-ttu-id="c9b6f-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="c9b6f-110">\<workflow></span></span>  
<span data-ttu-id="c9b6f-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="c9b6f-111">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9b6f-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9b6f-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9b6f-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c9b6f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c9b6f-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c9b6f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9b6f-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="c9b6f-115">Attributes</span></span>  
 <span data-ttu-id="c9b6f-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="c9b6f-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c9b6f-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c9b6f-117">Child Elements</span></span>  
  
|<span data-ttu-id="c9b6f-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="c9b6f-118">Element</span></span>|<span data-ttu-id="c9b6f-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c9b6f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9b6f-120">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="c9b6f-120">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="c9b6f-121">Dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="c9b6f-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c9b6f-122">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="c9b6f-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9b6f-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c9b6f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c9b6f-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="c9b6f-124">Element</span></span>|<span data-ttu-id="c9b6f-125">Popis</span><span class="sxs-lookup"><span data-stu-id="c9b6f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9b6f-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c9b6f-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c9b6f-127">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c9b6f-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9b6f-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9b6f-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c9b6f-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c9b6f-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c9b6f-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="c9b6f-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
