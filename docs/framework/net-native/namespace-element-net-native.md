---
title: <Namespace> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: b6d7a45de14d0fb8eb2e27a02c86510f630be9e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128265"
---
# <a name="namespace-element-net-native"></a>\<> elementu oboru názvů (.NET Native)
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
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název oboru názvů.|  
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci, která používá třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci JSON, které používají třídu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci XML, které používají třídu <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování struktur do nativního kódu.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*namespace_name*|Název oboru názvů. Pokud \<obor názvů > prvek je podřízenou položkou [\<aplikace >](application-element-net-native.md), [\<knihovny](library-element-net-native.md)> nebo [\<sestavení >](assembly-element-net-native.md) elementu, musí být *namespace_name* plně kvalifikovaný název oboru názvů. Pokud \<obor názvů > element je podřízenou položkou jiného \<oboru názvů > elementu, *namespace_name* musí být relativní název oboru názvů.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro všechny typy v oboru názvů Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`<Namespace>`|Aplikuje zásady reflexe za běhu na všechny typy v nadřazeném oboru názvů.|  
|[Typ\<](type-element-net-native.md)|Aplikuje zásadu odrazu na typ.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> aplikace](application-element-net-native.md)|Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu. [> Prvek\<aplikace](application-element-net-native.md) může mít nula, jednu nebo více [\<> prvků sestavení](assembly-element-net-native.md) .|  
|[\<> sestavení](assembly-element-net-native.md)|Aplikuje zásady reflexe za běhu na všechny typy v zadaném sestavení.|  
|[> knihovny \<](library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typů, jejichž metadata jsou k dispozici pro reflexi v době běhu. [> Element knihovny\<](library-element-net-native.md) může mít nula nebo jeden [\<> element Assembly](assembly-element-net-native.md) .|  
|`<Namespace>`|Aplikuje zásady odrazu na všechny typy v nadřazeném oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Atributy `Activate`, `Browse`, `Dynamic`a `Serialize` jsou všechny volitelné. Pokud není žádný, `<Namespace>` prvek slouží pouze jako kontejner pro podřízené elementy. Pokud jsou k dispozici, element `<Namespace>` aplikuje zásady reflexe modulu runtime na všechny typy v zadaném oboru názvů.  
  
 Pokud se jedná o podřízenou položku [\<sestavení >](assembly-element-net-native.md) elementu, prvek `<Namespace>` Přepisuje zásady reflexe modulu runtime definované elementem [\<sestavení >](assembly-element-net-native.md) .  
  
## <a name="see-also"></a>Viz také:

- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
