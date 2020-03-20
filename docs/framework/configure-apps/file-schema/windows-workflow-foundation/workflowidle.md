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
# <a name="workflowidle"></a>\<workflowIdle>
Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|timeToPersist|Hodnota Timespan, která určuje dobu mezi dobou, kdy se pracovní postup stane neaktivním a je trvalý. Výchozí hodnota je TimeSpan.MaxValue.<br /><br /> Doba trvání začíná uplynout při instance pracovního postupu se změní na nečinnosti. Tento atribut je užitečný, pokud chcete zachovat instanci pracovního postupu agresivněji při zachování instance v paměti tak dlouho, jak je to možné. Tento atribut je platný pouze v případě, že jeho hodnota je menší než atribut **timeToUnload.** Pokud je větší, je ignorována. Pokud tento atribut uplyne před hodnotou určenou atributem **timeToUnload,** musí být trvalost dokončena před uvolněním pracovního postupu. To znamená, že může být operace uvolnění zpožděna, dokud je trvalá pracovního postupu. Stálost vrstvu je zodpovědná za zpracování jakékoli pokusy o vytvoření přechodné chyb a pouze vyvolá výjimky na jiný obnovitelné chyby. Proto všechny výjimky, dojde při stálost jsou zpracovány jako závažné a instance pracovního postupu byl přerušen.|  
|timeToUnload|Časový interval hodnotu, která určuje dobu trvání v době mezi pracovního postupu se změní na nečinnosti a bude uvolněna. Výchozí hodnota je 1 minuta.<br /><br /> Uvolňování pracovního postupu znamená, že je také zachována. Pokud je tento atribut nastaven na nulu, instance pracovního postupu je trvalá a uvolněná ihned po nečinnosti pracovního postupu. Nastavení tohoto atributu timespan.maxvalue účinně zakáže operaci uvolnění. Instance nečinných pracovních postupů jsou nikdy uvolněna.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<chování> \<serviceBehaviors>](behavior-of-servicebehaviors-of-workflow.md)|Určuje chování element.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
