---
title: <faultPropagationQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855261"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="d3ba3-102">\<faultPropagationQueries>služby WCF</span><span class="sxs-lookup"><span data-stu-id="d3ba3-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="d3ba3-103">Představuje kolekci dotazů, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="d3ba3-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="d3ba3-104">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="d3ba3-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="d3ba3-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="d3ba3-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="d3ba3-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="d3ba3-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="d3ba3-107">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d3ba3-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="d3ba3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3ba3-108">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3ba3-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d3ba3-109">Attributes and elements</span></span>

<span data-ttu-id="d3ba3-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d3ba3-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="d3ba3-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="d3ba3-111">Attributes</span></span>

<span data-ttu-id="d3ba3-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="d3ba3-112">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="d3ba3-113">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="d3ba3-113">Child elements</span></span>

|<span data-ttu-id="d3ba3-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3ba3-114">Element</span></span>|<span data-ttu-id="d3ba3-115">Description</span><span class="sxs-lookup"><span data-stu-id="d3ba3-115">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="d3ba3-116">Dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="d3ba3-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="d3ba3-117">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="d3ba3-117">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3ba3-118">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="d3ba3-118">Parent elements</span></span>  
  
|<span data-ttu-id="d3ba3-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3ba3-119">Element</span></span>|<span data-ttu-id="d3ba3-120">Description</span><span class="sxs-lookup"><span data-stu-id="d3ba3-120">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="d3ba3-121">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d3ba3-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3ba3-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3ba3-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d3ba3-123">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d3ba3-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d3ba3-124">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="d3ba3-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
