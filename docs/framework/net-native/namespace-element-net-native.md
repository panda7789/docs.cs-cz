---
title: Element &lt;Namespace&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 108c27747e0b823f2315a914f8db3c8711fbb698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ltnamespacegt-element-net-native"></a>Element &lt;Namespace&gt; (.NET Native)
Modul runtime reflexe zásad platí pro všechny typy v určeném oboru názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Namespace Name="namespace_name"   
           Activate="policy_type"   
           Browse="policy_type" />  
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
|`Activate`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.|  
|`MarshalObject`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásady pro zařazování struktur nativního kódu.|  
  
## <a name="name-attribute"></a>Atribut Name.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*namespace_name*|Název oboru názvů. Pokud \<Namespace > elementu je podřízená [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md), [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md), nebo [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu *namespace_name* musí být obor názvů plně kvalifikovaný název. Pokud \<Namespace > elementu je podřízená jiné \<Namespace > elementu *namespace_name* musí být název relativní oboru názvů.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které chcete použít pro tento typ zásad pro všechny typy v oboru názvů. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`<Namespace>`|Platí pro všechny typy v oboru názvů nadřazené zásady reflexe modulu runtime.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Reflexe zásada se vztahuje na typ.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Reflexe zásada se vztahuje na vytvořený obecného typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|Slouží jako kontejner pro celou aplikaci typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu. [ \<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md) element může obsahovat nula, jednu nebo více [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md) elementy.|  
|[\<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|Modul runtime reflexe zásad platí pro všechny typy v zadaném sestavení.|  
|[\<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu. [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) element může obsahovat nula nebo jedna [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md) element.|  
|`<Namespace>`|Reflexe zásad platí pro všechny typy v oboru názvů nadřazené.|  
  
## <a name="remarks"></a>Poznámky  
 `Activate`, `Browse`, `Dynamic`, A `Serialize` atributy jsou nepovinné. Pokud žádný není přítomen `<Namespace>` element slouží pouze jako kontejner pro podřízené elementy. Pokud jsou přítomna, `<Namespace>` element platí zásady reflexe modulu runtime pro všechny typy v určeném oboru názvů.  
  
 Pokud je podřízený [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu, `<Namespace>` element přednost před zásadami reflexe runtime definované [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md) element.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
