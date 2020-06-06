---
title: <Namespace>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: 06d88a7b0f95c7c1dbe98818b847c92e08a57a19
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180957"
---
# <a name="namespace-element-net-native"></a>\<Namespace>– Element (.NET Native)
Aplikuje zásady reflexe za běhu na všechny typy v zadaném oboru názvů.  
  
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
  
|Atribut|Typ atributu|Description|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název oboru názvů.|  
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci, která používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídu.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci JSON, které používají <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídu.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci XML, které používají <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídu.|  
|`MarshalObject`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování struktur do nativního kódu.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Hodnota|Description|  
|-----------|-----------------|  
|*namespace_name*|Název oboru názvů. Pokud \<Namespace> je prvek podřízený prvku [\<Application>](application-element-net-native.md) , [\<Library>](library-element-net-native.md) nebo [\<Assembly>](assembly-element-net-native.md) , *namespace_name* musí být plně kvalifikovaný název oboru názvů. Pokud \<Namespace> je element podřízenou položkou jiného \<Namespace> prvku, *namespace_name* musí být relativní název oboru názvů.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Description|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro všechny typy v oboru názvů Možné hodnoty jsou `All` , `Auto` , `Excluded` , `Public` , `PublicAndInternal` , `Required Public` , a `Required PublicAndInternal` `Required All` . Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`<Namespace>`|Aplikuje zásady reflexe za běhu na všechny typy v nadřazeném oboru názvů.|  
|[\<Type>](type-element-net-native.md)|Aplikuje zásadu odrazu na typ.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu. [\<Application>](application-element-net-native.md)Element může mít nulový, jeden nebo více [\<Assembly>](assembly-element-net-native.md) prvků.|  
|[\<Assembly>](assembly-element-net-native.md)|Aplikuje zásady reflexe za běhu na všechny typy v zadaném sestavení.|  
|[\<Library>](library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typů, jejichž metadata jsou k dispozici pro reflexi v době běhu. [\<Library>](library-element-net-native.md)Element může mít nula nebo jeden [\<Assembly>](assembly-element-net-native.md) element.|  
|`<Namespace>`|Aplikuje zásady odrazu na všechny typy v nadřazeném oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
 `Activate`Atributy, `Browse` , `Dynamic` a `Serialize` jsou všechny volitelné. Pokud není žádné, `<Namespace>` prvek slouží jako kontejner pro podřízené elementy. Pokud jsou k dispozici, `<Namespace>` element aplikuje zásady reflexe modulu runtime na všechny typy v zadaném oboru názvů.  
  
 V případě, že se jedná o podřízený [\<Assembly>](assembly-element-net-native.md) prvek elementu, `<Namespace>` Přepisuje ovládací prvek zásady reflexe modulu runtime definované [\<Assembly>](assembly-element-net-native.md) elementem.  
  
## <a name="see-also"></a>Viz také

- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
