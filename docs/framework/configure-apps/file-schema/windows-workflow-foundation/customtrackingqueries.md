---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 6901244009956a499458858bf73f8fd83ec52e13
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152258"
---
# \<customTrackingQueries>
<span data-ttu-id="2ee4f-101">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="2ee4f-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="2ee4f-102">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="2ee4f-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="2ee4f-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="2ee4f-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="2ee4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ee4f-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String"
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ee4f-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2ee4f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2ee4f-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2ee4f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ee4f-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="2ee4f-107">Attributes</span></span>  
 <span data-ttu-id="2ee4f-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="2ee4f-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2ee4f-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2ee4f-109">Child Elements</span></span>  
  
|<span data-ttu-id="2ee4f-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="2ee4f-110">Element</span></span>|<span data-ttu-id="2ee4f-111">Description</span><span class="sxs-lookup"><span data-stu-id="2ee4f-111">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="2ee4f-112">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="2ee4f-112">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2ee4f-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2ee4f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="2ee4f-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="2ee4f-114">Element</span></span>|<span data-ttu-id="2ee4f-115">Description</span><span class="sxs-lookup"><span data-stu-id="2ee4f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="2ee4f-116">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="2ee4f-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ee4f-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ee4f-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2ee4f-118">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="2ee4f-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2ee4f-119">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="2ee4f-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
