---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 09cbc43ae4db82dc80e6985131f8d6cc0c24b2ac
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152408"
---
# \<activityScheduledQuery>
<span data-ttu-id="a84c3-101">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="a84c3-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="a84c3-102">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="a84c3-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="a84c3-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="a84c3-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="a84c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a84c3-104">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a84c3-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a84c3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a84c3-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a84c3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a84c3-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="a84c3-107">Attributes</span></span>  
  
|<span data-ttu-id="a84c3-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="a84c3-108">Attribute</span></span>|<span data-ttu-id="a84c3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a84c3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a84c3-110">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="a84c3-110">activityName</span></span>|<span data-ttu-id="a84c3-111">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="a84c3-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="a84c3-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="a84c3-112">childActivityName</span></span>|<span data-ttu-id="a84c3-113">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="a84c3-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a84c3-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a84c3-114">Child Elements</span></span>  
 <span data-ttu-id="a84c3-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="a84c3-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a84c3-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a84c3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a84c3-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="a84c3-117">Element</span></span>|<span data-ttu-id="a84c3-118">Description</span><span class="sxs-lookup"><span data-stu-id="a84c3-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="a84c3-119">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="a84c3-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a84c3-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a84c3-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a84c3-121">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a84c3-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a84c3-122">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="a84c3-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
