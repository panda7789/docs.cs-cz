---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: e24dae47171f741af064ca2eaa822928690acf6e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400455"
---
# \<dataContractSerializer>
Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer> . Tento prvek se vyskytuje ve dvou různých hierarchiích. Jedna je uvedena v následující části hierarchie schématu a druhá je uvedena v části poznámky.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Prvek|Description|  
|-------------|-----------------|  
|ignoreExtensionDataObject|Logická hodnota, která určuje, zda mají být při serializaci nebo deserializaci ignorována data poskytnutá koncovým bodem. Tento atribut lze nastavit pouze v `<dataContractSerializer>` rámci `<behavior>` elementu.|  
|maxItemsInObjectGraph|Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci. Tento atribut je 65536.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|Kolekce nastavení pro chování služby.|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|Představuje kořenový prvek <xref:System.Runtime.Serialization> oddílu oboru názvů a obsahuje prvky pro nastavení možností <xref:System.Runtime.Serialization.DataContractSerializer> .|  
  
## <a name="remarks"></a>Poznámky  
 Jak je uvedeno v úvodu tohoto tématu, je to druhá hierarchie, ve které se \<X509Extension> element vyskytuje.  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 Další informace o známých typech naleznete v tématu <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [Známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md)
- [Přenos a serializace dat](../../../wcf/feature-details/data-transfer-and-serialization.md)
