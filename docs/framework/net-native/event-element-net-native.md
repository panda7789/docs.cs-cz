---
title: <Event>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 60da48d5872d7ce61afcffa7977411bc6e1efc7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181043"
---
# <a name="event-element-net-native"></a>\<Prvek> události (nativní.NET)
Použije zásady reflexe za běhu na událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název události.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování na informace o události nebo výčet události, ale neumožňuje žádný dynamický přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu k události, aby bylo možné dynamické programování. Tato zásada zajišťuje, že událost může být zpracována dynamicky za běhu.|  
  
## <a name="name-attribute"></a>Atribut Název  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název události Typ události je definován nadřazeným [ \<typem>](type-element-net-native.md) nebo [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) elementem.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro událost. Možné hodnoty `Auto` `Excluded`jsou `Included`, `Required`, a . Další informace naleznete v tématu [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<Typ>](type-element-net-native.md)|Použije zásady reflexe na typ a všechny jeho členy.|  
|[\<TypRychlé>](typeinstantiation-element-net-native.md)|Použije zásady reflexe na vytvořený obecný typ a všechny jeho členy.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud zásady události není explicitně definována, dědí zásady runtime svého nadřazeného prvku.  
  
## <a name="see-also"></a>Viz také

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
