---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 32a37fb3cc2b93046bea133f351185638b0d7545
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790244"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="1564c-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="1564c-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="1564c-102">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="1564c-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="1564c-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="1564c-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="1564c-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1564c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="1564c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1564c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="1564c-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="1564c-106">\<tracking></span></span>  
<span data-ttu-id="1564c-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1564c-107">\<trackingProfile></span></span>  
<span data-ttu-id="1564c-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="1564c-108">\<workflow></span></span>  
<span data-ttu-id="1564c-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="1564c-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1564c-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1564c-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1564c-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1564c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1564c-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1564c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1564c-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1564c-113">Attributes</span></span>  
 <span data-ttu-id="1564c-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="1564c-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1564c-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1564c-115">Child Elements</span></span>  
  
|<span data-ttu-id="1564c-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="1564c-116">Element</span></span>|<span data-ttu-id="1564c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="1564c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1564c-118">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="1564c-118">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="1564c-119">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="1564c-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1564c-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1564c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1564c-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="1564c-121">Element</span></span>|<span data-ttu-id="1564c-122">Popis</span><span class="sxs-lookup"><span data-stu-id="1564c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1564c-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="1564c-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="1564c-124">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1564c-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1564c-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1564c-125">See also</span></span>

- [<span data-ttu-id="1564c-126">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1564c-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1564c-127">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="1564c-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
