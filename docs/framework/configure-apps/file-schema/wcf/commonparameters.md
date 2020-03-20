---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 73d8549f68e8ca77115619431c857c4a2aac3fdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153019"
---
# <a name="commonparameters"></a>\<commonParameters>
Představuje kolekci parametrů, které se používají globálně napříč více službami. Tato kolekce bude obvykle obsahovat připojovací řetězec databáze, které mohou být sdíleny trvalé služby.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<přidat>](add-of-commonparameters.md)|Přidá dvojici název-hodnota společné parametry používané služby do kolekce.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<workflowRuntime>](workflowruntime.md)|Určuje nastavení instance <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb WCF (Windows Communication Foundation) založených na pracovním postupu.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `<commonParameters>` definuje všechny parametry, které se používají globálně `ConnectionString` napříč <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>více službami, například při použití rozhraní .  
  
> [!NOTE]
> Služba sledování SQL nepoužívá `ConnectionString` konzistentně `<commonParameters>` hodnotu, pokud je zadána v části. Některé z jeho operací, `StateMachineWorkflowInstance.StateHistory` jako je například načítání vlastnosti může selhat. Chcete-li to toto řešení vyřešit, zadejte `ConnectionString` atribut v části konfigurace pro sledování zprostředkovatele, jak je uvedeno v následujícím příkladu.  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 Pro služby, které potvrdí pracovní dávky do úložišť trvalosti, například <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> a <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, můžete jim povolit opakování jejich transakce pomocí parametru, `EnableRetries` jak je znázorněno v následujícím příkladu:  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 Všimněte `EnableRetries` si, že parametr lze nastavit buď na globální úrovni (jak je znázorněno v *commonparameters* části) nebo pro jednotlivé služby, které podporují `EnableRetries` (jak je znázorněno v části *Služby).*  
  
 Následující ukázkový kód ukazuje, jak programově změnit běžné parametry:
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 Další informace o použití konfiguračního <xref:System.Workflow.Runtime.WorkflowRuntime> souboru k řízení chování objektu hostitelské aplikace služby Windows Workflow Foundation naleznete v [tématu Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
## <a name="example"></a>Příklad  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- [Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
- [\<přidat>](add-of-commonparameters.md)
