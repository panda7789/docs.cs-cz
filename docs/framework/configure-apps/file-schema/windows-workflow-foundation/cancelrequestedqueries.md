---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 32a37fb3cc2b93046bea133f351185638b0d7545
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163160"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="4fa0f-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="4fa0f-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="4fa0f-102">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="4fa0f-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4fa0f-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="4fa0f-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="4fa0f-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4fa0f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4fa0f-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4fa0f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="4fa0f-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="4fa0f-106">\<tracking></span></span>  
<span data-ttu-id="4fa0f-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4fa0f-107">\<trackingProfile></span></span>  
<span data-ttu-id="4fa0f-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="4fa0f-108">\<workflow></span></span>  
<span data-ttu-id="4fa0f-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="4fa0f-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fa0f-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fa0f-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fa0f-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4fa0f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4fa0f-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4fa0f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fa0f-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="4fa0f-113">Attributes</span></span>  
 <span data-ttu-id="4fa0f-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="4fa0f-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4fa0f-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4fa0f-115">Child Elements</span></span>  
  
|<span data-ttu-id="4fa0f-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="4fa0f-116">Element</span></span>|<span data-ttu-id="4fa0f-117">Popis</span><span class="sxs-lookup"><span data-stu-id="4fa0f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fa0f-118">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="4fa0f-118">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="4fa0f-119">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="4fa0f-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4fa0f-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4fa0f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4fa0f-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="4fa0f-121">Element</span></span>|<span data-ttu-id="4fa0f-122">Popis</span><span class="sxs-lookup"><span data-stu-id="4fa0f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fa0f-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="4fa0f-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="4fa0f-124">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4fa0f-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fa0f-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fa0f-125">See also</span></span>

- [<span data-ttu-id="4fa0f-126">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="4fa0f-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4fa0f-127">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="4fa0f-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
