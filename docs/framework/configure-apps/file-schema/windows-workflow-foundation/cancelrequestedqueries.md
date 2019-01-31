---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 989d6e99457108336c38fb1eece4c9ac2444c974
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271496"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="d4fb0-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="d4fb0-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="d4fb0-102">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d4fb0-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="d4fb0-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d4fb0-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d4fb0-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d4fb0-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d4fb0-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="d4fb0-106">\<tracking></span></span>  
<span data-ttu-id="d4fb0-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d4fb0-107">\<trackingProfile></span></span>  
<span data-ttu-id="d4fb0-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="d4fb0-108">\<workflow></span></span>  
<span data-ttu-id="d4fb0-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="d4fb0-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4fb0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4fb0-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4fb0-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d4fb0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d4fb0-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4fb0-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d4fb0-113">Attributes</span></span>  
 <span data-ttu-id="d4fb0-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="d4fb0-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d4fb0-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d4fb0-115">Child Elements</span></span>  
  
|<span data-ttu-id="d4fb0-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="d4fb0-116">Element</span></span>|<span data-ttu-id="d4fb0-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d4fb0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4fb0-118">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="d4fb0-118">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="d4fb0-119">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4fb0-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d4fb0-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d4fb0-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="d4fb0-121">Element</span></span>|<span data-ttu-id="d4fb0-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d4fb0-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4fb0-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="d4fb0-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="d4fb0-124">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4fb0-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4fb0-125">See also</span></span>
- [<span data-ttu-id="d4fb0-126">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d4fb0-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d4fb0-127">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="d4fb0-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
