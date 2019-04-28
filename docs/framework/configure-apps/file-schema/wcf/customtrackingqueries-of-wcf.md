---
title: <customTrackingQueries> služby WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 8b317cc289853902592e145e34b6e7bf5f84763b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704164"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="6c4f1-102">\<customTrackingQueries > služby WCF</span><span class="sxs-lookup"><span data-stu-id="6c4f1-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="6c4f1-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="6c4f1-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="6c4f1-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="6c4f1-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="6c4f1-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6c4f1-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="6c4f1-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6c4f1-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6c4f1-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="6c4f1-107">\<tracking></span></span>  
<span data-ttu-id="6c4f1-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="6c4f1-108">\<profiles></span></span>  
<span data-ttu-id="6c4f1-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="6c4f1-109">\<trackingProfile></span></span>  
<span data-ttu-id="6c4f1-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="6c4f1-110">\<workflow></span></span>  
<span data-ttu-id="6c4f1-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="6c4f1-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c4f1-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c4f1-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c4f1-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6c4f1-113">Attributes and elements</span></span>

<span data-ttu-id="6c4f1-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6c4f1-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c4f1-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="6c4f1-115">Attributes</span></span>

<span data-ttu-id="6c4f1-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="6c4f1-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="6c4f1-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="6c4f1-117">Child elements</span></span>
  
|<span data-ttu-id="6c4f1-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="6c4f1-118">Element</span></span>|<span data-ttu-id="6c4f1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="6c4f1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c4f1-120">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="6c4f1-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="6c4f1-121">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="6c4f1-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c4f1-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="6c4f1-122">Parent elements</span></span>  
  
|<span data-ttu-id="6c4f1-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="6c4f1-123">Element</span></span>|<span data-ttu-id="6c4f1-124">Popis</span><span class="sxs-lookup"><span data-stu-id="6c4f1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c4f1-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="6c4f1-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="6c4f1-126">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6c4f1-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c4f1-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c4f1-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6c4f1-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6c4f1-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6c4f1-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="6c4f1-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
