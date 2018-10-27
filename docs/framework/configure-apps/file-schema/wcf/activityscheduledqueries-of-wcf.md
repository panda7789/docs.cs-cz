---
title: '&lt;activityScheduledQueries&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 35bcb0dc0c33d30eee566869579edb32f131f495
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452693"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="f104f-102">&lt;activityScheduledQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="f104f-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="f104f-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="f104f-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="f104f-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="f104f-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="f104f-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f104f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f104f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f104f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f104f-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="f104f-107">\<tracking></span></span>  
<span data-ttu-id="f104f-108">\<profily ></span><span class="sxs-lookup"><span data-stu-id="f104f-108">\<profiles></span></span>  
<span data-ttu-id="f104f-109">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f104f-109">\<trackingProfile></span></span>  
<span data-ttu-id="f104f-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="f104f-110">\<workflow></span></span>  
<span data-ttu-id="f104f-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="f104f-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f104f-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f104f-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"   
                                  childActivityName="String"/>
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f104f-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f104f-113">Attributes and elements</span></span>  

<span data-ttu-id="f104f-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f104f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f104f-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="f104f-115">Attributes</span></span>  

<span data-ttu-id="f104f-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="f104f-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f104f-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="f104f-117">Child elements</span></span>  
  
|<span data-ttu-id="f104f-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="f104f-118">Element</span></span>|<span data-ttu-id="f104f-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f104f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f104f-120">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="f104f-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="f104f-121">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="f104f-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f104f-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="f104f-122">Parent elements</span></span>  
  
|<span data-ttu-id="f104f-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="f104f-123">Element</span></span>|<span data-ttu-id="f104f-124">Popis</span><span class="sxs-lookup"><span data-stu-id="f104f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f104f-125">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="f104f-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f104f-126">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f104f-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f104f-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f104f-127">See also</span></span>  

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="f104f-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="f104f-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f104f-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="f104f-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
