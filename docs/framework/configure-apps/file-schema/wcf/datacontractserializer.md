---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400434"
---
# <a name="datacontractserializer"></a>dataContractSerializer
Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
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
|ignoreExtensionDataObject|Logická hodnota, která určuje, zda se mají ignorovat data poskytnutá koncovým bodem při jeho serializaci nebo deserializaci.|  
|maxItemsInObjectGraph|Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.Runtime.Serialization.DataContractSerializer>Další informace o známých typech naleznete v dokumentaci.  
  
> [!CAUTION]
> `<dataContractSerializer>`Prvek chování (je-li k dispozici) by se měl vždy zobrazit před `<enableWebScript>` prvkem chování v konfiguračním souboru. V opačném případě není výsledné chování definováno.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [Známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md)
- [Přenos a serializace dat](../../../wcf/feature-details/data-transfer-and-serialization.md)
