---
title: '&lt;activityScheduledQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 6192fea9a520a3f453593e5efac964a5d32a492f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756290"
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="da4b0-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="da4b0-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="da4b0-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="da4b0-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="da4b0-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="da4b0-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="da4b0-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="da4b0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="da4b0-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="da4b0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="da4b0-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="da4b0-107">\<tracking></span></span>  
<span data-ttu-id="da4b0-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="da4b0-108">\<trackingProfile></span></span>  
<span data-ttu-id="da4b0-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="da4b0-109">\<workflow></span></span>  
<span data-ttu-id="da4b0-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="da4b0-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da4b0-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da4b0-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da4b0-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="da4b0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="da4b0-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="da4b0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da4b0-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="da4b0-114">Attributes</span></span>  
 <span data-ttu-id="da4b0-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="da4b0-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="da4b0-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="da4b0-116">Child Elements</span></span>  
  
|<span data-ttu-id="da4b0-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="da4b0-117">Element</span></span>|<span data-ttu-id="da4b0-118">Popis</span><span class="sxs-lookup"><span data-stu-id="da4b0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da4b0-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="da4b0-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="da4b0-120">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="da4b0-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da4b0-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="da4b0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="da4b0-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="da4b0-122">Element</span></span>|<span data-ttu-id="da4b0-123">Popis</span><span class="sxs-lookup"><span data-stu-id="da4b0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da4b0-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="da4b0-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="da4b0-125">Konfigurace elementu, který obsahuje všechny dotazy pro konkrétní pracovní tok identifikovaný **activityDefinitionId** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="da4b0-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da4b0-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="da4b0-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="da4b0-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="da4b0-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="da4b0-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="da4b0-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
