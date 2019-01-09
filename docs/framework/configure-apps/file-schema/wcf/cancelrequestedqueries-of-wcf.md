---
title: '&lt;cancelRequestedQueries&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 9cf2761bdab36d95b5077e36174565659230b512
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145442"
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="2a960-102">&lt;cancelRequestedQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="2a960-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="2a960-103">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="2a960-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="2a960-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="2a960-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="2a960-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2a960-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="2a960-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2a960-106">\<system.serviceModel></span></span>  
<span data-ttu-id="2a960-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="2a960-107">\<tracking></span></span>  
<span data-ttu-id="2a960-108">\<profily > \<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="2a960-108">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="2a960-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="2a960-109">\<workflow></span></span>  
<span data-ttu-id="2a960-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="2a960-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a960-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a960-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a960-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2a960-112">Attributes and elements</span></span>  

<span data-ttu-id="2a960-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2a960-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a960-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="2a960-114">Attributes</span></span>

<span data-ttu-id="2a960-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="2a960-115">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="2a960-116">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="2a960-116">Child elements</span></span>
  
|<span data-ttu-id="2a960-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="2a960-117">Element</span></span>|<span data-ttu-id="2a960-118">Popis</span><span class="sxs-lookup"><span data-stu-id="2a960-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a960-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="2a960-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="2a960-120">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="2a960-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a960-121">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="2a960-121">Parent elements</span></span>  
  
|<span data-ttu-id="2a960-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="2a960-122">Element</span></span>|<span data-ttu-id="2a960-123">Popis</span><span class="sxs-lookup"><span data-stu-id="2a960-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a960-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="2a960-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="2a960-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2a960-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a960-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a960-126">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="2a960-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="2a960-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2a960-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="2a960-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
