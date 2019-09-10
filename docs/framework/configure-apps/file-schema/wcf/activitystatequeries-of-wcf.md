---
title: <activityStateQueries>služby WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 249ac3d91f6251a943dd856e4122b8b54f691702
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850572"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="603d5-102">\<activityStateQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="603d5-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="603d5-103">Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="603d5-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="603d5-104">Například můžete chtít sledovat pokaždé, když se aktivita odeslat E-Mail dokončí v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="603d5-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="603d5-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="603d5-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="603d5-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="603d5-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="603d5-107">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="603d5-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="603d5-108">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="603d5-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="603d5-109">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="603d5-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="603d5-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="603d5-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="603d5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="603d5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="603d5-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="603d5-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="603d5-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="603d5-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="603d5-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQueries >**</span><span class="sxs-lookup"><span data-stu-id="603d5-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="603d5-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="603d5-115">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="603d5-116">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="603d5-116">Attributes and elements</span></span>

<span data-ttu-id="603d5-117">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="603d5-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="603d5-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="603d5-118">Attributes</span></span>  

<span data-ttu-id="603d5-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="603d5-119">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="603d5-120">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="603d5-120">Child elements</span></span>

|<span data-ttu-id="603d5-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="603d5-121">Element</span></span>|<span data-ttu-id="603d5-122">Popis</span><span class="sxs-lookup"><span data-stu-id="603d5-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="603d5-123">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="603d5-123">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="603d5-124">Dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="603d5-124">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="603d5-125">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="603d5-125">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="603d5-126">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="603d5-126">Parent elements</span></span>

|<span data-ttu-id="603d5-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="603d5-127">Element</span></span>|<span data-ttu-id="603d5-128">Popis</span><span class="sxs-lookup"><span data-stu-id="603d5-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="603d5-129">\<workflow></span><span class="sxs-lookup"><span data-stu-id="603d5-129">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="603d5-130">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="603d5-130">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="603d5-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="603d5-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="603d5-132">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="603d5-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="603d5-133">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="603d5-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
