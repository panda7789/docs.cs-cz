---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1d8ddaf5d69d87ff6112b5cbb285f0ccfda724e2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397538"
---
# <a name="workflowidle"></a><span data-ttu-id="037aa-101">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="037aa-101">\<workflowIdle></span></span>
<span data-ttu-id="037aa-102">Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.</span><span class="sxs-lookup"><span data-stu-id="037aa-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="037aa-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="037aa-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="037aa-104">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="037aa-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="037aa-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="037aa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="037aa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="037aa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="037aa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="037aa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="037aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowIdle >**</span><span class="sxs-lookup"><span data-stu-id="037aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="037aa-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="037aa-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="037aa-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="037aa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="037aa-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="037aa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="037aa-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="037aa-112">Attributes</span></span>  
  
|<span data-ttu-id="037aa-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="037aa-113">Attribute</span></span>|<span data-ttu-id="037aa-114">Popis</span><span class="sxs-lookup"><span data-stu-id="037aa-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="037aa-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="037aa-115">timeToPersist</span></span>|<span data-ttu-id="037aa-116">Hodnota TimeSpan, která určuje dobu mezi časem, kdy je pracovní postup neaktivní a trvalý.</span><span class="sxs-lookup"><span data-stu-id="037aa-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="037aa-117">Výchozí hodnota je TimeSpan. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="037aa-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="037aa-118">Doba trvání začíná uplynout při instance pracovního postupu se změní na nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="037aa-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="037aa-119">Tento atribut je užitečný, pokud chcete zachovat instanci pracovního postupu s více agresivními a přitom udržet instanci v paměti tak dlouho, jak je to možné.</span><span class="sxs-lookup"><span data-stu-id="037aa-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="037aa-120">Tento atribut je platný pouze v případě, že jeho hodnota je menší než atribut **TimeToUnload** .</span><span class="sxs-lookup"><span data-stu-id="037aa-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="037aa-121">Pokud je větší, je ignorována.</span><span class="sxs-lookup"><span data-stu-id="037aa-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="037aa-122">Pokud tento atribut uplyne před hodnotou určenou atributem **TimeToUnload** , musí být před uvolněním pracovního postupu dokončena trvalost.</span><span class="sxs-lookup"><span data-stu-id="037aa-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="037aa-123">To znamená, že může být operace uvolnění zpožděna, dokud je trvalá pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="037aa-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="037aa-124">Stálost vrstvu je zodpovědná za zpracování jakékoli pokusy o vytvoření přechodné chyb a pouze vyvolá výjimky na jiný obnovitelné chyby.</span><span class="sxs-lookup"><span data-stu-id="037aa-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="037aa-125">Proto všechny výjimky, dojde při stálost jsou zpracovány jako závažné a instance pracovního postupu byl přerušen.</span><span class="sxs-lookup"><span data-stu-id="037aa-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="037aa-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="037aa-126">timeToUnload</span></span>|<span data-ttu-id="037aa-127">Časový interval hodnotu, která určuje dobu trvání v době mezi pracovního postupu se změní na nečinnosti a bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="037aa-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="037aa-128">Výchozí hodnota je 1 minuta.</span><span class="sxs-lookup"><span data-stu-id="037aa-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="037aa-129">Uvolňování pracovního postupu znamená, že je také zachována.</span><span class="sxs-lookup"><span data-stu-id="037aa-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="037aa-130">Pokud je tento atribut nastaven na hodnotu nula, instance pracovního postupu je trvalá a uvolněna ihned po nečinnosti pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="037aa-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="037aa-131">Nastavení tohoto atributu na hodnotu TimeSpan. MaxValue efektivně zakáže operaci uvolnění.</span><span class="sxs-lookup"><span data-stu-id="037aa-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="037aa-132">Instance nečinných pracovních postupů jsou nikdy uvolněna.</span><span class="sxs-lookup"><span data-stu-id="037aa-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="037aa-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="037aa-133">Child Elements</span></span>  
 <span data-ttu-id="037aa-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="037aa-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="037aa-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="037aa-135">Parent Elements</span></span>  
  
|<span data-ttu-id="037aa-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="037aa-136">Element</span></span>|<span data-ttu-id="037aa-137">Popis</span><span class="sxs-lookup"><span data-stu-id="037aa-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="037aa-138">\<chování > \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="037aa-138">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="037aa-139">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="037aa-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="037aa-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="037aa-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
