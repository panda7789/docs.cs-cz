---
title: '&lt;cancelRequestedQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 5bc2e3ffeb93bdfcd45638d6b50e218c03706f42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520682"
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="a440f-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="a440f-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="a440f-103">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="a440f-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a440f-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="a440f-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="a440f-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a440f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a440f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a440f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a440f-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="a440f-107">\<tracking></span></span>  
<span data-ttu-id="a440f-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a440f-108">\<trackingProfile></span></span>  
<span data-ttu-id="a440f-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="a440f-109">\<workflow></span></span>  
<span data-ttu-id="a440f-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="a440f-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a440f-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a440f-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a440f-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a440f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a440f-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a440f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a440f-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="a440f-114">Attributes</span></span>  
 <span data-ttu-id="a440f-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="a440f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a440f-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a440f-116">Child Elements</span></span>  
  
|<span data-ttu-id="a440f-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="a440f-117">Element</span></span>|<span data-ttu-id="a440f-118">Popis</span><span class="sxs-lookup"><span data-stu-id="a440f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a440f-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="a440f-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="a440f-120">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="a440f-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a440f-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a440f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a440f-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="a440f-122">Element</span></span>|<span data-ttu-id="a440f-123">Popis</span><span class="sxs-lookup"><span data-stu-id="a440f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a440f-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a440f-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="a440f-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a440f-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a440f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a440f-126">See also</span></span>
- [<span data-ttu-id="a440f-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a440f-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a440f-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="a440f-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
