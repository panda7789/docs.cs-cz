---
title: '&lt;declaredTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3066ee9247e69c746c28251b975bb80425ccbc8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltdeclaredtypesgt"></a>&lt;declaredTypes&gt;
Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.  
  
 Další informace o kontraktech dat a známé typy najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 system.runtime.serialization  
\<dataContractSerializer >  
\<declaredTypes >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
                <parameter index="Integer"/>  
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
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|Přidá typy, které vyžadují známé typy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]známé typy, najdete v části [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje deklarované známé typy a přidat do `DataContractSerializer` elementu. Příklad ukazuje tři typy, který chcete přidat. První je vlastního typu s názvem "Objednávky", který používá známý typ s názvem "Položka". Druhý deklarovaný typ <xref:System.Collections.Generic.List%601> používající `Item` jako známému typu. Nakonec třetí deklarovaný typ <xref:System.Collections.Generic.Dictionary%602>. <xref:System.Collections.Generic.Dictionary%602> Typu třídy je obecného typu, s parametry dva typy. Představuje klíč první a druhý představuje hodnotu. Následující příklad přidá <xref:System.Collections.Generic.List%601> druhého typu (hodnota) do seznamu ze známých typů. Je nutné použít `index` které parametr typu pro použití v známý typ žádné atributy. Typ hodnoty v tomto případě je indikován atribut index, který je nastavený na hodnotu "1" (kolekce je počítáno od nuly).  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
            <parameter index="1"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [Známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
