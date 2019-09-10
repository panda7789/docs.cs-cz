---
title: <customTrackingQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 2c4bd74ae346c536e8bc0ae454e638b7c76a40fc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855430"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="0aac2-102">\<customTrackingQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="0aac2-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="0aac2-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="0aac2-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="0aac2-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="0aac2-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="0aac2-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0aac2-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="0aac2-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0aac2-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0aac2-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0aac2-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0aac2-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0aac2-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="0aac2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="0aac2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="0aac2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0aac2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="0aac2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0aac2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="0aac2-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQueries >**</span><span class="sxs-lookup"><span data-stu-id="0aac2-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="0aac2-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0aac2-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0aac2-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0aac2-114">Attributes and elements</span></span>

<span data-ttu-id="0aac2-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0aac2-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0aac2-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="0aac2-116">Attributes</span></span>

<span data-ttu-id="0aac2-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="0aac2-117">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="0aac2-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="0aac2-118">Child elements</span></span>
  
|<span data-ttu-id="0aac2-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="0aac2-119">Element</span></span>|<span data-ttu-id="0aac2-120">Popis</span><span class="sxs-lookup"><span data-stu-id="0aac2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0aac2-121">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="0aac2-121">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="0aac2-122">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="0aac2-122">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0aac2-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="0aac2-123">Parent elements</span></span>  
  
|<span data-ttu-id="0aac2-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="0aac2-124">Element</span></span>|<span data-ttu-id="0aac2-125">Popis</span><span class="sxs-lookup"><span data-stu-id="0aac2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0aac2-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="0aac2-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="0aac2-127">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0aac2-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0aac2-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0aac2-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0aac2-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="0aac2-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0aac2-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="0aac2-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
