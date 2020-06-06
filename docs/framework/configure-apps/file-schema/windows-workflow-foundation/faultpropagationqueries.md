---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 3d6d03638ec5806448a16cc32b37e630d6198624
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152128"
---
# \<faultPropagationQueries>
<span data-ttu-id="a42e9-101">Představuje kolekci dotazů, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="a42e9-101">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a42e9-102">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="a42e9-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="a42e9-103">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="a42e9-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="a42e9-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="a42e9-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="a42e9-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a42e9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**
  
## <a name="syntax"></a><span data-ttu-id="a42e9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a42e9-106">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a42e9-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a42e9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a42e9-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a42e9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a42e9-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="a42e9-109">Attributes</span></span>  
 <span data-ttu-id="a42e9-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="a42e9-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a42e9-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a42e9-111">Child Elements</span></span>  
  
|<span data-ttu-id="a42e9-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="a42e9-112">Element</span></span>|<span data-ttu-id="a42e9-113">Description</span><span class="sxs-lookup"><span data-stu-id="a42e9-113">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="a42e9-114">Dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="a42e9-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a42e9-115">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="a42e9-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a42e9-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a42e9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a42e9-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="a42e9-117">Element</span></span>|<span data-ttu-id="a42e9-118">Description</span><span class="sxs-lookup"><span data-stu-id="a42e9-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="a42e9-119">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="a42e9-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a42e9-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a42e9-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a42e9-121">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a42e9-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a42e9-122">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="a42e9-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
