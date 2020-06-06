---
title: <TypeInstantiation>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
ms.openlocfilehash: 9069856b3d8739724d148b5eea5d4188c8b8b9e1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128683"
---
# <a name="typeinstantiation-element-net-native"></a>\<TypeInstantiation>– Element (.NET Native)
Aplikuje zásady reflexe za běhu na konstruovaný obecný typ.  
  
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
  
|Atribut|Typ atributu|Description|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název typu.|  
|`Arguments`|Obecné|Požadovaný atribut. Určuje argumenty obecného typu. Pokud je přítomno více argumentů, jsou odděleny čárkami.|  
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
|*type_name*|Název typu. Je-li tento `<TypeInstantiation>` prvek podřízený [\<Namespace>](namespace-element-net-native.md) prvku elementu, [\<Type>](type-element-net-native.md) prvku nebo jiného `<TypeInstantiation>` prvku, *TYPE_NAME* lze zadat název typu bez jeho oboru názvů. Jinak *TYPE_NAME* musí zahrnovat plně kvalifikovaný název typu. Název typu není upravený. Například pro <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> objekt `<TypeInstantiation>` může být element vypadat takto:<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Arguments – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|*type_argument*|Určuje argumenty obecného typu. Pokud je přítomno více argumentů, jsou odděleny čárkami. Každý argument musí obsahovat plně kvalifikovaný název typu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Description|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro konstruovaný obecný typ. Možné hodnoty jsou `All` , `Auto` , `Excluded` , `Public` , `PublicAndInternal` , `Required Public` , a `Required PublicAndInternal` `Required All` . Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<Event>](event-element-net-native.md)|Aplikuje zásadu odrazu na událost, která patří k tomuto typu.|  
|[\<Field>](field-element-net-native.md)|Aplikuje zásadu odrazu na pole patřící do tohoto typu.|  
|[\<ImpliesType>](impliestype-element-net-native.md)|Použije zásady na typ, pokud byly tyto zásady použity na typ reprezentovaný nadřazeným `<TypeInstantiation>` prvkem.|  
|[\<Method>](method-element-net-native.md)|Aplikuje zásadu odrazu na metodu, která patří tomuto typu.|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|Aplikuje zásady odrazu na vytvořenou obecnou metodu, která patří k tomuto typu.|  
|[\<Property>](property-element-net-native.md)|Aplikuje zásadu odrazu na vlastnost patřící tomuto typu.|  
|[\<Type>](type-element-net-native.md)|Aplikuje zásadu odrazu na vnořený typ.|  
|`<TypeInstantiation>`|Aplikuje zásadu odrazu na vnořený konstruovaný obecný typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu.|  
|[\<Assembly>](assembly-element-net-native.md)|Aplikuje zásady odrazu na všechny typy v zadaném sestavení.|  
|[\<Library>](library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typů, jejichž metadata jsou k dispozici pro reflexi v době běhu.|  
|[\<Namespace>](namespace-element-net-native.md)|Aplikuje zásady odrazu na všechny typy v oboru názvů.|  
|[\<Type>](type-element-net-native.md)|Aplikuje zásadu odrazu na typ a všechny jeho členy.|  
|`<TypeInstantiation>`|Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Atributy reflexe, serializace a interoperability jsou volitelné. Musí se ale vyskytovat aspoň jeden.  
  
 Pokud `<TypeInstantiation>` je prvek podřízený prvku [\<Assembly>](assembly-element-net-native.md) , [\<Namespace>](namespace-element-net-native.md) , nebo [\<Type>](type-element-net-native.md) , přepíše nastavení zásad definované nadřazeným prvkem. Pokud [\<Type>](type-element-net-native.md) prvek definuje odpovídající definici obecného typu, `<TypeInstantiation>` prvek přepíše zásady reflexe za běhu pouze pro vytvoření instancí zadaného konstruovaného obecného typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá reflexi k načtení definice obecného typu z vytvořeného <xref:System.Collections.Generic.Dictionary%602> objektu. Také používá reflexi k zobrazení informací o <xref:System.Type> objektech, které reprezentují konstruované obecné typy a definice obecného typu. Proměnná `b` v příkladu je <xref:Windows.UI.Xaml.Controls.TextBlock> ovládací prvek.  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 Po kompilaci s řetězem nástrojů .NET Native vyvolá příklad výjimku [MissingMetadataException](missingmetadataexception-class-net-native.md) na řádku, který volá <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> metodu. Můžete eliminovat výjimku a poskytnout potřebná metadata přidáním následujícího `<TypeInstantiation>` elementu do souboru direktiv modulu runtime:  
  
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

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
