---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: d12656b77fa219080382603fd04a542d2fa9064a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399078"
---
# \<workflowRuntime>
Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb Windows Communication Foundation založených na pracovních postupech (WCF).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
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
|cachedInstanceExpiration|Volitelná <xref:System.TimeSpan> hodnota, která určuje maximální dobu, po kterou může instance pracovního postupu zůstat v paměti ve stavu nečinnosti, než bude vynuceně uvolněna nebo přerušena. Pokud je v aktivitě typu WorkflowRuntime `PersistenceService` proveden UnloadOnIdle, tento atribut se ignoruje.|  
|enablePerformanceCounters|Volitelná logická hodnota, která určuje, zda jsou povoleny čítače výkonu. Čítače výkonu poskytují informace o různých statistikách vztahujících se k pracovním postupům, ale způsobují snížení výkonu při spuštění modulu runtime pracovního postupu a při spuštěných instancích pracovního postupu. Výchozí hodnota je `true`.|  
|name|Řetězec, který obsahuje název modulu runtime pracovního postupu. Název se používá ve výstupu k odlišení tohoto modulu runtime od jiných modulů runtime, které mohou být spuštěny v systému, například v čítačích výkonu.<br /><br /> Výchozí hodnota je prázdný řetězec.|  
|validateOnCreate|Volitelná logická hodnota, která určuje, zda bude při otevření hostitele WorkflowServiceHost provedeno ověření definice pracovního postupu.  Pokud je tento atribut nastaven na `true` , je provedeno ověření pracovního postupu při každém `WorkflowServiceHost.Open` volání. Pokud jsou nalezeny chyby ověřování, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> je vyvolána chyba.<br /><br /> Pokud je tato vlastnost nastavena na hodnotu `false` , nebude provedena žádná validace definice pracovního postupu.<br /><br /> Výchozí hodnota této vlastnosti je `true` .|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|commonParameters|Kolekce běžných parametrů používaných službami. Tato kolekce obvykle zahrnuje připojovací řetězec databáze, který může sdílet trvalé služby.|  
|services|Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modulu. Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .  Služby zadané v kolekci budou inicializovány modulem runtime pracovního postupu a přidány ke svým službám při <xref:System.Workflow.Runtime.WorkflowRuntime> volání příslušného konstruktoru. Proto musí služby zadané v kolekci dodržovat určitá pravidla týkající se signatur jejich konstruktorů. Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o tom, jak pomocí konfiguračního souboru řídit chování <xref:System.Workflow.Runtime.WorkflowRuntime> objektu programovací model Windows Workflow Foundation hostitelské aplikace, najdete v tématu [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- [Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
