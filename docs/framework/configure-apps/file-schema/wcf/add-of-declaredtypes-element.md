---
title: <add><declaredTypes>elementu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: a001e8743b2c24f68b1b23cbccf3e5ac162c4e71
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400661"
---
# <a name="add-of-declaredtypes-element"></a>\<add>\<declaredTypes>elementu
Přidá typ používaný <xref:System.Runtime.Serialization.DataContractSerializer> Při deserializaci. Každý deklarovaný typ obsahuje známé typy, které budou vráceny jako pole nebo vlastnost deklarovaného typu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|typ|Povinný atribut řetězce.<br /><br /> Určuje název typu (včetně oboru názvů), název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|Určuje známý typ pro deklarovaný typ, který se přidává. Je-li deklarovaný typ obecný typ, je nutné také přidat prvek parametru k `<knownType>` elementu pro určení, který obecný parametr slouží k vrácení známého typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|Obsahuje typy, které během deserializace vyžadují známé typy <xref:System.Runtime.Serialization.DataContractSerializer> .|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)Příklad použití tohoto prvku naleznete v tématu.  
  
> [!NOTE]
> Pokud přidáte <xref:System.Object> typ jako `<declaredType>` , <xref:System.Configuration.ConfigurationErrorsException> je vyvolána. Důvodem je, že <xref:System.Object> typ nelze použít jako deklarovaný typ v konfiguraci.  
  
## <a name="example"></a>Příklad  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>tohoto\<declaredTypes>](add-of-declaredtypes-element.md)
