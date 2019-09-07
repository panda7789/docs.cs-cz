---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 0d08612ce5d74f4f7f505c538187ddecea610132
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398830"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="bae0d-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="bae0d-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="bae0d-102">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="bae0d-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="bae0d-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="bae0d-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="bae0d-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="bae0d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="bae0d-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bae0d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bae0d-106">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="bae0d-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="bae0d-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="bae0d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="bae0d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="bae0d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="bae0d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="bae0d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="bae0d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQueries >**</span><span class="sxs-lookup"><span data-stu-id="bae0d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bae0d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bae0d-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bae0d-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bae0d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bae0d-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bae0d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bae0d-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="bae0d-114">Attributes</span></span>  
 <span data-ttu-id="bae0d-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="bae0d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bae0d-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bae0d-116">Child Elements</span></span>  
  
|<span data-ttu-id="bae0d-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="bae0d-117">Element</span></span>|<span data-ttu-id="bae0d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="bae0d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bae0d-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="bae0d-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="bae0d-120">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="bae0d-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bae0d-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bae0d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bae0d-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="bae0d-122">Element</span></span>|<span data-ttu-id="bae0d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="bae0d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bae0d-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="bae0d-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="bae0d-125">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="bae0d-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bae0d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bae0d-126">See also</span></span>

- [<span data-ttu-id="bae0d-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bae0d-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bae0d-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="bae0d-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
