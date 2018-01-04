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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f31663d44774f84feab76f22f19400a955a3cf8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="dc96b-102">&lt;cancelRequestedQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="dc96b-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="dc96b-103">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="dc96b-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="dc96b-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="dc96b-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="dc96b-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="dc96b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="dc96b-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="dc96b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="dc96b-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="dc96b-107">\<tracking></span></span>  
<span data-ttu-id="dc96b-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="dc96b-108">\<trackingProfile></span></span>  
<span data-ttu-id="dc96b-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="dc96b-109">\<workflow></span></span>  
<span data-ttu-id="dc96b-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="dc96b-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc96b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc96b-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc96b-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dc96b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dc96b-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dc96b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc96b-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="dc96b-114">Attributes</span></span>  
 <span data-ttu-id="dc96b-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="dc96b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dc96b-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dc96b-116">Child Elements</span></span>  
  
|<span data-ttu-id="dc96b-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc96b-117">Element</span></span>|<span data-ttu-id="dc96b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="dc96b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc96b-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="dc96b-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="dc96b-120">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="dc96b-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc96b-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dc96b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="dc96b-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc96b-122">Element</span></span>|<span data-ttu-id="dc96b-123">Popis</span><span class="sxs-lookup"><span data-stu-id="dc96b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc96b-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="dc96b-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="dc96b-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dc96b-125">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc96b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc96b-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="dc96b-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="dc96b-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="dc96b-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="dc96b-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
