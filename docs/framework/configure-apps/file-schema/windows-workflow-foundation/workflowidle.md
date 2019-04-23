---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1dc186f5899935dab43c0d33894e659c4b19748c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201114"
---
# <a name="workflowidle"></a><span data-ttu-id="8d998-101">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="8d998-101">\<workflowIdle></span></span>
<span data-ttu-id="8d998-102">Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.</span><span class="sxs-lookup"><span data-stu-id="8d998-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="8d998-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8d998-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8d998-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="8d998-104">\<behaviors></span></span>  
<span data-ttu-id="8d998-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8d998-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="8d998-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="8d998-106">\<behavior></span></span>  
<span data-ttu-id="8d998-107">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="8d998-107">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d998-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d998-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d998-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8d998-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8d998-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8d998-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d998-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="8d998-111">Attributes</span></span>  
  
|<span data-ttu-id="8d998-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="8d998-112">Attribute</span></span>|<span data-ttu-id="8d998-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8d998-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d998-114">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="8d998-114">timeToPersist</span></span>|<span data-ttu-id="8d998-115">Časový interval hodnotu, která určuje dobu trvání mezi čas změní na nečinnosti a je trvalá pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8d998-115">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="8d998-116">Výchozí hodnota je hodnotu TimeSpan.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="8d998-116">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="8d998-117">Doba trvání začíná uplynout při instance pracovního postupu se změní na nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="8d998-117">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="8d998-118">Tento atribut je užitečné, pokud chcete zachovat instance pracovního postupu agresivnější stále zachováním instance v paměti pro co nejdéle.</span><span class="sxs-lookup"><span data-stu-id="8d998-118">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="8d998-119">Tento atribut je platná pouze pokud její hodnota je menší než **timeToUnload** atribut.</span><span class="sxs-lookup"><span data-stu-id="8d998-119">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="8d998-120">Pokud je větší, je ignorována.</span><span class="sxs-lookup"><span data-stu-id="8d998-120">If it is greater, it is ignored.</span></span> <span data-ttu-id="8d998-121">Pokud tento atribut uplyne hodnotu zadanou proměnnou **timeToUnload** atributu, stálost, musíte dokončit pracovní postup bude odpojen.</span><span class="sxs-lookup"><span data-stu-id="8d998-121">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="8d998-122">To znamená, že může být operace uvolnění zpožděna, dokud je trvalá pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8d998-122">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="8d998-123">Stálost vrstvu je zodpovědná za zpracování jakékoli pokusy o vytvoření přechodné chyb a pouze vyvolá výjimky na jiný obnovitelné chyby.</span><span class="sxs-lookup"><span data-stu-id="8d998-123">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="8d998-124">Proto všechny výjimky, dojde při stálost jsou zpracovány jako závažné a instance pracovního postupu byl přerušen.</span><span class="sxs-lookup"><span data-stu-id="8d998-124">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="8d998-125">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="8d998-125">timeToUnload</span></span>|<span data-ttu-id="8d998-126">Časový interval hodnotu, která určuje dobu trvání v době mezi pracovního postupu se změní na nečinnosti a bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="8d998-126">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="8d998-127">Výchozí hodnota je 1 minuta.</span><span class="sxs-lookup"><span data-stu-id="8d998-127">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="8d998-128">Uvolňování pracovního postupu znamená, že je také zachována.</span><span class="sxs-lookup"><span data-stu-id="8d998-128">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="8d998-129">Pokud tento atribut je nastaven na hodnotu nula instance pracovního postupu je trvalá a odpojeno ihned po pracovního postupu změní nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="8d998-129">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="8d998-130">Nastavení tohoto atributu na hodnotu TimeSpan.MaxValue efektivně zakáže operace uvolnění.</span><span class="sxs-lookup"><span data-stu-id="8d998-130">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="8d998-131">Instance nečinných pracovních postupů jsou nikdy uvolněna.</span><span class="sxs-lookup"><span data-stu-id="8d998-131">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d998-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8d998-132">Child Elements</span></span>  
 <span data-ttu-id="8d998-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="8d998-133">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d998-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8d998-134">Parent Elements</span></span>  
  
|<span data-ttu-id="8d998-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="8d998-135">Element</span></span>|<span data-ttu-id="8d998-136">Popis</span><span class="sxs-lookup"><span data-stu-id="8d998-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d998-137">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8d998-137">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="8d998-138">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="8d998-138">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d998-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d998-139">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
