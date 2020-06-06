---
title: <activityScheduledQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850475"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="c14de-102">\<activityScheduledQuery>služby WCF</span><span class="sxs-lookup"><span data-stu-id="c14de-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="c14de-103">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="c14de-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="c14de-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="c14de-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="c14de-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="c14de-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="c14de-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c14de-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c14de-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c14de-107">Attributes and elements</span></span>  

<span data-ttu-id="c14de-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c14de-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c14de-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="c14de-109">Attributes</span></span>  
  
|<span data-ttu-id="c14de-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="c14de-110">Attribute</span></span>|<span data-ttu-id="c14de-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c14de-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="c14de-112">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="c14de-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="c14de-113">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="c14de-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c14de-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="c14de-114">Child elements</span></span>

<span data-ttu-id="c14de-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="c14de-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="c14de-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="c14de-116">Parent elements</span></span>  
  
|<span data-ttu-id="c14de-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="c14de-117">Element</span></span>|<span data-ttu-id="c14de-118">Description</span><span class="sxs-lookup"><span data-stu-id="c14de-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="c14de-119">Kolekce dotazů, které se používají ke sledování aktivity naplánované pro provádění nadřazenou aktivitou.</span><span class="sxs-lookup"><span data-stu-id="c14de-119">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c14de-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c14de-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="c14de-121">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c14de-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c14de-122">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="c14de-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
