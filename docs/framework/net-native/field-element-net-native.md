---
title: Element &lt;Field&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b713eefa4f23aec34b5f55c0c3457381f54ef931
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ltfieldgt-element-net-native"></a>Element &lt;Field&gt; (.NET Native)
Platí zásady reflexe modulu runtime pro pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název pole.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o nebo vytváření výčtu pole, ale neumožňuje žádné dynamické přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup do pole, které chcete povolit dynamické programování. Tato zásada zajistí, že pole můžete nastavit nebo načíst dynamicky za běhu.|  
|`Serialize`|Serializace|Nepovinný atribut. Určuje runtime přístup do pole, které chcete povolit instance typu bylo serializováno modulem knihovny například serializátor Newtonsoft JSON nebo má být použit pro datové vazby.|  
  
## <a name="name-attribute"></a>Atribut Name.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název pole. Typ pole je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které chcete použít pro tento typ zásad pro pole. Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Reflexe zásada se vztahuje na typ a všechny její členy.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Reflexe zásada se vztahuje na sestavené obecné typy a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud pole zásady nejsou výslovně definované, dědí zásady modulu runtime objektů svého nadřízeného elementu.  
  
## <a name="see-also"></a>Viz také  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
