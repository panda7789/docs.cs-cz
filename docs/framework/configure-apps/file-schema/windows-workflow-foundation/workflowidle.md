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
ms.locfileid: "32756901"
---
# <a name="ltworkflowidlegt"></a>&lt;workflowIdle&gt;
Chování služby, která určuje, kdy jsou instance nečinných pracovních postupů odpojeno a zachována.  
  
\<system.ServiceModel>  
\<chování >  
\<serviceBehaviors >  
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
|timeToPersist|Hodnota časového rozpětí, který určuje dobu mezi tím, kdy pracovní postup bude nečinné a je trvalá. Výchozí hodnota je TimeSpan.MaxValue, což.<br /><br /> Doba trvání začíná uplynout při instance pracovního postupu se změní na nečinnosti. Tento atribut je užitečné, pokud chcete zachovat instanci pracovního postupu agresivnější přitom instance v paměti pro stejně dlouho. Tento atribut je platný, pokud je jeho hodnota je menší než **timeToUnload** atribut. Pokud je větší, je ignorována. Pokud tento atribut uplyne před hodnotu zadanou pomocí **timeToUnload** atribut trvalost musí dokončit, než pracovní postup bude odpojen. To znamená, že může být operace uvolnění zpožděna, dokud je trvalá pracovního postupu. Stálost vrstvu je zodpovědná za zpracování jakékoli pokusy o vytvoření přechodné chyb a pouze vyvolá výjimky na jiný obnovitelné chyby. Proto všechny výjimky, dojde při stálost jsou zpracovány jako závažné a instance pracovního postupu byl přerušen.|  
|timeToUnload|Časový interval hodnotu, která určuje dobu trvání v době mezi pracovního postupu se změní na nečinnosti a bude uvolněna. Výchozí hodnota je 1 minuta.<br /><br /> Uvolňování pracovního postupu znamená, že je také zachována. Pokud tento atribut je nastaven na hodnotu nula k instanci pracovního postupu je trvalá a uvolněna ihned po stane nečinnosti pracovního postupu. Nastavení tohoto atributu na hodnotu TimeSpan.MaxValue efektivně zakáže operace uvolnění. Instance nečinných pracovních postupů jsou nikdy uvolněna.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování > z \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Určuje chování element.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
