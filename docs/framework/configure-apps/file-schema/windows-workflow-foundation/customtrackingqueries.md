---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 663dda571990a86dc71ea927c4e97241e0ed3fc1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120078"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="9ad84-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="9ad84-101">\<customTrackingQueries></span></span>
<span data-ttu-id="9ad84-102">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="9ad84-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="9ad84-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="9ad84-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="9ad84-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9ad84-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9ad84-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9ad84-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9ad84-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="9ad84-106">\<tracking></span></span>  
<span data-ttu-id="9ad84-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9ad84-107">\<trackingProfile></span></span>  
<span data-ttu-id="9ad84-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9ad84-108">\<workflow></span></span>  
<span data-ttu-id="9ad84-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="9ad84-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ad84-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ad84-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ad84-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9ad84-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9ad84-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9ad84-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ad84-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="9ad84-113">Attributes</span></span>  
 <span data-ttu-id="9ad84-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="9ad84-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ad84-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9ad84-115">Child Elements</span></span>  
  
|<span data-ttu-id="9ad84-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="9ad84-116">Element</span></span>|<span data-ttu-id="9ad84-117">Popis</span><span class="sxs-lookup"><span data-stu-id="9ad84-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ad84-118">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="9ad84-118">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="9ad84-119">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="9ad84-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ad84-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9ad84-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9ad84-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="9ad84-121">Element</span></span>|<span data-ttu-id="9ad84-122">Popis</span><span class="sxs-lookup"><span data-stu-id="9ad84-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ad84-123">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9ad84-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9ad84-124">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9ad84-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ad84-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ad84-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9ad84-126">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9ad84-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9ad84-127">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="9ad84-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
