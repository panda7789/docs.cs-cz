---
title: <activityScheduledQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850493"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="de355-102">\<activityScheduledQueries>služby WCF</span><span class="sxs-lookup"><span data-stu-id="de355-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="de355-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="de355-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="de355-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="de355-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="de355-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="de355-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="de355-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de355-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de355-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="de355-107">Attributes and elements</span></span>  

<span data-ttu-id="de355-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="de355-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de355-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="de355-109">Attributes</span></span>  

<span data-ttu-id="de355-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="de355-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de355-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="de355-111">Child elements</span></span>  
  
|<span data-ttu-id="de355-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="de355-112">Element</span></span>|<span data-ttu-id="de355-113">Description</span><span class="sxs-lookup"><span data-stu-id="de355-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="de355-114">Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="de355-114">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de355-115">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="de355-115">Parent elements</span></span>  
  
|<span data-ttu-id="de355-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="de355-116">Element</span></span>|<span data-ttu-id="de355-117">Description</span><span class="sxs-lookup"><span data-stu-id="de355-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="de355-118">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="de355-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de355-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="de355-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="de355-120">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="de355-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="de355-121">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="de355-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
