---
title: '&lt;cancelRequestedQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b3699985095fca59d5817a31c52b29fe7609a2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="df469-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="df469-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="df469-103">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="df469-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="df469-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="df469-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="df469-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="df469-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="df469-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="df469-106">\<system.serviceModel></span></span>  
<span data-ttu-id="df469-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="df469-107">\<tracking></span></span>  
<span data-ttu-id="df469-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="df469-108">\<trackingProfile></span></span>  
<span data-ttu-id="df469-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="df469-109">\<workflow></span></span>  
<span data-ttu-id="df469-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="df469-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df469-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df469-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df469-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="df469-112">Attributes and Elements</span></span>  
 <span data-ttu-id="df469-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="df469-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df469-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="df469-114">Attributes</span></span>  
 <span data-ttu-id="df469-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="df469-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="df469-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="df469-116">Child Elements</span></span>  
  
|<span data-ttu-id="df469-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="df469-117">Element</span></span>|<span data-ttu-id="df469-118">Popis</span><span class="sxs-lookup"><span data-stu-id="df469-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df469-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="df469-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="df469-120">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="df469-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df469-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="df469-121">Parent Elements</span></span>  
  
|<span data-ttu-id="df469-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="df469-122">Element</span></span>|<span data-ttu-id="df469-123">Popis</span><span class="sxs-lookup"><span data-stu-id="df469-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df469-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="df469-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="df469-125">Konfigurace elementu, který obsahuje všechny dotazy pro konkrétní pracovní tok identifikovaný **activityDefinitionId** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="df469-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df469-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="df469-126">See Also</span></span>  
 [<span data-ttu-id="df469-127">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="df469-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="df469-128">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="df469-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
