---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 58e3752be81609e32eee631e46d10c0a7d704248
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398960"
---
# \<activityStateQueries>
<span data-ttu-id="40044-101">Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="40044-101">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="40044-102">Například můžete chtít sledovat pokaždé, když se aktivita odeslat E-Mail dokončí v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="40044-102">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="40044-103">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="40044-103">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="40044-104">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="40044-104">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="40044-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="40044-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="40044-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40044-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40044-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="40044-107">Attributes and Elements</span></span>  
 <span data-ttu-id="40044-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="40044-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40044-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="40044-109">Attributes</span></span>  
 <span data-ttu-id="40044-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="40044-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40044-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="40044-111">Child Elements</span></span>  
  
|<span data-ttu-id="40044-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="40044-112">Element</span></span>|<span data-ttu-id="40044-113">Description</span><span class="sxs-lookup"><span data-stu-id="40044-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="40044-114">Dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="40044-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="40044-115">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="40044-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40044-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="40044-116">Parent Elements</span></span>  
  
|<span data-ttu-id="40044-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="40044-117">Element</span></span>|<span data-ttu-id="40044-118">Description</span><span class="sxs-lookup"><span data-stu-id="40044-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="40044-119">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="40044-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40044-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="40044-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="40044-121">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="40044-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="40044-122">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="40044-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
