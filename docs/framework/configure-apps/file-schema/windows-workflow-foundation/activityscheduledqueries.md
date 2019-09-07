---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: a43242e2f22c48a57c11f6f03657d7d3de27ff48
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398978"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="08698-101">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="08698-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="08698-102">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="08698-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="08698-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="08698-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="08698-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="08698-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="08698-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="08698-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="08698-106">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="08698-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="08698-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="08698-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="08698-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="08698-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="08698-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="08698-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="08698-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQueries >**</span><span class="sxs-lookup"><span data-stu-id="08698-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08698-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08698-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08698-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="08698-112">Attributes and Elements</span></span>  
 <span data-ttu-id="08698-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="08698-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08698-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="08698-114">Attributes</span></span>  
 <span data-ttu-id="08698-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="08698-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="08698-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="08698-116">Child Elements</span></span>  
  
|<span data-ttu-id="08698-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="08698-117">Element</span></span>|<span data-ttu-id="08698-118">Popis</span><span class="sxs-lookup"><span data-stu-id="08698-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08698-119">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="08698-119">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="08698-120">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="08698-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08698-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="08698-121">Parent Elements</span></span>  
  
|<span data-ttu-id="08698-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="08698-122">Element</span></span>|<span data-ttu-id="08698-123">Popis</span><span class="sxs-lookup"><span data-stu-id="08698-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08698-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="08698-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="08698-125">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="08698-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08698-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08698-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="08698-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="08698-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="08698-128">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="08698-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
