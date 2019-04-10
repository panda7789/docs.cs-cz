---
title: <Field> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c58be27334bcb862367464475a4eade5e01bdbb2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221610"
---
# <a name="field-element-net-native"></a>\<Pole > – Element (.NET Native)
Použije zásady reflexe runtime pole.  
  
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
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o nebo vytváření výčtu pole, ale neumožňuje dynamické přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k poli Povolit dynamické programování. Tato zásada zajistí, že pole můžete nastavit nebo načíst dynamicky za běhu.|  
|`Serialize`|Serializace|Nepovinný atribut. Určuje runtime přístup do pole, které chcete povolit instance typu bylo serializováno modulem knihoven, jako je například serializátor Newtonsoft JSON nebo má být použit pro vytváření datových vazeb.|  
  
## <a name="name-attribute"></a>Název atributu  
  
|Value|Popis|  
|-----------|-----------------|  
|*method_name*|Název pole. Typ pole je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Toto nastavení platí pro tento typ zásad pole. Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Použije zásady reflexe pro typ a všechny její členy.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud nejsou výslovně definované zásady polí, dědí zásady modulu runtime objektů svého nadřízeného elementu.  
  
## <a name="see-also"></a>Viz také:

- [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
