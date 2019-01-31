---
title: <cancelRequestedQueries> služby WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: a9364fc53c7eb62a240206f6c81bd434b25c3f40
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289468"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="ba822-102">\<cancelRequestedQueries > služby WCF</span><span class="sxs-lookup"><span data-stu-id="ba822-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="ba822-103">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="ba822-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ba822-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="ba822-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="ba822-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ba822-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ba822-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ba822-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ba822-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="ba822-107">\<tracking></span></span>  
<span data-ttu-id="ba822-108">\<profiles> \<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ba822-108">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="ba822-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="ba822-109">\<workflow></span></span>  
<span data-ttu-id="ba822-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="ba822-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba822-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba822-111">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba822-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ba822-112">Attributes and elements</span></span>  

<span data-ttu-id="ba822-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ba822-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba822-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="ba822-114">Attributes</span></span>

<span data-ttu-id="ba822-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="ba822-115">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="ba822-116">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="ba822-116">Child elements</span></span>
  
|<span data-ttu-id="ba822-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="ba822-117">Element</span></span>|<span data-ttu-id="ba822-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ba822-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba822-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="ba822-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="ba822-120">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="ba822-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba822-121">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="ba822-121">Parent elements</span></span>  
  
|<span data-ttu-id="ba822-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="ba822-122">Element</span></span>|<span data-ttu-id="ba822-123">Popis</span><span class="sxs-lookup"><span data-stu-id="ba822-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba822-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="ba822-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="ba822-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ba822-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba822-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba822-126">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="ba822-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ba822-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ba822-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="ba822-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
