---
title: <add> z <declaredTypes> – Element
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 9b280a63e85beac3231bc1a414430239bea4a1f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111511"
---
# <a name="add-of-declaredtypes-element"></a>\<Přidat > z \<declaredTypes > – Element
Přidá typ používaný <xref:System.Runtime.Serialization.DataContractSerializer> během deserializace. Každý deklarovaný typ obsahuje známé typy, které budou vráceny jako pole nebo vlastnost deklarovaného typu.  
  
 system.runtime.serialization  
\<dataContractSerializer>  
\<declaredTypes>  
\<Přidat > z \<declaredTypes >  
  
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
| – typ|Požadovaný atribut typu string.<br /><br /> Určuje název typu (včetně oboru názvů), název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<knownType>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Určuje známý typ deklarovaný typ, který je přidáván. Pokud je deklarovaný typ obecného typu, pak musíte taky přidat prvek parametru, který se `<knownType>` element k určení, které obecný parametr se používá k vrácení známého typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<declaredTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|Obsahuje typy, které vyžadují během deserializace za pomocí známých typů <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o známých typů najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Zobrazit [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto prvku.  
  
> [!NOTE]
>  Pokud chcete přidat <xref:System.Object> jako typ `<declaredType>`, <xref:System.Configuration.ConfigurationErrorsException> je vyvolána výjimka. Je to proto, <xref:System.Object> typ nelze použít jako deklarovaný typ v konfiguraci.  
  
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
- [Známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [\<Přidat > z \<declaredTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
