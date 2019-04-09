---
title: <Assembly> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0788c05edace2142d348c679c73aa1b4404ce75
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137849"
---
# <a name="assembly-element-net-native"></a>\<Sestavení > – Element (.NET Native)
Zásady reflexe modulu runtime se vztahuje na všechny typy v zadané sestavení.  
  
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
|`Activate`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory Povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Určuje, zadávání dotazů na informace o nebo vytváření výčtů typů v sestavení, ale neumožňuje dynamické přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.|  
|`MarshalObject`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásad pro zařazování odkazové typy Windows Runtime a modelu COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Určuje zásady pro zařazování struktur do nativního kódu.|  
  
## <a name="name-attribute"></a>Název atributu  
  
|Value|Popis|  
|-----------|-----------------|  
|*název_sestavení*|Jednoduchý název sestavení, bez jeho přípona souboru. Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnost. Název sestavení s názvem Extensions.dll je například "Rozšíření".<br /><br /> Můžete také určit řetězcového literálu `*Application*` uplatňovat zásady na všechna sestavení v balíčku aplikace, zda tato sestavení jsou načteny, nebo ne. `*Application*` nikdy použije zásady na sestavení rozhraní .NET Framework.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Value|Popis|  
|-----------|-----------------|  
|*policy_setting*|Toto nastavení platí pro tento typ zásad pro všechny typy v sestavení. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Použije zásady reflexe pro všechny typy z podřízených oborů názvů.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Použije zásady reflexe typu.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Použije zásady reflexe pro Konstruovaný obecný typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|Slouží jako kontejner pro celou aplikaci typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe v době běhu. [ \<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md) prvek může mít nula, jeden nebo více `<Assembly>` elementy.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Určuje sestavení, který obsahuje typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe v době běhu. [ \<Knihovny >](../../../docs/framework/net-native/library-element-net-native.md) prvek může mít nula nebo jedna `<Assembly>` elementu.|  
  
## <a name="remarks"></a>Poznámky  
 `<Assembly>` Element definuje zásady pro režim spuštění pro všechny typy v sestavení. Se liší od [ \<knihovny >](../../../docs/framework/net-native/library-element-net-native.md) element, který určuje knihovnu, ale závisí na jeho podřízené prvky k definování zásady reflexe modulu runtime. `<Assembly>` Element platí pro všechny typy v sestavení, pokud je nepřepíšete podřízený element.  
  
 Následující příklad ukazuje, jak je možné použít zásady modulu runtime pro všechny typy v sestavení v rámci vašeho balíčku aplikace pomocí přiřazení `Name` hodnotu atributu "* aplikace\*". `<Assembly>` Element musí být podřízeným [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) elementu.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 `Activate`, `Browse`, `Dynamic`, A `Serialize` atributy jsou nepovinné. Ale `<Assembly>` element musí obsahovat alespoň jeden z těchto atributů.  
  
## <a name="see-also"></a>Viz také:

- [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
