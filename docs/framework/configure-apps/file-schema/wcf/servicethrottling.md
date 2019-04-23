---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 995ff9979096757225c9241e977f86f755955945
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158766"
---
# <a name="servicethrottling"></a>\<serviceThrottling>
Určuje mechanismus omezení služby Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceThrottling>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|maxConcurrentCalls|Kladné celé číslo omezující počet zpráv, které právě zpracovat přes <xref:System.ServiceModel.ServiceHost>. Volání nad tento limit se zařadí do fronty. Tuto hodnotu nastavíte na 0 je rovnocenná ji nastavíte na hodnotu Int32.MaxValue. Výchozí hodnota je 16 * počet procesorů.|  
|maxConcurrentInstances|Kladné celé číslo omezující počet <xref:System.ServiceModel.InstanceContext> objekty, které jsou spuštěny v jednu chvíli napříč <xref:System.ServiceModel.ServiceHost>. Požadavky na vytvoření další instance se zařadí do fronty a dokončit, jakmile je k dispozici slot pod limit. Výchozí hodnota je součtem maxConcurrentSessions a MaxConcurrentCalls|  
|maxConcurrentSessions|Kladné celé číslo omezující počet relací <xref:System.ServiceModel.ServiceHost> může přijmout objekt.<br /><br /> Služba bude akceptovat připojení nad tento limit, ale pouze kanály pod limit jsou aktivní (zprávy načtené z kanálu). Tuto hodnotu nastavíte na 0 je rovnocenná ji nastavíte na hodnotu Int32.MaxValue. Výchozí hodnota je 100 * počet procesorů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Omezení ovládacích prvků umístit omezení na počtu souběžných volání, instance nebo relace, aby se zabránilo typu over-pass-the spotřebu prostředků.  
  
 Trasování bude zapsáno pokaždé, když je dosaženo hodnoty atributů. První trasování bude zapsáno jako upozornění.  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace určuje, že služba omezuje maximální souběžných volání 2 a maximální počet souběžných instancí do 10. Podrobný příklad spuštěním tohoto příkladu, naleznete v tématu [omezování](../../../../../docs/framework/wcf/samples/throttling.md).  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [Řízení výkonu služby WCF pomocí ServiceThrottlingBehavior](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
