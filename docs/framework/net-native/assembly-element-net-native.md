---
title: Element &lt;Assembly&gt; (.NET Native)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a34e49e4d11f442f15db2f06b330b8b84a165a08
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="ltassemblygt-element-net-native"></a>Element &lt;Assembly&gt; (.NET Native)
Modul runtime reflexe zásad platí pro všechny typy v zadaném sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Assembly Name="assembly_name"   
          Activate="policy_setting"  
          Browse="policy_setting"  
          Dynamic="policy_setting"  
          Serialize="policy_setting" />  
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
|`Activate`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o nebo vytváření výčtu typy v sestavení, ale neumožňuje žádné dynamické přístup za běhu.|  
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
|*assembly_name*|Jednoduchý název sestavení, bez jeho přípona souboru. Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnost. Název sestavení s názvem Extensions.dll je například "Rozšíření".<br /><br /> Můžete také určit řetězcového literálu `*Application*` uplatňovat zásady na všechna sestavení v balíčku aplikace se, zda tato sestavení jsou načteny, nebo ne. `*Application*` nikdy platí zásady pro sestavení rozhraní .NET Framework.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které chcete použít pro tento typ zásad pro všechny typy v sestavení. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Reflexe zásad platí pro všechny typy v oboru názvů podřízené.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Reflexe zásada se vztahuje na typ.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Reflexe zásada se vztahuje na vytvořený obecného typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|Slouží jako kontejner pro celou aplikaci typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu. [ \<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md) element může obsahovat nula, jednu nebo více `<Assembly>` elementy.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu. [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) element může obsahovat nula nebo jedna `<Assembly>` elementu.|  
  
## <a name="remarks"></a>Poznámky  
 `<Assembly>` Element definuje zásady modulu runtime pro všechny typy v sestavení. Liší se od [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) element, který určuje knihovnu, ale závisí na její podřízené elementy definovat zásady reflexe modulu runtime. `<Assembly>` Element platí pro všechny typy v sestavení, pokud jsou přepsány podřízený element.  
  
 Následující příklad ukazuje, jak můžete použít zásady modulu runtime pro všechny typy v sestavení v rámci vašeho balíčku aplikace přiřazením `Name` hodnotu atributu "* aplikace\*". `<Assembly>` Element musí být podřízenou [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) element.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 `Activate`, `Browse`, `Dynamic`, A `Serialize` atributy jsou nepovinné. Ale `<Assembly>` element musí obsahovat alespoň jeden z těchto atributů.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
