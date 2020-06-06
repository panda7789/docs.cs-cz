---
title: <customTrackingQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 2c4bd74ae346c536e8bc0ae454e638b7c76a40fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855430"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="65bd6-102">\<customTrackingQueries>služby WCF</span><span class="sxs-lookup"><span data-stu-id="65bd6-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="65bd6-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="65bd6-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="65bd6-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="65bd6-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="65bd6-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="65bd6-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  

## <a name="syntax"></a><span data-ttu-id="65bd6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65bd6-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65bd6-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="65bd6-107">Attributes and elements</span></span>

<span data-ttu-id="65bd6-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="65bd6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65bd6-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="65bd6-109">Attributes</span></span>

<span data-ttu-id="65bd6-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="65bd6-110">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="65bd6-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="65bd6-111">Child elements</span></span>
  
|<span data-ttu-id="65bd6-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="65bd6-112">Element</span></span>|<span data-ttu-id="65bd6-113">Description</span><span class="sxs-lookup"><span data-stu-id="65bd6-113">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery-of-wcf.md)|<span data-ttu-id="65bd6-114">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="65bd6-114">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65bd6-115">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="65bd6-115">Parent elements</span></span>  
  
|<span data-ttu-id="65bd6-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="65bd6-116">Element</span></span>|<span data-ttu-id="65bd6-117">Description</span><span class="sxs-lookup"><span data-stu-id="65bd6-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="65bd6-118">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="65bd6-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65bd6-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="65bd6-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="65bd6-120">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="65bd6-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="65bd6-121">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="65bd6-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
