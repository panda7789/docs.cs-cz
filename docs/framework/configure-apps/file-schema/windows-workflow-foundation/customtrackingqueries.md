---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 663dda571990a86dc71ea927c4e97241e0ed3fc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120078"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="d454d-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="d454d-101">\<customTrackingQueries></span></span>
<span data-ttu-id="d454d-102">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="d454d-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="d454d-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="d454d-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="d454d-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d454d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d454d-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d454d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d454d-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="d454d-106">\<tracking></span></span>  
<span data-ttu-id="d454d-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d454d-107">\<trackingProfile></span></span>  
<span data-ttu-id="d454d-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="d454d-108">\<workflow></span></span>  
<span data-ttu-id="d454d-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="d454d-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d454d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d454d-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d454d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d454d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d454d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d454d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d454d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d454d-113">Attributes</span></span>  
 <span data-ttu-id="d454d-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="d454d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d454d-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d454d-115">Child Elements</span></span>  
  
|<span data-ttu-id="d454d-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="d454d-116">Element</span></span>|<span data-ttu-id="d454d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d454d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d454d-118">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="d454d-118">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="d454d-119">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="d454d-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d454d-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d454d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d454d-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="d454d-121">Element</span></span>|<span data-ttu-id="d454d-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d454d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d454d-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d454d-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="d454d-124">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d454d-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d454d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d454d-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d454d-126">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d454d-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d454d-127">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="d454d-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
