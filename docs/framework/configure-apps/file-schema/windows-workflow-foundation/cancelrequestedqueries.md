---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 89297b3a7d64f4300a735d8512230d441836c634
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152304"
---
# \<cancelRequestedQueries>
<span data-ttu-id="c703a-101">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="c703a-101">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c703a-102">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="c703a-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="c703a-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="c703a-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="c703a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c703a-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c703a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c703a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c703a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c703a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c703a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="c703a-107">Attributes</span></span>  
 <span data-ttu-id="c703a-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="c703a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c703a-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c703a-109">Child Elements</span></span>  
  
|<span data-ttu-id="c703a-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="c703a-110">Element</span></span>|<span data-ttu-id="c703a-111">Description</span><span class="sxs-lookup"><span data-stu-id="c703a-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery.md)|<span data-ttu-id="c703a-112">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="c703a-112">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c703a-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c703a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c703a-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="c703a-114">Element</span></span>|<span data-ttu-id="c703a-115">Description</span><span class="sxs-lookup"><span data-stu-id="c703a-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="c703a-116">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="c703a-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c703a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c703a-117">See also</span></span>

- [<span data-ttu-id="c703a-118">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c703a-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c703a-119">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="c703a-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
