---
title: '&lt;customTrackingQueries&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 060e2b5c8efd51f6245a39bd9562a69f0111fd41
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50038783"
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="a22c0-102">&lt;customTrackingQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="a22c0-102">&lt;customTrackingQueries&gt; of WCF</span></span>

<span data-ttu-id="a22c0-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="a22c0-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="a22c0-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="a22c0-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="a22c0-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a22c0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="a22c0-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a22c0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a22c0-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="a22c0-107">\<tracking></span></span>  
<span data-ttu-id="a22c0-108">\<profily ></span><span class="sxs-lookup"><span data-stu-id="a22c0-108">\<profiles></span></span>  
<span data-ttu-id="a22c0-109">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="a22c0-109">\<trackingProfile></span></span>  
<span data-ttu-id="a22c0-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="a22c0-110">\<workflow></span></span>  
<span data-ttu-id="a22c0-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="a22c0-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a22c0-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a22c0-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a22c0-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a22c0-113">Attributes and elements</span></span>

<span data-ttu-id="a22c0-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a22c0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a22c0-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="a22c0-115">Attributes</span></span>

<span data-ttu-id="a22c0-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="a22c0-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="a22c0-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="a22c0-117">Child elements</span></span>
  
|<span data-ttu-id="a22c0-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="a22c0-118">Element</span></span>|<span data-ttu-id="a22c0-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a22c0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a22c0-120">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="a22c0-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="a22c0-121">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="a22c0-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a22c0-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="a22c0-122">Parent elements</span></span>  
  
|<span data-ttu-id="a22c0-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="a22c0-123">Element</span></span>|<span data-ttu-id="a22c0-124">Popis</span><span class="sxs-lookup"><span data-stu-id="a22c0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a22c0-125">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="a22c0-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="a22c0-126">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a22c0-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a22c0-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a22c0-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
- [<span data-ttu-id="a22c0-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a22c0-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="a22c0-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="a22c0-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
