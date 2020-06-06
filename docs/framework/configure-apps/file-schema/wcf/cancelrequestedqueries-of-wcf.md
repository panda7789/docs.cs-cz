---
title: <cancelRequestedQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 63cfc835ac7ce88bde56fd9243a2cf6652cbce6e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850093"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="11047-102">\<cancelRequestedQueries>služby WCF</span><span class="sxs-lookup"><span data-stu-id="11047-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="11047-103">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="11047-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="11047-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="11047-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="11047-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="11047-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="11047-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11047-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11047-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11047-107">Attributes and elements</span></span>  

<span data-ttu-id="11047-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11047-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11047-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="11047-109">Attributes</span></span>

<span data-ttu-id="11047-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="11047-110">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="11047-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="11047-111">Child elements</span></span>
  
|<span data-ttu-id="11047-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="11047-112">Element</span></span>|<span data-ttu-id="11047-113">Description</span><span class="sxs-lookup"><span data-stu-id="11047-113">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="11047-114">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="11047-114">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11047-115">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="11047-115">Parent elements</span></span>  
  
|<span data-ttu-id="11047-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="11047-116">Element</span></span>|<span data-ttu-id="11047-117">Description</span><span class="sxs-lookup"><span data-stu-id="11047-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="11047-118">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="11047-118">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11047-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="11047-119">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="11047-120">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="11047-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="11047-121">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="11047-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
