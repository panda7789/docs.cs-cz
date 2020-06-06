---
title: <bookmarkResumptionQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71834008"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="da318-102">\<bookmarkResumptionQuery>služby WCF</span><span class="sxs-lookup"><span data-stu-id="da318-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="da318-103">Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="da318-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="da318-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="da318-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="da318-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="da318-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="da318-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da318-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da318-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="da318-107">Attributes and elements</span></span>

<span data-ttu-id="da318-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="da318-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da318-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="da318-109">Attributes</span></span>  
  
|<span data-ttu-id="da318-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="da318-110">Attribute</span></span>|<span data-ttu-id="da318-111">Popis</span><span class="sxs-lookup"><span data-stu-id="da318-111">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="da318-112">Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="da318-112">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da318-113">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="da318-113">Child elements</span></span>

<span data-ttu-id="da318-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="da318-114">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="da318-115">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="da318-115">Parent elements</span></span>  
  
|<span data-ttu-id="da318-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="da318-116">Element</span></span>|<span data-ttu-id="da318-117">Description</span><span class="sxs-lookup"><span data-stu-id="da318-117">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="da318-118">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="da318-118">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da318-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="da318-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="da318-120">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="da318-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="da318-121">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="da318-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
