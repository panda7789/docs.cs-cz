---
title: <faultPropagationQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855261"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="6acbf-102">\<faultPropagationQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="6acbf-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="6acbf-103">Představuje kolekci dotazů, které se používají ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="6acbf-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="6acbf-104">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="6acbf-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="6acbf-105">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="6acbf-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="6acbf-106">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="6acbf-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="6acbf-107">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6acbf-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="6acbf-108">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6acbf-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6acbf-109">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6acbf-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6acbf-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="6acbf-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="6acbf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="6acbf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="6acbf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="6acbf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="6acbf-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="6acbf-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="6acbf-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQueries >**</span><span class="sxs-lookup"><span data-stu-id="6acbf-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6acbf-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6acbf-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6acbf-116">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6acbf-116">Attributes and elements</span></span>

<span data-ttu-id="6acbf-117">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6acbf-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="6acbf-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="6acbf-118">Attributes</span></span>

<span data-ttu-id="6acbf-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="6acbf-119">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="6acbf-120">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="6acbf-120">Child elements</span></span>

|<span data-ttu-id="6acbf-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="6acbf-121">Element</span></span>|<span data-ttu-id="6acbf-122">Popis</span><span class="sxs-lookup"><span data-stu-id="6acbf-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6acbf-123">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="6acbf-123">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="6acbf-124">Dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="6acbf-124">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="6acbf-125">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="6acbf-125">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6acbf-126">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="6acbf-126">Parent elements</span></span>  
  
|<span data-ttu-id="6acbf-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="6acbf-127">Element</span></span>|<span data-ttu-id="6acbf-128">Popis</span><span class="sxs-lookup"><span data-stu-id="6acbf-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6acbf-129">\<workflow></span><span class="sxs-lookup"><span data-stu-id="6acbf-129">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="6acbf-130">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6acbf-130">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6acbf-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6acbf-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6acbf-132">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6acbf-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6acbf-133">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="6acbf-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
