---
title: '&lt;System.Runtime.Serialization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a6eb2b152f2ab11bbe0e08ff1ad22f94d45057e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemruntimeserializationgt"></a>&lt;System.Runtime.Serialization&gt;
Reprezentuje kořenový element <xref:System.Runtime.Serialization> část oboru názvů a obsahuje prvky pro nastavení možností nástroje <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 system.runtime.serialization  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer">  
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
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|Umožňuje přidání ze známých typů, který se má použít při deserializaci.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Konfigurace > elementu](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Element na nejvyšší úrovni konfigurace.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization>  
 [Použití kontraktů dat](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
