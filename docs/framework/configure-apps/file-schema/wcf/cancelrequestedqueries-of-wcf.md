---
title: '&lt;cancelRequestedQueries&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 4d746290f01e702979d1dd0165ad3fc5299e1b75
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087749"
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="8dadc-102">&lt;cancelRequestedQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="8dadc-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="8dadc-103">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="8dadc-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8dadc-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="8dadc-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="8dadc-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8dadc-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="8dadc-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8dadc-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8dadc-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="8dadc-107">\<tracking></span></span>  
<span data-ttu-id="8dadc-108">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="8dadc-108">\<trackingProfile></span></span>  
<span data-ttu-id="8dadc-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="8dadc-109">\<workflow></span></span>  
<span data-ttu-id="8dadc-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="8dadc-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dadc-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dadc-111">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="8dadc-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8dadc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8dadc-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8dadc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dadc-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="8dadc-114">Attributes</span></span>  
 <span data-ttu-id="8dadc-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="8dadc-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8dadc-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8dadc-116">Child Elements</span></span>  
  
|<span data-ttu-id="8dadc-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="8dadc-117">Element</span></span>|<span data-ttu-id="8dadc-118">Popis</span><span class="sxs-lookup"><span data-stu-id="8dadc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8dadc-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="8dadc-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="8dadc-120">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="8dadc-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8dadc-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8dadc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8dadc-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="8dadc-122">Element</span></span>|<span data-ttu-id="8dadc-123">Popis</span><span class="sxs-lookup"><span data-stu-id="8dadc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8dadc-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="8dadc-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="8dadc-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8dadc-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8dadc-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="8dadc-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="8dadc-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="8dadc-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8dadc-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="8dadc-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
