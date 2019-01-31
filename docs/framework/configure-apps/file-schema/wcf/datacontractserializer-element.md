---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 1b4fd959d5e522150751d2e9b8be8c5b2252bf27
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254948"
---
# <a name="datacontractserializer"></a>\<dataContractSerializer>
Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>. Tento element vyskytuje ve dvou různých hierarchií. Jeden je uvedena v následující části hierarchie schémat a druhý je uveden v oddílu Poznámky.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<dataContractSerializer>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|ignoreExtensionDataObject|Logická hodnota, která určuje, jestli se má ignorovat data dodaná nástrojem koncový bod, když je serializován nebo deserializován. Tento atribut je nastavit pouze v `<dataContractSerializer>` pod `<behavior>` elementu.|  
|maxItemsInObjectGraph|Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci. Tento atribut je 65536.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|Kolekce nastavení pro chování služby.|  
|[\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|Představuje kořenový element <xref:System.Runtime.Serialization> části obor názvů a obsahuje prvky pro nastavení voleb <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Poznámky  
 Jak jsme uvedli v úvodu tohoto tématu, toto je druhá hierarchie, ve kterém \<X509Extension > element vyskytuje.  
  
 [\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 Další informace o známých typů najdete v tématu <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [Známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Přenos a serializace dat](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
