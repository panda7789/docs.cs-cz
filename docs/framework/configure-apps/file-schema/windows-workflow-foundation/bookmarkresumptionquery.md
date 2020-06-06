---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: b2a81a42a17474bdb0124bec6d3c3eeefa514411
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398851"
---
# \<bookmarkResumptionQuery>
<span data-ttu-id="8b19c-101">Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8b19c-101">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="8b19c-102">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="8b19c-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="8b19c-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="8b19c-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="8b19c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b19c-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b19c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8b19c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8b19c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8b19c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b19c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="8b19c-107">Attributes</span></span>  
  
|<span data-ttu-id="8b19c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="8b19c-108">Attribute</span></span>|<span data-ttu-id="8b19c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8b19c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b19c-110">name</span><span class="sxs-lookup"><span data-stu-id="8b19c-110">name</span></span>|<span data-ttu-id="8b19c-111">Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="8b19c-111">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b19c-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8b19c-112">Child Elements</span></span>  
 <span data-ttu-id="8b19c-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="8b19c-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b19c-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8b19c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8b19c-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="8b19c-115">Element</span></span>|<span data-ttu-id="8b19c-116">Description</span><span class="sxs-lookup"><span data-stu-id="8b19c-116">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="8b19c-117">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8b19c-117">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b19c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b19c-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8b19c-119">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="8b19c-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8b19c-120">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="8b19c-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
