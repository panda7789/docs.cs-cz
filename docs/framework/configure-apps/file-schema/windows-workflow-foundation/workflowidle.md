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
# <a name="workflowidle"></a>\<workflowIdle >
Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.  
  
\<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<workflowIdle >  
  
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
|timeToPersist|Časový interval hodnotu, která určuje dobu trvání mezi čas změní na nečinnosti a je trvalá pracovního postupu. Výchozí hodnota je hodnotu TimeSpan.MaxValue.<br /><br /> Doba trvání začíná uplynout při instance pracovního postupu se změní na nečinnosti. Tento atribut je užitečné, pokud chcete zachovat instance pracovního postupu agresivnější stále zachováním instance v paměti pro co nejdéle. Tento atribut je platná pouze pokud její hodnota je menší než **timeToUnload** atribut. Pokud je větší, je ignorována. Pokud tento atribut uplyne hodnotu zadanou proměnnou **timeToUnload** atributu, stálost, musíte dokončit pracovní postup bude odpojen. To znamená, že může být operace uvolnění zpožděna, dokud je trvalá pracovního postupu. Stálost vrstvu je zodpovědná za zpracování jakékoli pokusy o vytvoření přechodné chyb a pouze vyvolá výjimky na jiný obnovitelné chyby. Proto všechny výjimky, dojde při stálost jsou zpracovány jako závažné a instance pracovního postupu byl přerušen.|  
|timeToUnload|Časový interval hodnotu, která určuje dobu trvání v době mezi pracovního postupu se změní na nečinnosti a bude uvolněna. Výchozí hodnota je 1 minuta.<br /><br /> Uvolňování pracovního postupu znamená, že je také zachována. Pokud tento atribut je nastaven na hodnotu nula instance pracovního postupu je trvalá a odpojeno ihned po pracovního postupu změní nečinnosti. Nastavení tohoto atributu na hodnotu TimeSpan.MaxValue efektivně zakáže operace uvolnění. Instance nečinných pracovních postupů jsou nikdy uvolněna.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování > z \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Určuje chování element.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
