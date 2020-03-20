---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151842"
---
# <a name="workflowidle"></a><span data-ttu-id="f0aa9-101">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="f0aa9-101">\<workflowIdle></span></span>
<span data-ttu-id="f0aa9-102">Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="f0aa9-103">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f0aa9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f0aa9-104">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f0aa9-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="f0aa9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f0aa9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f0aa9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f0aa9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f0aa9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f0aa9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f0aa9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**</span><span class="sxs-lookup"><span data-stu-id="f0aa9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0aa9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0aa9-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan"
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0aa9-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f0aa9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f0aa9-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0aa9-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f0aa9-112">Attributes</span></span>  
  
|<span data-ttu-id="f0aa9-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f0aa9-113">Attribute</span></span>|<span data-ttu-id="f0aa9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f0aa9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0aa9-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="f0aa9-115">timeToPersist</span></span>|<span data-ttu-id="f0aa9-116">Hodnota Timespan, která určuje dobu mezi dobou, kdy se pracovní postup stane neaktivním a je trvalý.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="f0aa9-117">Výchozí hodnota je TimeSpan.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="f0aa9-118">Doba trvání začíná uplynout při instance pracovního postupu se změní na nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="f0aa9-119">Tento atribut je užitečný, pokud chcete zachovat instanci pracovního postupu agresivněji při zachování instance v paměti tak dlouho, jak je to možné.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="f0aa9-120">Tento atribut je platný pouze v případě, že jeho hodnota je menší než atribut **timeToUnload.**</span><span class="sxs-lookup"><span data-stu-id="f0aa9-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="f0aa9-121">Pokud je větší, je ignorována.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="f0aa9-122">Pokud tento atribut uplyne před hodnotou určenou atributem **timeToUnload,** musí být trvalost dokončena před uvolněním pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="f0aa9-123">To znamená, že může být operace uvolnění zpožděna, dokud je trvalá pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="f0aa9-124">Stálost vrstvu je zodpovědná za zpracování jakékoli pokusy o vytvoření přechodné chyb a pouze vyvolá výjimky na jiný obnovitelné chyby.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="f0aa9-125">Proto všechny výjimky, dojde při stálost jsou zpracovány jako závažné a instance pracovního postupu byl přerušen.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="f0aa9-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="f0aa9-126">timeToUnload</span></span>|<span data-ttu-id="f0aa9-127">Časový interval hodnotu, která určuje dobu trvání v době mezi pracovního postupu se změní na nečinnosti a bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="f0aa9-128">Výchozí hodnota je 1 minuta.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="f0aa9-129">Uvolňování pracovního postupu znamená, že je také zachována.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="f0aa9-130">Pokud je tento atribut nastaven na nulu, instance pracovního postupu je trvalá a uvolněná ihned po nečinnosti pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="f0aa9-131">Nastavení tohoto atributu timespan.maxvalue účinně zakáže operaci uvolnění.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="f0aa9-132">Instance nečinných pracovních postupů jsou nikdy uvolněna.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0aa9-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f0aa9-133">Child Elements</span></span>  
 <span data-ttu-id="f0aa9-134">Žádné.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0aa9-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f0aa9-135">Parent Elements</span></span>  
  
|<span data-ttu-id="f0aa9-136">Element</span><span class="sxs-lookup"><span data-stu-id="f0aa9-136">Element</span></span>|<span data-ttu-id="f0aa9-137">Popis</span><span class="sxs-lookup"><span data-stu-id="f0aa9-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0aa9-138">\<chování> \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f0aa9-138">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f0aa9-139">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="f0aa9-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0aa9-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0aa9-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
