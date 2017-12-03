---
title: "&lt;bookmarkResumptionQuery&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 124b05d8e1ce9831a1efb3c6e62cc5e9fd3058fc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="d5440-102">&lt;bookmarkResumptionQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="d5440-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="d5440-103">Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d5440-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d5440-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="d5440-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="d5440-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d5440-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="d5440-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d5440-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d5440-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="d5440-107">\<tracking></span></span>  
<span data-ttu-id="d5440-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d5440-108">\<trackingProfile></span></span>  
<span data-ttu-id="d5440-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="d5440-109">\<workflow></span></span>  
<span data-ttu-id="d5440-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="d5440-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="d5440-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="d5440-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5440-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5440-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d5440-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d5440-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d5440-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d5440-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5440-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="d5440-115">Attributes</span></span>  
  
|<span data-ttu-id="d5440-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="d5440-116">Attribute</span></span>|<span data-ttu-id="d5440-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d5440-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d5440-118">name</span><span class="sxs-lookup"><span data-stu-id="d5440-118">name</span></span>|<span data-ttu-id="d5440-119">Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="d5440-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5440-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d5440-120">Child Elements</span></span>  
 <span data-ttu-id="d5440-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="d5440-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5440-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d5440-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d5440-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="d5440-123">Element</span></span>|<span data-ttu-id="d5440-124">Popis</span><span class="sxs-lookup"><span data-stu-id="d5440-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5440-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="d5440-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="d5440-126">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d5440-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5440-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5440-127">See Also</span></span>  
 <span data-ttu-id="d5440-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d5440-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="d5440-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d5440-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="d5440-130">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="d5440-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d5440-131">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="d5440-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
