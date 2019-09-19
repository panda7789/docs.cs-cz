---
title: <Field>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dfb6a07f9733ab1a01a1ce9917c6a4bb4ce793b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049780"
---
# <a name="field-element-net-native"></a>\<Field > element (.NET Native)
Aplikuje na pole zásady reflexe modulu runtime.  
  
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
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování na informace o nebo výčet pole, ale nepovoluje žádný dynamický přístup v době běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu k poli pro povolení dynamického programování. Tato zásada zajišťuje, že pole lze v době běhu nastavit nebo načíst dynamicky.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k poli, aby se mohly instance typů serializovat pomocí knihoven, jako je Newtonsoft JSON serializátor nebo který se má použít pro datovou vazbu.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Value|Popis|  
|-----------|-----------------|  
|*method_name*|Název pole Typ pole je definován nadřazeným [ \<typem >](type-element-net-native.md) nebo [ \<elementem > TypeInstantiation](typeinstantiation-element-net-native.md) .|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Value|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro pole Možné hodnoty jsou `Auto`, `Excluded`, `Included`a. `Required` Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Zadejte >](type-element-net-native.md)|Aplikuje zásadu odrazu na typ a všechny jeho členy.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud zásady pole nejsou explicitně definovány, zdědí zásady modulu runtime svého nadřazeného prvku.  
  
## <a name="see-also"></a>Viz také:

- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
