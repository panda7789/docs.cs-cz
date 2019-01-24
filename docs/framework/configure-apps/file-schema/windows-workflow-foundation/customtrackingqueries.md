---
title: '&lt;customTrackingQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 757bbe500ec3edccef465b7ff23b2c974e4a5011
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598838"
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="6e22d-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="6e22d-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="6e22d-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="6e22d-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="6e22d-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="6e22d-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="6e22d-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6e22d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="6e22d-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6e22d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6e22d-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="6e22d-107">\<tracking></span></span>  
<span data-ttu-id="6e22d-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="6e22d-108">\<trackingProfile></span></span>  
<span data-ttu-id="6e22d-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="6e22d-109">\<workflow></span></span>  
<span data-ttu-id="6e22d-110">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="6e22d-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e22d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e22d-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e22d-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6e22d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6e22d-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6e22d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e22d-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="6e22d-114">Attributes</span></span>  
 <span data-ttu-id="6e22d-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="6e22d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6e22d-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6e22d-116">Child Elements</span></span>  
  
|<span data-ttu-id="6e22d-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e22d-117">Element</span></span>|<span data-ttu-id="6e22d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="6e22d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e22d-119">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="6e22d-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="6e22d-120">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="6e22d-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e22d-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6e22d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6e22d-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e22d-122">Element</span></span>|<span data-ttu-id="6e22d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="6e22d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e22d-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="6e22d-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="6e22d-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6e22d-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e22d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e22d-126">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6e22d-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6e22d-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6e22d-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="6e22d-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
