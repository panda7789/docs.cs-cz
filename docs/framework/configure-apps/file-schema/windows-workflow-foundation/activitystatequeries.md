---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 58e3752be81609e32eee631e46d10c0a7d704248
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398960"
---
# <a name="activitystatequeries"></a><span data-ttu-id="57b37-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="57b37-101">\<activityStateQueries></span></span>
<span data-ttu-id="57b37-102">Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="57b37-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="57b37-103">Například můžete chtít sledovat pokaždé, když se aktivita odeslat E-Mail dokončí v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="57b37-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="57b37-104">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="57b37-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="57b37-105">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="57b37-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="57b37-106">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="57b37-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="57b37-107">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="57b37-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="57b37-108">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="57b37-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="57b37-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="57b37-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="57b37-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="57b37-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="57b37-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="57b37-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="57b37-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQueries >**</span><span class="sxs-lookup"><span data-stu-id="57b37-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57b37-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57b37-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57b37-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="57b37-114">Attributes and Elements</span></span>  
 <span data-ttu-id="57b37-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="57b37-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57b37-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="57b37-116">Attributes</span></span>  
 <span data-ttu-id="57b37-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="57b37-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57b37-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="57b37-118">Child Elements</span></span>  
  
|<span data-ttu-id="57b37-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="57b37-119">Element</span></span>|<span data-ttu-id="57b37-120">Popis</span><span class="sxs-lookup"><span data-stu-id="57b37-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57b37-121">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="57b37-121">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="57b37-122">Dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="57b37-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="57b37-123">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="57b37-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57b37-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="57b37-124">Parent Elements</span></span>  
  
|<span data-ttu-id="57b37-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="57b37-125">Element</span></span>|<span data-ttu-id="57b37-126">Popis</span><span class="sxs-lookup"><span data-stu-id="57b37-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57b37-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="57b37-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="57b37-128">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="57b37-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57b37-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57b37-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="57b37-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="57b37-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="57b37-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="57b37-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
