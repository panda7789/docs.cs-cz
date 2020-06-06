---
title: <cancelRequestedQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850060"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="a18b4-102">\<cancelRequestedQuery>služby WCF</span><span class="sxs-lookup"><span data-stu-id="a18b4-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="a18b4-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="a18b4-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a18b4-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="a18b4-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="a18b4-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a18b4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  

## <a name="syntax"></a><span data-ttu-id="a18b4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a18b4-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a18b4-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a18b4-107">Attributes and elements</span></span>

<span data-ttu-id="a18b4-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a18b4-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a18b4-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="a18b4-109">Attributes</span></span>  
  
|<span data-ttu-id="a18b4-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="a18b4-110">Attribute</span></span>|<span data-ttu-id="a18b4-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a18b4-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="a18b4-112">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="a18b4-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="a18b4-113">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="a18b4-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a18b4-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="a18b4-114">Child elements</span></span>

<span data-ttu-id="a18b4-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="a18b4-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="a18b4-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="a18b4-116">Parent elements</span></span>
  
|<span data-ttu-id="a18b4-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="a18b4-117">Element</span></span>|<span data-ttu-id="a18b4-118">Description</span><span class="sxs-lookup"><span data-stu-id="a18b4-118">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQueries>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="a18b4-119">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="a18b4-119">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a18b4-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a18b4-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a18b4-121">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a18b4-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a18b4-122">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="a18b4-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
