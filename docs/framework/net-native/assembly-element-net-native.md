---
title: <Assembly>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
ms.openlocfilehash: f3cf65b185b1db3289a0dbb785c2b91431951cc2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181071"
---
# <a name="assembly-element-net-native"></a>\<Prvek> sestavení (nativní.NET)
Aplikuje zásady reflexe za běhu na všechny typy v zadaném sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Assembly Name="assembly_name"
          Activate="policy_setting"  
          Browse="policy_setting"  
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
|`Name`|Obecné|Požadovaný atribut. Určuje jednoduchý název sestavení.|  
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, aby bylo možné aktivovat instance.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování na informace o nebo výčtu typů v sestavení, ale neumožňuje žádný dynamický přístup za běhu.|  
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
|*assembly_name*|Jednoduchý název sestavení bez jeho přípony souboru. Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnosti. Například název sestavení s názvem Extensions.dll je "Rozšíření".<br /><br /> Můžete také zadat literál řetězec `*Application*` použít zásady pro všechna sestavení v balíčku aplikace, bez ohledu na to, zda jsou načteny nebo ne. `*Application*`nikdy nepoužije zásady pro sestavení rozhraní .NET Framework.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro všechny typy v sestavení. Možné hodnoty `All` `Auto`jsou `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , a . Další informace naleznete v tématu [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>oboru názvů](namespace-element-net-native.md)|Použije zásady reflexe na všechny typy v podřízeném oboru názvů.|  
|[\<Typ>](type-element-net-native.md)|Použije zásady reflexe na typ.|  
|[\<TypRychlé>](typeinstantiation-element-net-native.md)|Použije zásady reflexe na vytvořený obecný typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>aplikace](application-element-net-native.md)|Slouží jako kontejner pro typy pro celou aplikaci a členy typu, jejichž metadata jsou k dispozici pro reflexi za běhu. [ \<Prvek Aplikace>](application-element-net-native.md) může mít nula, jeden nebo více `<Assembly>` prvků.|  
|[\<>knihovny](library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typu, jejichž metadata jsou k dispozici pro reflexi za běhu. [ \<Prvek Library>](library-element-net-native.md) může mít nulu nebo jeden `<Assembly>` prvek.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `<Assembly>` definuje zásady runtime pro všechny typy v sestavení. Liší se od [ \<library>](library-element-net-native.md) element, který určuje knihovnu, ale závisí na jeho podřízené prvky definovat zásady reflexe za běhu. Prvek `<Assembly>` se vztahuje na všechny typy v sestavení, pokud nejsou přepsány podřízeným prvkem.  
  
 Následující příklad ukazuje, jak můžete použít zásady runtime pro všechny typy v `Name` sestaveních v rámci\*balíčku aplikace přiřazením atributu hodnotu "*Aplikace ". Prvek `<Assembly>` musí být podřízený [ \<prvek Application>.](application-element-net-native.md)  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>  
```  
  
 Všechny `Activate` `Browse`atributy , `Dynamic`, a `Serialize` jsou volitelné. `<Assembly>` Prvek však musí obsahovat alespoň jeden z těchto atributů.  
  
## <a name="see-also"></a>Viz také

- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
