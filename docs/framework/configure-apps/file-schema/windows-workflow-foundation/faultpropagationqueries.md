---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 3d6d03638ec5806448a16cc32b37e630d6198624
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152128"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="1e505-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="1e505-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="1e505-102">Představuje kolekci dotazů, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="1e505-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="1e505-103">K této události dochází pokaždé, když FaultHandler zpracuje chybu.</span><span class="sxs-lookup"><span data-stu-id="1e505-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="1e505-104">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="1e505-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="1e505-105">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="1e505-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="1e505-106">Další informace o sledování profilových dotazů naleznete v [tématu Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1e505-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="1e505-107">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e505-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1e505-108">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="1e505-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="1e505-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sledování>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="1e505-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="1e505-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfil>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="1e505-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="1e505-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="1e505-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="1e505-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chybyPropagationQueries>**</span><span class="sxs-lookup"><span data-stu-id="1e505-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="1e505-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e505-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e505-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1e505-114">Attributes and Elements</span></span>  
 <span data-ttu-id="1e505-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1e505-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e505-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="1e505-116">Attributes</span></span>  
 <span data-ttu-id="1e505-117">Žádné.</span><span class="sxs-lookup"><span data-stu-id="1e505-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e505-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1e505-118">Child Elements</span></span>  
  
|<span data-ttu-id="1e505-119">Element</span><span class="sxs-lookup"><span data-stu-id="1e505-119">Element</span></span>|<span data-ttu-id="1e505-120">Popis</span><span class="sxs-lookup"><span data-stu-id="1e505-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e505-121">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="1e505-121">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="1e505-122">Dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="1e505-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="1e505-123">K této události dochází pokaždé, když FaultHandler zpracuje chybu.</span><span class="sxs-lookup"><span data-stu-id="1e505-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e505-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1e505-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1e505-125">Element</span><span class="sxs-lookup"><span data-stu-id="1e505-125">Element</span></span>|<span data-ttu-id="1e505-126">Popis</span><span class="sxs-lookup"><span data-stu-id="1e505-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e505-127">\<>pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1e505-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="1e505-128">Konfigurační prvek, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **activityDefinitionId.**</span><span class="sxs-lookup"><span data-stu-id="1e505-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e505-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e505-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1e505-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1e505-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1e505-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="1e505-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
