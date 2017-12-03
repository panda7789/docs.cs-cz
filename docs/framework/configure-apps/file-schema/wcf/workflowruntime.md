---
title: "&lt;modul runtime pracovního postupu&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: db891e9d967f4471e2b0a3778db433adb62e121c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowruntimegt"></a>&lt;modul runtime pracovního postupu&gt;
Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování založené na pracovním postupu [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby.  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<modul runtime pracovního postupu >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"  
                                  enablePerformanceCounters="Boolean"  
                                  name="String"  
                                  validateOnCreate="Boolean">  
                 <commonParameters>  
                    <add name="String" value="String" />  
                 </commonParameters>  
                 <services>  
                    <add type="String"/>  
                 </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|cachedInstanceExpiration|Volitelný <xref:System.TimeSpan> hodnotu, která určuje maximální dobu trvání instanci pracovního postupu můžete zůstat v paměti ve stavu nečinnosti, než je vynuceně odpojeno nebo přerušena. Pokud modul runtime pracovního postupu má `PersistenceService` která provede unloadOnIdle, tento atribut je ignorován.|  
|enablePerformanceCounters|Volitelné logická hodnota, která určuje, zda jsou povoleny čítače výkonu. Čítače výkonu poskytují informace o různé statistické údaje související s pracovního postupu, ale mohou způsobit snížení výkonu při spuštění modulu runtime pracovního postupu, a když jsou spuštěné instance pracovního postupu. Výchozí hodnota je `true`.|  
|name|Řetězec, který obsahuje název modulu runtime pracovního postupu. Název se používá ve výstupu k rozlišení tento modul runtime z jiné moduly runtime, který může běžet na systému, například ve čítače výkonu.<br /><br /> Výchozí hodnota je prázdný řetězec.|  
|validateOnCreate|Volitelné logická hodnota, která určuje, zda ověření definice pracovního postupu se stane, když je otevřen hostitele služby pracovního postupu.  Když tento atribut je nastaven na `true`, ověření pracovního postupu se spustí pokaždé, když `WorkflowServiceHost.Open` je volána. Pokud jsou zjištěny chyby ověřování, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> , je vržena chyba.<br /><br /> Pokud je tato vlastnost nastavená na `false`, se stane žádné ověření definice pracovního postupu.<br /><br /> Výchozí hodnota pro tuto vlastnost je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|commonParameters|Kolekce společných parametrů, které jsou používané službami. Tato kolekce bude obvykle obsahovat připojovací řetězec databáze, který může být sdílen trvalé služby.|  
|služby|Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modul. Elementy jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Služby uvedené v kolekci se inicializovat modul runtime pracovního postupu a přidat do jeho služby při odpovídající <xref:System.Workflow.Runtime.WorkflowRuntime> volání konstruktoru. Proto služby uvedené v kolekci musí následovat určitá pravidla o signatur jejich konstruktory. Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o použití konfiguračního souboru pro řízení chování <xref:System.Workflow.Runtime.WorkflowRuntime> objekt hostitele aplikace Windows Workflow Foundation, najdete v části [konfigurační soubory pracovního postupu](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).  
  
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
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [Konfigurační soubory pracovního postupu](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
