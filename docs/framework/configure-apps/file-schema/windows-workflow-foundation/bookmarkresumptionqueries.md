---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 563e0cbd3f50887e1c9e3d47a3c9502acc13b2c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398857"
---
# \<bookmarkResumptionQueries>
<span data-ttu-id="2e540-101">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2e540-101">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="2e540-102">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="2e540-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="2e540-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="2e540-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="2e540-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e540-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e540-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2e540-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2e540-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2e540-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e540-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="2e540-107">Attributes</span></span>  
 <span data-ttu-id="2e540-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="2e540-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2e540-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2e540-109">Child Elements</span></span>  
  
|<span data-ttu-id="2e540-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="2e540-110">Element</span></span>|<span data-ttu-id="2e540-111">Description</span><span class="sxs-lookup"><span data-stu-id="2e540-111">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery.md)|<span data-ttu-id="2e540-112">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2e540-112">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="2e540-113">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="2e540-113">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2e540-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2e540-114">Parent Elements</span></span>  
  
|<span data-ttu-id="2e540-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="2e540-115">Element</span></span>|<span data-ttu-id="2e540-116">Description</span><span class="sxs-lookup"><span data-stu-id="2e540-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="2e540-117">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="2e540-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e540-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e540-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2e540-119">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="2e540-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2e540-120">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="2e540-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
