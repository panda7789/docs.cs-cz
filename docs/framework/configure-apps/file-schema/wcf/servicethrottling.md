---
title: '&lt;serviceThrottling&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a059684967af26c72aca48a3fa6bb10c2f26b0c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicethrottlinggt"></a>&lt;serviceThrottling&gt;
Určuje omezení mechanismus služby Windows Communication Foundation (WCF).  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<serviceThrottling >  
  
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
|maxConcurrentCalls|Kladné celé číslo, který omezuje počet zpráv, které aktuálně zpracovávají napříč <xref:System.ServiceModel.ServiceHost>. Volání nad tento limit jsou zařazeny do fronty. Tuto hodnotu nastavíte na 0 je stejné jako jeho nastavení na Int32.MaxValue. Výchozí hodnota je 16 * počet procesorů.|  
|maxConcurrentInstances|Kladné celé číslo, které omezuje počet <xref:System.ServiceModel.InstanceContext> objekty, které jsou spouštěny v jednu chvíli napříč <xref:System.ServiceModel.ServiceHost>. Požadavky na vytvoření další instance jsou zařazeny do fronty a dokončit při slot pod limit bude k dispozici. Výchozí hodnota je součtem maxConcurrentSessions a MaxConcurrentCalls|  
|maxConcurrentSessions|Kladné celé číslo, který omezuje počet relací <xref:System.ServiceModel.ServiceHost> může přijmout objekt.<br /><br /> Služba bude akceptovat připojení nad tento limit, ale jsou aktivní pouze kanály pod limit (zprávy se načítají z kanál). Tuto hodnotu nastavíte na 0 je stejné jako jeho nastavení na Int32.MaxValue. Výchozí hodnota je 100 * počet procesorů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Omezení ovládacích prvků umístit omezení na počet souběžných volání, instancí nebo relací, aby se zabránilo nadměrné spotřeby prostředků.  
  
 Trasování je zapsán pokaždé, když je dosaženo hodnoty atributů. První trasování bude zapsáno jako upozornění.  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace určuje, že služba omezuje maximální souběžných volání 2 a maximální počet souběžných instancí do 10. Podrobný příklad spuštěných v tomto příkladu najdete v tématu [omezování](../../../../../docs/framework/wcf/samples/throttling.md).  
  
```xml  
<behaviors>   
  <serviceBehaviors>   
    <behavior name="CalculatorServiceBehavior">   
      <serviceDebug includeExceptionDetailInFaults="False" />   
      <serviceMetadata httpGetEnabled="True"/>   
      <!-- Specify throttling behavior -->  
      <serviceThrottling maxConcurrentCalls="2"   
           maxConcurrentInstances="10"/>   
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>  
 [Řízení výkonu služby WCF pomocí ServiceThrottlingBehavior](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
