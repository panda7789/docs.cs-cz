---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 32a37fb3cc2b93046bea133f351185638b0d7545
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163160"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="a5084-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="a5084-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="a5084-102">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="a5084-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a5084-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="a5084-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="a5084-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a5084-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a5084-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a5084-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a5084-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="a5084-106">\<tracking></span></span>  
<span data-ttu-id="a5084-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a5084-107">\<trackingProfile></span></span>  
<span data-ttu-id="a5084-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="a5084-108">\<workflow></span></span>  
<span data-ttu-id="a5084-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="a5084-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5084-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5084-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5084-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a5084-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a5084-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a5084-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5084-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a5084-113">Attributes</span></span>  
 <span data-ttu-id="a5084-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="a5084-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5084-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a5084-115">Child Elements</span></span>  
  
|<span data-ttu-id="a5084-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="a5084-116">Element</span></span>|<span data-ttu-id="a5084-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a5084-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5084-118">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="a5084-118">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="a5084-119">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="a5084-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5084-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a5084-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a5084-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="a5084-121">Element</span></span>|<span data-ttu-id="a5084-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a5084-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5084-123">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="a5084-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="a5084-124">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a5084-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5084-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5084-125">See also</span></span>

- [<span data-ttu-id="a5084-126">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a5084-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a5084-127">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="a5084-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
