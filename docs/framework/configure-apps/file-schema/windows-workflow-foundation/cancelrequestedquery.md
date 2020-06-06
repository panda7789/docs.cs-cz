---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e6840ce647625c36356cccd4651f17de32777e2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152284"
---
# \<cancelRequestedQuery>
<span data-ttu-id="87fd8-101">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="87fd8-101">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="87fd8-102">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="87fd8-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="87fd8-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="87fd8-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="87fd8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87fd8-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87fd8-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="87fd8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="87fd8-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="87fd8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87fd8-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="87fd8-107">Attributes</span></span>  
  
|<span data-ttu-id="87fd8-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="87fd8-108">Attribute</span></span>|<span data-ttu-id="87fd8-109">Popis</span><span class="sxs-lookup"><span data-stu-id="87fd8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87fd8-110">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="87fd8-110">activityName</span></span>|<span data-ttu-id="87fd8-111">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="87fd8-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="87fd8-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="87fd8-112">childActivityName</span></span>|<span data-ttu-id="87fd8-113">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="87fd8-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87fd8-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="87fd8-114">Child Elements</span></span>  
 <span data-ttu-id="87fd8-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="87fd8-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87fd8-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="87fd8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="87fd8-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="87fd8-117">Element</span></span>|<span data-ttu-id="87fd8-118">Description</span><span class="sxs-lookup"><span data-stu-id="87fd8-118">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="87fd8-119">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="87fd8-119">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="87fd8-120">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="87fd8-120">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87fd8-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="87fd8-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="87fd8-122">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="87fd8-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="87fd8-123">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="87fd8-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
