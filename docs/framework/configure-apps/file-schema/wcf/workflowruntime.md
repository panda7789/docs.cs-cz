---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: db5e1083c07d4e204eb19eaae9257ed44439132e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206561"
---
# <a name="workflowruntime"></a>\<workflowRuntime>
Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služby Windows Communication Foundation (WCF) založené na pracovních postupech.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<workflowRuntime>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|cachedInstanceExpiration|Volitelně <xref:System.TimeSpan> hodnotu, která určuje maximální dobu setrvání instance pracovního postupu v paměti ve stavu nečinnosti, než je nuceným uvolněním nebo přerušením. Pokud má aktivity typu workflowruntime `PersistenceService` které provádí unloadOnIdle, tento atribut se ignoruje.|  
|enablePerformanceCounters|Volitelná logická hodnota, která určuje, zda jsou povoleny čítače výkonu. Čítače výkonu poskytují informace o různých statistiky týkající se pracovní postup, ale mohou způsobit snížení výkonu při spuštění modulu runtime pracovního postupu, a pokud jsou spuštěny instance pracovních postupů. Výchozí hodnota je `true`.|  
|name|Řetězec obsahující název modulu runtime pracovního postupu. Název se používá ve výstupu k rozlišení tohoto modulu runtime z jiných modulů runtime, který může běžet na systému, například v čítače výkonu.<br /><br /> Výchozí hodnota je prázdný řetězec.|  
|validateOnCreate|Volitelná logická hodnota, která určuje, zda ověření definice pracovního postupu dojde při otevření WorkflowServiceHost provedeno.  Když tento atribut je nastaven na `true`, provádí se ověření pracovního postupu pokaždé, když `WorkflowServiceHost.Open` je volána. Pokud byly zjištěny chyby ověřování, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> , je vržena chyba.<br /><br /> Pokud je tato vlastnost nastavena na `false`, stane se žádné ověření definice pracovního postupu.<br /><br /> Výchozí hodnota této vlastnosti je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|commonParameters|Kolekce společných parametrů, které jsou používané službami. Tato kolekce bude obvykle obsahují řetězec připojení k databázi, kterou může sdílet trvalé služby.|  
|služby|Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modul. Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Služby uvedené v kolekci inicializoval modul runtime pracovního postupu, který se přidá do jeho služby při odpovídající <xref:System.Workflow.Runtime.WorkflowRuntime> volání konstruktoru. Proto služby uvedené v kolekci musí následovat některá pravidla týkající se podpisy jejich konstruktory. Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o použití konfiguračního souboru pro řízení chování <xref:System.Workflow.Runtime.WorkflowRuntime> objekt hostitele aplikace Windows Workflow Foundation, najdete v článku [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
## <a name="example"></a>Příklad  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- [Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
