---
title: <activityScheduledQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850475"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="93aba-102">\<activityScheduledQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="93aba-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="93aba-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="93aba-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="93aba-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="93aba-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="93aba-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="93aba-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="93aba-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="93aba-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="93aba-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="93aba-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="93aba-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="93aba-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="93aba-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="93aba-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="93aba-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="93aba-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="93aba-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="93aba-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="93aba-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityScheduledQueries >** ](activityscheduledqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="93aba-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)</span></span>\
<span data-ttu-id="93aba-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQuery >**</span><span class="sxs-lookup"><span data-stu-id="93aba-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93aba-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93aba-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93aba-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="93aba-115">Attributes and elements</span></span>  

<span data-ttu-id="93aba-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="93aba-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93aba-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="93aba-117">Attributes</span></span>  
  
|<span data-ttu-id="93aba-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="93aba-118">Attribute</span></span>|<span data-ttu-id="93aba-119">Popis</span><span class="sxs-lookup"><span data-stu-id="93aba-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="93aba-120">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="93aba-120">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="93aba-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="93aba-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93aba-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="93aba-122">Child elements</span></span>

<span data-ttu-id="93aba-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="93aba-123">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="93aba-124">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="93aba-124">Parent elements</span></span>  
  
|<span data-ttu-id="93aba-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="93aba-125">Element</span></span>|<span data-ttu-id="93aba-126">Popis</span><span class="sxs-lookup"><span data-stu-id="93aba-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93aba-127">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="93aba-127">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="93aba-128">Kolekce dotazů, které se používají ke sledování aktivity naplánované pro provádění nadřazenou aktivitou.</span><span class="sxs-lookup"><span data-stu-id="93aba-128">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93aba-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93aba-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="93aba-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="93aba-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="93aba-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="93aba-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
