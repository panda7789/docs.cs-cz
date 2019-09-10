---
title: <activityScheduledQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850493"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="68baf-102">\<activityScheduledQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="68baf-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="68baf-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="68baf-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="68baf-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="68baf-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="68baf-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="68baf-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="68baf-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="68baf-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="68baf-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="68baf-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="68baf-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="68baf-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="68baf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="68baf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="68baf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="68baf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="68baf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="68baf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="68baf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQueries >**</span><span class="sxs-lookup"><span data-stu-id="68baf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68baf-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68baf-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68baf-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="68baf-114">Attributes and elements</span></span>  

<span data-ttu-id="68baf-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="68baf-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68baf-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="68baf-116">Attributes</span></span>  

<span data-ttu-id="68baf-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="68baf-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="68baf-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="68baf-118">Child elements</span></span>  
  
|<span data-ttu-id="68baf-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="68baf-119">Element</span></span>|<span data-ttu-id="68baf-120">Popis</span><span class="sxs-lookup"><span data-stu-id="68baf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68baf-121">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="68baf-121">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="68baf-122">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="68baf-122">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68baf-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="68baf-123">Parent elements</span></span>  
  
|<span data-ttu-id="68baf-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="68baf-124">Element</span></span>|<span data-ttu-id="68baf-125">Popis</span><span class="sxs-lookup"><span data-stu-id="68baf-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68baf-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="68baf-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="68baf-127">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="68baf-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68baf-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68baf-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="68baf-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="68baf-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="68baf-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="68baf-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
