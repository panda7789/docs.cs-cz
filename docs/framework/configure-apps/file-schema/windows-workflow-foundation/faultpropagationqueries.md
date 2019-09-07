---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: bc0cc5fd027da45994269b149b72496fa03becef
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398736"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="cd644-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="cd644-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="cd644-102">Představuje kolekci dotazů, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="cd644-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="cd644-103">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="cd644-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="cd644-104">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="cd644-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="cd644-105">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="cd644-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="cd644-106">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="cd644-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="cd644-107">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cd644-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cd644-108">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cd644-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="cd644-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="cd644-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="cd644-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="cd644-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="cd644-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cd644-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="cd644-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQueries >**</span><span class="sxs-lookup"><span data-stu-id="cd644-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="cd644-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd644-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd644-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cd644-114">Attributes and Elements</span></span>  
 <span data-ttu-id="cd644-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cd644-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd644-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="cd644-116">Attributes</span></span>  
 <span data-ttu-id="cd644-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="cd644-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cd644-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cd644-118">Child Elements</span></span>  
  
|<span data-ttu-id="cd644-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="cd644-119">Element</span></span>|<span data-ttu-id="cd644-120">Popis</span><span class="sxs-lookup"><span data-stu-id="cd644-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd644-121">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="cd644-121">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="cd644-122">Dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="cd644-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="cd644-123">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="cd644-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd644-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cd644-124">Parent Elements</span></span>  
  
|<span data-ttu-id="cd644-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="cd644-125">Element</span></span>|<span data-ttu-id="cd644-126">Popis</span><span class="sxs-lookup"><span data-stu-id="cd644-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd644-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="cd644-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="cd644-128">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="cd644-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd644-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd644-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cd644-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="cd644-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cd644-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="cd644-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
