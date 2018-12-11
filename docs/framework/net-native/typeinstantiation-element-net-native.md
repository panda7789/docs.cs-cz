---
title: Element &lt;TypeInstantiation&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5277b056c11de4c3e32d33c72bafc8f64ee17d05
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154822"
---
# <a name="lttypeinstantiationgt-element-net-native"></a>Element &lt;TypeInstantiation&gt; (.NET Native)
Platí pro Konstruovaný obecný typ zásady reflexe modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
                   Activate="policy_type"  
                   Browse="policy_type"  
                   Dynamic="policy_type"  
                   Serialize="policy_type"  
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
|`Name`|Obecné|Požadovaný atribut. Určuje název typu.|  
|`Arguments`|Obecné|Požadovaný atribut. Určuje argumenty obecného typu. Pokud je více argumentů, jsou odděleny čárkami.|  
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
|*type_name*|Název typu. Pokud tento `<TypeInstantiation>` element je podřízeným [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md) elementu, [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) element nebo jiného `<TypeInstantiation>` elementu, *type_ název* můžete zadat název typu bez svůj obor názvů. V opačném případě *type_name* musí obsahovat plně kvalifikovaného názvu. Název typu není upravena. Třeba <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> objektu, `<TypeInstantiation>` element může vypadat následovně:<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Argumenty atributu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*type_argument*|Určuje argumenty obecného typu. Pokud je více argumentů, jsou odděleny čárkami. Každý argument musí obsahovat plně kvalifikovaného názvu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Toto nastavení platí pro tento typ zásad pro Konstruovaný obecný typ. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Událost >](../../../docs/framework/net-native/event-element-net-native.md)|Použije zásady reflexe pro událost, které patří k tomuto typu.|  
|[\<pole >](../../../docs/framework/net-native/field-element-net-native.md)|Použije zásady reflexe pro pole, které patří k tomuto typu.|  
|[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|Použije zásady na typ, pokud byl použit tyto zásady na typ zastoupený obsahující `<TypeInstantiation>` elementu.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Použije zásady reflexe pro metody, které patří k tomuto typu.|  
|[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Použije zásady reflexe konstruované obecné metody, které patří k tomuto typu.|  
|[\<Vlastnost >](../../../docs/framework/net-native/property-element-net-native.md)|Použije zásady reflexe pro vlastnosti, které patří k tomuto typu.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Použije zásady reflexe vnořeného typu.|  
|`<TypeInstantiation>`|Použije zásady reflexe pro vnořené Konstruovaný obecný typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|Slouží jako kontejner pro celou aplikaci typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe v době běhu.|  
|[\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|Použije zásady reflexe pro všechny typy v zadané sestavení.|  
|[\<Knihovny >](../../../docs/framework/net-native/library-element-net-native.md)|Určuje sestavení, který obsahuje typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe v době běhu.|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Použije zásady reflexe pro všechny typy v oboru názvů.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Použije zásady reflexe pro typ a všechny její členy.|  
|`<TypeInstantiation>`|Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Reflexe, serializace a atributů spolupráce jsou nepovinné. Alespoň jeden musí však být k dispozici.  
  
 Pokud `<TypeInstantiation>` element je podřízeným [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), nebo [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md), elementu přepíše nastavení zásad, které jsou definované v nadřazeném prvku. Pokud [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) element definuje odpovídající definici obecného typu, `<TypeInstantiation>` přepisuje zásady reflexe modulu runtime pouze pro konkretizací zadané Konstruovaný obecný typ elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá reflexi k načtení definice obecného typu z vytvořeného <xref:System.Collections.Generic.Dictionary%602> objektu. Také používá reflexi pro zobrazení informací o <xref:System.Type> objekty, které představují sestavené obecné typy a definice obecného typu. Proměnná `b` v tomto příkladu je <xref:Windows.UI.Xaml.Controls.TextBlock> ovládacího prvku.  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 Po kompilaci s [!INCLUDE[net_native](../../../includes/net-native-md.md)] řetězce nástrojů, příklad vyvolá [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimky na řádku, který volá <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> metoda. Můžete vyloučit výjimku a zadat potřebná metadata přidáním následujícího kódu `<TypeInstantiation>` element do souboru direktiv modulu runtime:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Viz také  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
