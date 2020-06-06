---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151842"
---
# \<workflowIdle>
<span data-ttu-id="3f1d4-101">Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-101">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a><span data-ttu-id="3f1d4-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f1d4-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f1d4-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3f1d4-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3f1d4-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f1d4-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="3f1d4-105">Attributes</span></span>  
  
|<span data-ttu-id="3f1d4-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="3f1d4-106">Attribute</span></span>|<span data-ttu-id="3f1d4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3f1d4-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f1d4-108">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="3f1d4-108">timeToPersist</span></span>|<span data-ttu-id="3f1d4-109">Hodnota TimeSpan, která určuje dobu mezi časem, kdy je pracovní postup neaktivní a trvalý.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-109">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="3f1d4-110">Výchozí hodnota je TimeSpan. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-110">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="3f1d4-111">Doba trvání začíná uplynout při instance pracovního postupu se změní na nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-111">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="3f1d4-112">Tento atribut je užitečný, pokud chcete zachovat instanci pracovního postupu s více agresivními a přitom udržet instanci v paměti tak dlouho, jak je to možné.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-112">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="3f1d4-113">Tento atribut je platný pouze v případě, že jeho hodnota je menší než atribut **TimeToUnload** .</span><span class="sxs-lookup"><span data-stu-id="3f1d4-113">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="3f1d4-114">Pokud je větší, je ignorována.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-114">If it is greater, it is ignored.</span></span> <span data-ttu-id="3f1d4-115">Pokud tento atribut uplyne před hodnotou určenou atributem **TimeToUnload** , musí být před uvolněním pracovního postupu dokončena trvalost.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-115">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="3f1d4-116">To znamená, že může být operace uvolnění zpožděna, dokud je trvalá pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-116">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="3f1d4-117">Stálost vrstvu je zodpovědná za zpracování jakékoli pokusy o vytvoření přechodné chyb a pouze vyvolá výjimky na jiný obnovitelné chyby.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-117">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="3f1d4-118">Proto všechny výjimky, dojde při stálost jsou zpracovány jako závažné a instance pracovního postupu byl přerušen.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-118">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="3f1d4-119">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="3f1d4-119">timeToUnload</span></span>|<span data-ttu-id="3f1d4-120">Časový interval hodnotu, která určuje dobu trvání v době mezi pracovního postupu se změní na nečinnosti a bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-120">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="3f1d4-121">Výchozí hodnota je 1 minuta.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-121">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="3f1d4-122">Uvolňování pracovního postupu znamená, že je také zachována.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-122">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="3f1d4-123">Pokud je tento atribut nastaven na hodnotu nula, instance pracovního postupu je trvalá a uvolněna ihned po nečinnosti pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-123">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="3f1d4-124">Nastavení tohoto atributu na hodnotu TimeSpan. MaxValue efektivně zakáže operaci uvolnění.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-124">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="3f1d4-125">Instance nečinných pracovních postupů jsou nikdy uvolněna.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-125">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f1d4-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3f1d4-126">Child Elements</span></span>  
 <span data-ttu-id="3f1d4-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="3f1d4-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f1d4-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3f1d4-128">Parent Elements</span></span>  
  
|<span data-ttu-id="3f1d4-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="3f1d4-129">Element</span></span>|<span data-ttu-id="3f1d4-130">Description</span><span class="sxs-lookup"><span data-stu-id="3f1d4-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f1d4-131">\<behavior>tohoto\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3f1d4-131">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="3f1d4-132">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="3f1d4-132">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f1d4-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f1d4-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
