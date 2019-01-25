---
title: '&lt;faultPropagationQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 546b37279c8ba58f9dd9f07dabacb7af602ff232
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610055"
---
# <a name="ltfaultpropagationqueriesgt"></a><span data-ttu-id="f8213-102">&lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="f8213-102">&lt;faultPropagationQueries&gt;</span></span>
<span data-ttu-id="f8213-103">Představuje kolekci dotazů, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="f8213-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f8213-104">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="f8213-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="f8213-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="f8213-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="f8213-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="f8213-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="f8213-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f8213-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f8213-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f8213-108">\<system.serviceModel></span></span>  
<span data-ttu-id="f8213-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="f8213-109">\<tracking></span></span>  
<span data-ttu-id="f8213-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f8213-110">\<trackingProfile></span></span>  
<span data-ttu-id="f8213-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="f8213-111">\<workflow></span></span>  
<span data-ttu-id="f8213-112">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="f8213-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8213-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8213-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8213-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f8213-114">Attributes and Elements</span></span>  
 <span data-ttu-id="f8213-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f8213-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8213-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="f8213-116">Attributes</span></span>  
 <span data-ttu-id="f8213-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="f8213-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f8213-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f8213-118">Child Elements</span></span>  
  
|<span data-ttu-id="f8213-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="f8213-119">Element</span></span>|<span data-ttu-id="f8213-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f8213-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8213-121">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="f8213-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="f8213-122">Dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="f8213-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f8213-123">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="f8213-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8213-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f8213-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f8213-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="f8213-125">Element</span></span>|<span data-ttu-id="f8213-126">Popis</span><span class="sxs-lookup"><span data-stu-id="f8213-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8213-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f8213-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f8213-128">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f8213-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8213-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8213-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f8213-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="f8213-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f8213-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="f8213-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
