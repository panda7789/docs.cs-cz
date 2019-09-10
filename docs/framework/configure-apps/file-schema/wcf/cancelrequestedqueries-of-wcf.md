---
title: <cancelRequestedQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 63cfc835ac7ce88bde56fd9243a2cf6652cbce6e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850093"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="31edd-102">\<cancelRequestedQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="31edd-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="31edd-103">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="31edd-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="31edd-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="31edd-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="31edd-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="31edd-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="31edd-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="31edd-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="31edd-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="31edd-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="31edd-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="31edd-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="31edd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="31edd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="31edd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="31edd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="31edd-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="31edd-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="31edd-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQueries >**</span><span class="sxs-lookup"><span data-stu-id="31edd-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31edd-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31edd-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31edd-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="31edd-114">Attributes and elements</span></span>  

<span data-ttu-id="31edd-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="31edd-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31edd-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="31edd-116">Attributes</span></span>

<span data-ttu-id="31edd-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="31edd-117">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="31edd-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="31edd-118">Child elements</span></span>
  
|<span data-ttu-id="31edd-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="31edd-119">Element</span></span>|<span data-ttu-id="31edd-120">Popis</span><span class="sxs-lookup"><span data-stu-id="31edd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31edd-121">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="31edd-121">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="31edd-122">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="31edd-122">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31edd-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="31edd-123">Parent elements</span></span>  
  
|<span data-ttu-id="31edd-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="31edd-124">Element</span></span>|<span data-ttu-id="31edd-125">Popis</span><span class="sxs-lookup"><span data-stu-id="31edd-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31edd-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="31edd-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="31edd-127">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="31edd-127">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31edd-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31edd-128">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="31edd-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="31edd-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="31edd-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="31edd-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
