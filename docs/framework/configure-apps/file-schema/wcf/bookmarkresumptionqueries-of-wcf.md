---
title: <bookmarkResumptionQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850136"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="6cf39-102">\<bookmarkResumptionQueries>služby WCF</span><span class="sxs-lookup"><span data-stu-id="6cf39-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="6cf39-103">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6cf39-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="6cf39-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="6cf39-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="6cf39-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6cf39-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="6cf39-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cf39-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cf39-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6cf39-107">Attributes and elements</span></span>  
  
<span data-ttu-id="6cf39-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6cf39-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cf39-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="6cf39-109">Attributes</span></span>  
  
<span data-ttu-id="6cf39-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="6cf39-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6cf39-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="6cf39-111">Child elements</span></span>  
  
|<span data-ttu-id="6cf39-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="6cf39-112">Element</span></span>|<span data-ttu-id="6cf39-113">Description</span><span class="sxs-lookup"><span data-stu-id="6cf39-113">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="6cf39-114">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6cf39-114">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="6cf39-115">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="6cf39-115">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6cf39-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="6cf39-116">Parent elements</span></span>  
  
|<span data-ttu-id="6cf39-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="6cf39-117">Element</span></span>|<span data-ttu-id="6cf39-118">Description</span><span class="sxs-lookup"><span data-stu-id="6cf39-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="6cf39-119">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6cf39-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6cf39-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cf39-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6cf39-121">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6cf39-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6cf39-122">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="6cf39-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
