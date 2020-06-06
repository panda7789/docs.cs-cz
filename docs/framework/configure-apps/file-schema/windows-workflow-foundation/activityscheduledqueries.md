---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 763754b95a7f39c7f35e05df28589b69352168e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152421"
---
# \<activityScheduledQueries>
<span data-ttu-id="0e1ff-101">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="0e1ff-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="0e1ff-102">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="0e1ff-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="0e1ff-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="0e1ff-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="0e1ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e1ff-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e1ff-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0e1ff-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0e1ff-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0e1ff-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e1ff-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="0e1ff-107">Attributes</span></span>  
 <span data-ttu-id="0e1ff-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="0e1ff-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0e1ff-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0e1ff-109">Child Elements</span></span>  
  
|<span data-ttu-id="0e1ff-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="0e1ff-110">Element</span></span>|<span data-ttu-id="0e1ff-111">Description</span><span class="sxs-lookup"><span data-stu-id="0e1ff-111">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="0e1ff-112">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="0e1ff-112">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e1ff-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0e1ff-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0e1ff-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="0e1ff-114">Element</span></span>|<span data-ttu-id="0e1ff-115">Description</span><span class="sxs-lookup"><span data-stu-id="0e1ff-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="0e1ff-116">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="0e1ff-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e1ff-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e1ff-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0e1ff-118">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="0e1ff-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0e1ff-119">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="0e1ff-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
