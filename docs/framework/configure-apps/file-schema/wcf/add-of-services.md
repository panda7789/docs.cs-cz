---
title: "&lt;add&gt; – &lt;services&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 040db3b350ebacfc3aff76d90e87e65206701069
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltaddgt-of-ltservicesgt"></a>&lt;add&gt; – &lt;services&gt;
Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování založené na pracovním postupu [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby. Tento element je typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<služby >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<workflowRuntime>  
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
|– typ|Řetězec, který určuje název sestavení kvalifikovaný typ služby k inicializovat. Zadaná služba musí následovat určitá pravidla o signatur jejich konstruktory. Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modul. Elementy jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Služby uvedené v kolekci se inicializovat modul runtime pracovního postupu a přidat do jeho služby při odpovídající <xref:System.Workflow.Runtime.WorkflowRuntime> volání konstruktoru. Proto služby uvedené v kolekci musí následovat určitá pravidla o signatur jejich konstruktory. Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
## <a name="remarks"></a>Poznámky  
 Zadaná služba v tomto elementu se inicializovat modul runtime pracovního postupu a přidat do jeho služby při odpovídající <xref:System.Workflow.Runtime.WorkflowRuntime> volání konstruktoru. Zadaná služba proto musí následovat určitá pravidla o signatur jejich konstruktory. Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  
  
## <a name="example"></a>Příklad  
  
```xml  
<serviceBehaviors>  
   <behavior name="ServiceBehavior">  
      <workflowRuntime name="WorkflowServiceHostRuntime"  
                       validateOnCreate="true"  
                       enablePerformanceCounters="true">  
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
 [Konfigurační soubory pracovního postupu](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
