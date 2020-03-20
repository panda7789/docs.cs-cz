---
title: <Namespace>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: 06d88a7b0f95c7c1dbe98818b847c92e08a57a19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180957"
---
# <a name="namespace-element-net-native"></a>\<Obor názvů> element (nativní.NET)
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
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, aby bylo možné aktivovat instance.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování na informace o prvcích programu, ale neumožňuje žádný přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, aby bylo možné povolit dynamické programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby instance typu mohly být serializovány a deserializovány knihovnami, jako je například serializátor Newtonsoft JSON.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Řídí zásady serializace, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> která používá třídu.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci JSON, který používá třídu. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Řídí zásady serializace XML, která používá třídu. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>|  
|`MarshalObject`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů odkazů na prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkce do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování struktur nativního kódu.|  
  
## <a name="name-attribute"></a>Atribut Název  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*namespace_name*|Název oboru názvů. Pokud \<je element obor názvů> podřízeným prvkem [ \<>aplikace ](application-element-net-native.md), [ \<>knihovny ](library-element-net-native.md)nebo [ \<>sestavení,](assembly-element-net-native.md) *musí být namespace_name* plně kvalifikovaný název oboru názvů. Pokud \<je> obor názvů podřízeným prvkem \<jiného oboru názvů> element, musí být *namespace_name* relativní název oboru názvů.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro všechny typy v oboru názvů. Možné hodnoty `All` `Auto`jsou `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , a . Další informace naleznete v tématu [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`<Namespace>`|Aplikuje zásady reflexe za běhu na všechny typy v nadřazeném oboru názvů.|  
|[\<Typ>](type-element-net-native.md)|Použije zásady reflexe na typ.|  
|[\<TypRychlé>](typeinstantiation-element-net-native.md)|Použije zásady reflexe na vytvořený obecný typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>aplikace](application-element-net-native.md)|Slouží jako kontejner pro typy pro celou aplikaci a členy typu, jejichž metadata jsou k dispozici pro reflexi za běhu. Prvek [ \<Application>](application-element-net-native.md) může mít nula, jeden nebo více [ \<prvků>sestavení.](assembly-element-net-native.md)|  
|[\<montážní>](assembly-element-net-native.md)|Aplikuje zásady reflexe za běhu na všechny typy v zadaném sestavení.|  
|[\<>knihovny](library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typu, jejichž metadata jsou k dispozici pro reflexi za běhu. [ \<Prvek Library>](library-element-net-native.md) může mít nula nebo jeden [ \<](assembly-element-net-native.md) prvek>sestavení.|  
|`<Namespace>`|Aplikuje zásady reflexe na všechny typy v nadřazeném oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Všechny `Activate` `Browse`atributy , `Dynamic`, a `Serialize` jsou volitelné. Pokud žádné nejsou `<Namespace>` k dispozici, prvek slouží pouze jako kontejner pro podřízené prvky. Pokud jsou k `<Namespace>` dispozici, prvek použije zásady reflexe za běhu na všechny typy v zadaném oboru názvů.  
  
 Pokud je podřízený matný prvek `<Namespace>` [ \<assembly>,](assembly-element-net-native.md) prvek přepíše zásady reflexe za běhu definované [ \<elementem assembly>.](assembly-element-net-native.md)  
  
## <a name="see-also"></a>Viz také

- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
