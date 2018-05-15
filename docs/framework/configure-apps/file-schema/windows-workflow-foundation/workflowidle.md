---
title: '&lt;workflowIdle&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 65bcc1ccd357fb7f331665aefbd975b11a2378cd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowidlegt"></a><span data-ttu-id="79c7e-102">&lt;workflowIdle&gt;</span><span class="sxs-lookup"><span data-stu-id="79c7e-102">&lt;workflowIdle&gt;</span></span>
<span data-ttu-id="79c7e-103">Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.</span><span class="sxs-lookup"><span data-stu-id="79c7e-103">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="79c7e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="79c7e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="79c7e-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="79c7e-105">\<behaviors></span></span>  
<span data-ttu-id="79c7e-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="79c7e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="79c7e-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="79c7e-107">\<behavior></span></span>  
<span data-ttu-id="79c7e-108">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="79c7e-108">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79c7e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79c7e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79c7e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="79c7e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="79c7e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="79c7e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79c7e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="79c7e-112">Attributes</span></span>  
  
|<span data-ttu-id="79c7e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="79c7e-113">Attribute</span></span>|<span data-ttu-id="79c7e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="79c7e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79c7e-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="79c7e-115">timeToPersist</span></span>|<span data-ttu-id="79c7e-116">Hodnota časového rozpětí, který určuje dobu mezi tím, kdy pracovní postup bude nečinné a je trvalá.</span><span class="sxs-lookup"><span data-stu-id="79c7e-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="79c7e-117">Výchozí hodnota je TimeSpan.MaxValue, což.</span><span class="sxs-lookup"><span data-stu-id="79c7e-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="79c7e-118">Doba trvání začíná uplynout při instance pracovního postupu se změní na nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="79c7e-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="79c7e-119">Tento atribut je užitečné, pokud chcete zachovat instanci pracovního postupu agresivnější přitom instance v paměti pro stejně dlouho.</span><span class="sxs-lookup"><span data-stu-id="79c7e-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="79c7e-120">Tento atribut je platný, pokud je jeho hodnota je menší než **timeToUnload** atribut.</span><span class="sxs-lookup"><span data-stu-id="79c7e-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="79c7e-121">Pokud je větší, je ignorována.</span><span class="sxs-lookup"><span data-stu-id="79c7e-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="79c7e-122">Pokud tento atribut uplyne před hodnotu zadanou pomocí **timeToUnload** atribut trvalost musí dokončit, než pracovní postup bude odpojen.</span><span class="sxs-lookup"><span data-stu-id="79c7e-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="79c7e-123">To znamená, že může být operace uvolnění zpožděna, dokud je trvalá pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="79c7e-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="79c7e-124">Stálost vrstvu je zodpovědná za zpracování jakékoli pokusy o vytvoření přechodné chyb a pouze vyvolá výjimky na jiný obnovitelné chyby.</span><span class="sxs-lookup"><span data-stu-id="79c7e-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="79c7e-125">Proto všechny výjimky, dojde při stálost jsou zpracovány jako závažné a instance pracovního postupu byl přerušen.</span><span class="sxs-lookup"><span data-stu-id="79c7e-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="79c7e-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="79c7e-126">timeToUnload</span></span>|<span data-ttu-id="79c7e-127">Časový interval hodnotu, která určuje dobu trvání v době mezi pracovního postupu se změní na nečinnosti a bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="79c7e-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="79c7e-128">Výchozí hodnota je 1 minuta.</span><span class="sxs-lookup"><span data-stu-id="79c7e-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="79c7e-129">Uvolňování pracovního postupu znamená, že je také zachována.</span><span class="sxs-lookup"><span data-stu-id="79c7e-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="79c7e-130">Pokud tento atribut je nastaven na hodnotu nula k instanci pracovního postupu je trvalá a uvolněna ihned po stane nečinnosti pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="79c7e-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="79c7e-131">Nastavení tohoto atributu na hodnotu TimeSpan.MaxValue efektivně zakáže operace uvolnění.</span><span class="sxs-lookup"><span data-stu-id="79c7e-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="79c7e-132">Instance nečinných pracovních postupů jsou nikdy uvolněna.</span><span class="sxs-lookup"><span data-stu-id="79c7e-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79c7e-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="79c7e-133">Child Elements</span></span>  
 <span data-ttu-id="79c7e-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="79c7e-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79c7e-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="79c7e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="79c7e-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="79c7e-136">Element</span></span>|<span data-ttu-id="79c7e-137">Popis</span><span class="sxs-lookup"><span data-stu-id="79c7e-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79c7e-138">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="79c7e-138">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="79c7e-139">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="79c7e-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79c7e-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="79c7e-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
