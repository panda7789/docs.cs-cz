---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 0424c01397a95803b9e8502d90a55d1bd4c3b5e6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269390"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="fb0ac-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="fb0ac-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="fb0ac-102">Představuje kolekci dotazů, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="fb0ac-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="fb0ac-103">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="fb0ac-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="fb0ac-104">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="fb0ac-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="fb0ac-105">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="fb0ac-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="fb0ac-106">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="fb0ac-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="fb0ac-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fb0ac-107">\<system.serviceModel></span></span>  
<span data-ttu-id="fb0ac-108">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="fb0ac-108">\<tracking></span></span>  
<span data-ttu-id="fb0ac-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="fb0ac-109">\<trackingProfile></span></span>  
<span data-ttu-id="fb0ac-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="fb0ac-110">\<workflow></span></span>  
<span data-ttu-id="fb0ac-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="fb0ac-111">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb0ac-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb0ac-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb0ac-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fb0ac-113">Attributes and Elements</span></span>  
 <span data-ttu-id="fb0ac-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fb0ac-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb0ac-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="fb0ac-115">Attributes</span></span>  
 <span data-ttu-id="fb0ac-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="fb0ac-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fb0ac-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fb0ac-117">Child Elements</span></span>  
  
|<span data-ttu-id="fb0ac-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="fb0ac-118">Element</span></span>|<span data-ttu-id="fb0ac-119">Popis</span><span class="sxs-lookup"><span data-stu-id="fb0ac-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb0ac-120">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="fb0ac-120">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="fb0ac-121">Dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="fb0ac-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="fb0ac-122">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="fb0ac-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb0ac-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fb0ac-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fb0ac-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="fb0ac-124">Element</span></span>|<span data-ttu-id="fb0ac-125">Popis</span><span class="sxs-lookup"><span data-stu-id="fb0ac-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb0ac-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="fb0ac-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="fb0ac-127">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fb0ac-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb0ac-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb0ac-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fb0ac-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="fb0ac-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fb0ac-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="fb0ac-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
