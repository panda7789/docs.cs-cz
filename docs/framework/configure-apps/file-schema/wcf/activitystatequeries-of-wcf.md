---
title: <activityStateQueries>služby WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 249ac3d91f6251a943dd856e4122b8b54f691702
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850572"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="e43eb-102">\<activityStateQueries>služby WCF</span><span class="sxs-lookup"><span data-stu-id="e43eb-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="e43eb-103">Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e43eb-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="e43eb-104">Například můžete chtít sledovat pokaždé, když se aktivita odeslat E-Mail dokončí v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e43eb-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="e43eb-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="e43eb-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="e43eb-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="e43eb-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="e43eb-107">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e43eb-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="e43eb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e43eb-108">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="e43eb-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e43eb-109">Attributes and elements</span></span>

<span data-ttu-id="e43eb-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e43eb-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="e43eb-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e43eb-111">Attributes</span></span>  

<span data-ttu-id="e43eb-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="e43eb-112">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="e43eb-113">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="e43eb-113">Child elements</span></span>

|<span data-ttu-id="e43eb-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="e43eb-114">Element</span></span>|<span data-ttu-id="e43eb-115">Description</span><span class="sxs-lookup"><span data-stu-id="e43eb-115">Description</span></span>|
|-------------|-----------------|
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|<span data-ttu-id="e43eb-116">Dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="e43eb-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e43eb-117">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="e43eb-117">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e43eb-118">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="e43eb-118">Parent elements</span></span>

|<span data-ttu-id="e43eb-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="e43eb-119">Element</span></span>|<span data-ttu-id="e43eb-120">Description</span><span class="sxs-lookup"><span data-stu-id="e43eb-120">Description</span></span>|
|-------------|-----------------|
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="e43eb-121">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e43eb-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e43eb-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e43eb-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="e43eb-123">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e43eb-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e43eb-124">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="e43eb-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
