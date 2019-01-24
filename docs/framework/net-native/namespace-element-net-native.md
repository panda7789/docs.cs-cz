---
title: Element &lt;Namespace&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f89c9edf47edcb5089e094529b8e8108271518d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590571"
---
# <a name="ltnamespacegt-element-net-native"></a>Element &lt;Namespace&gt; (.NET Native)
Zásady reflexe modulu runtime se vztahuje na všechny typy v určeném oboru názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Namespace Name="namespace_name"   
           Activate="policy_type"   
           Browse="policy_type"  
           Dynamic="policy_setting"  
           Serialize="policy_setting"  
           DataContractSerializer="policy_setting"  
           DataContractJsonSerializer="policy_setting"  
           XmlSerializer="policy_setting"  
           MarshalObject="policy_setting"  
           MarshalDelegate="policy_setting"  
           MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název oboru názvů.|  
|`Activate`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory Povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky, zadávání dotazů na informace o prvcích program, ale neumožňuje přístup modulu runtime.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.|  
|`MarshalObject`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásad pro zařazování odkazové typy Windows Runtime a modelu COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Určuje zásady pro zařazování struktur do nativního kódu.|  
  
## <a name="name-attribute"></a>Název atributu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*namespace_name*|Název oboru názvů. Pokud \<Namespace > element je podřízeným prvkem [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md), [ \<knihovny >](../../../docs/framework/net-native/library-element-net-native.md), nebo [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu *namespace_name* musí být plně kvalifikovaný obor názvů. Pokud \<Namespace > element je podřízeným prvkem jiného \<Namespace > elementu *namespace_name* musí být název oboru názvů relativní.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Toto nastavení platí pro tento typ zásad pro všechny typy v oboru názvů. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`<Namespace>`|Platí pro všechny typy v oboru nadřazené zásady reflexe modulu runtime.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Použije zásady reflexe typu.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Použije zásady reflexe pro Konstruovaný obecný typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|Slouží jako kontejner pro celou aplikaci typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe v době běhu. [ \<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md) prvek může mít nula, jeden nebo více [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md) elementy.|  
|[\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|Zásady reflexe modulu runtime se vztahuje na všechny typy v zadané sestavení.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Určuje sestavení, který obsahuje typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe v době běhu. [ \<Knihovny >](../../../docs/framework/net-native/library-element-net-native.md) prvek může mít nula nebo jedna [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu.|  
|`<Namespace>`|Použije zásady reflexe pro všechny typy v oboru nadřazené.|  
  
## <a name="remarks"></a>Poznámky  
 `Activate`, `Browse`, `Dynamic`, A `Serialize` atributy jsou nepovinné. Pokud nejsou k dispozici, `<Namespace>` prvek slouží pouze jako kontejner pro podřízené prvky. Pokud jsou k dispozici, `<Namespace>` element platí zásady reflexe modulu runtime pro všechny typy v určeném oboru názvů.  
  
 Když je podřízeným prvkem [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu, `<Namespace>` prvek přepisuje zásady reflexe modulu runtime definované [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu.  
  
## <a name="see-also"></a>Viz také:
- [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
