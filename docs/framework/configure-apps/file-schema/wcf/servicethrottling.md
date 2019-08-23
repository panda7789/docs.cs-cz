---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 77ed5e91f09d9e658deeb7996baaca445b4e0c90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937112"
---
# <a name="servicethrottling"></a>\<serviceThrottling>
Určuje mechanismus omezování služby Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<> chování  
\<serviceBehaviors>  
\<> chování  
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
|maxConcurrentCalls|Kladné celé číslo omezující počet zpráv, které jsou aktuálně zpracovány v rámci <xref:System.ServiceModel.ServiceHost>. Volání přesahující limit jsou zařazená do fronty. Nastavení této hodnoty na 0 je ekvivalentem nastavení Int32. MaxValue. Výchozí hodnota je 16 × počet procesorů.|  
|maxConcurrentInstances|Kladné celé číslo, které omezuje počet <xref:System.ServiceModel.InstanceContext> objektů, které jsou spouštěny v jednom okamžiku <xref:System.ServiceModel.ServiceHost>napříč. Žádosti o vytvoření dalších instancí se zařadí do fronty a dokončí, když se uvolní slot pod limitem. Výchozí hodnota je součet hodnot maxConcurrentSessions a MaxConcurrentCalls.|  
|maxConcurrentSessions|Kladné celé číslo omezující počet relací <xref:System.ServiceModel.ServiceHost> , které může objekt přijmout.<br /><br /> Služba bude přijímat připojení přesahující limit, ale budou aktivní jenom kanály pod limitem (zprávy se čtou z kanálu). Nastavení této hodnoty na 0 je ekvivalentem nastavení Int32. MaxValue. Výchozí hodnota je 100 × počet procesorů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> chování](behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Omezení ovládacích prvků omezuje počet souběžných volání, instancí nebo relací, které zabrání přečerpání prostředků.  
  
 Trasování je zapsáno pokaždé, když je dosaženo hodnoty atributů. První trasování je zapsáno jako varování.  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace určuje, že služba omezuje maximální počet souběžných volání na 2 a maximální počet souběžných instancí na 10. Podrobný příklad spuštění tohoto příkladu naleznete v tématu [omezování](../../../wcf/samples/throttling.md).  
  
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
- [Řízení výkonu služby WCF pomocí ServiceThrottlingBehavior](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
