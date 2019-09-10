---
title: <bookmarkResumptionQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850136"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="269ef-102">\<bookmarkResumptionQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="269ef-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="269ef-103">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="269ef-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="269ef-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="269ef-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="269ef-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="269ef-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="269ef-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="269ef-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="269ef-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="269ef-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="269ef-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="269ef-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="269ef-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="269ef-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="269ef-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="269ef-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="269ef-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="269ef-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="269ef-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQueries >**</span><span class="sxs-lookup"><span data-stu-id="269ef-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="269ef-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="269ef-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="269ef-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="269ef-114">Attributes and elements</span></span>  
  
<span data-ttu-id="269ef-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="269ef-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="269ef-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="269ef-116">Attributes</span></span>  
  
<span data-ttu-id="269ef-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="269ef-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="269ef-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="269ef-118">Child elements</span></span>  
  
|<span data-ttu-id="269ef-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="269ef-119">Element</span></span>|<span data-ttu-id="269ef-120">Popis</span><span class="sxs-lookup"><span data-stu-id="269ef-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="269ef-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="269ef-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="269ef-122">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="269ef-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="269ef-123">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="269ef-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="269ef-124">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="269ef-124">Parent elements</span></span>  
  
|<span data-ttu-id="269ef-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="269ef-125">Element</span></span>|<span data-ttu-id="269ef-126">Popis</span><span class="sxs-lookup"><span data-stu-id="269ef-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="269ef-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="269ef-127">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="269ef-128">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="269ef-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="269ef-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="269ef-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="269ef-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="269ef-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="269ef-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="269ef-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
