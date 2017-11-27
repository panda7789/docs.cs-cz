---
title: "&lt;cancelRequestedQueries&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7a5501965f746fe85ad07e396f005beb8e12f3d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="6ed4e-102">&lt;cancelRequestedQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="6ed4e-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="6ed4e-103">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="6ed4e-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6ed4e-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="6ed4e-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="6ed4e-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6ed4e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="6ed4e-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6ed4e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6ed4e-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="6ed4e-107">\<tracking></span></span>  
<span data-ttu-id="6ed4e-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="6ed4e-108">\<trackingProfile></span></span>  
<span data-ttu-id="6ed4e-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="6ed4e-109">\<workflow></span></span>  
<span data-ttu-id="6ed4e-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="6ed4e-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed4e-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ed4e-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ed4e-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6ed4e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6ed4e-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6ed4e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ed4e-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="6ed4e-114">Attributes</span></span>  
 <span data-ttu-id="6ed4e-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="6ed4e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6ed4e-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6ed4e-116">Child Elements</span></span>  
  
|<span data-ttu-id="6ed4e-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="6ed4e-117">Element</span></span>|<span data-ttu-id="6ed4e-118">Popis</span><span class="sxs-lookup"><span data-stu-id="6ed4e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ed4e-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="6ed4e-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="6ed4e-120">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="6ed4e-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6ed4e-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6ed4e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6ed4e-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="6ed4e-122">Element</span></span>|<span data-ttu-id="6ed4e-123">Popis</span><span class="sxs-lookup"><span data-stu-id="6ed4e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ed4e-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="6ed4e-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="6ed4e-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6ed4e-125">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ed4e-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ed4e-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="6ed4e-127">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="6ed4e-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="6ed4e-128">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="6ed4e-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
