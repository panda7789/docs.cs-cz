---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c93a1f482882cc8cd9d229d82597efa64ba209bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152967"
---
# <a name="systemruntimeserialization"></a>\<system.runtime.serialization>
Představuje kořenový prvek <xref:System.Runtime.Serialization> oddílu oboru názvů a obsahuje <xref:System.Runtime.Serialization.DataContractSerializer>prvky pro nastavení možností .  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>dataContractSerializer](datacontractserializer-of-system-runtime-serialization.md)|Umožňuje přidání známých typů, které mají být použity při rekonstrukci.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<konfigurace> Element](../configuration-element.md)|Prvek nejvyšší úrovně pro konfiguraci.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization>
- [Použití kontraktů dat](../../../wcf/feature-details/using-data-contracts.md)
- [Známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md)
