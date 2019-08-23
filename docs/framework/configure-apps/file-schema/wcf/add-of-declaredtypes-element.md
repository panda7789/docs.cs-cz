---
title: <add><declaredTypes> elementu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 1ea008dcc72d555b00e9648ace95bb9522ffc2c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920175"
---
# <a name="add-of-declaredtypes-element"></a>\<Přidat > \<prvku > declaredTypes
Přidá typ používaný <xref:System.Runtime.Serialization.DataContractSerializer> Při deserializaci. Každý deklarovaný typ obsahuje známé typy, které budou vráceny jako pole nebo vlastnost deklarovaného typu.  
  
 system.runtime.serialization  
\<dataContractSerializer>  
\<declaredTypes >  
\<Přidat > \<> declaredTypes  
  
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
|– typ|Požadovaný atribut typu string.<br /><br /> Určuje název typu (včetně oboru názvů), název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|Určuje známý typ pro deklarovaný typ, který se přidává. Je-li deklarovaný typ obecný typ, je nutné také přidat prvek `<knownType>` parametru k elementu pro určení, který obecný parametr slouží k vrácení známého typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|Obsahuje typy, které během deserializace <xref:System.Runtime.Serialization.DataContractSerializer>vyžadují známé typy.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Příklad použití tohoto prvku naleznete v [ \<> DataContractSerializer](datacontractserializer-element.md) .  
  
> [!NOTE]
> Pokud přidáte <xref:System.Object> typ `<declaredType>`jako, <xref:System.Configuration.ConfigurationErrorsException> je vyvolána. Důvodem je, že <xref:System.Object> typ nelze použít jako deklarovaný typ v konfiguraci.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<Přidat > \<> declaredTypes](add-of-declaredtypes-element.md)
