---
title: <TypeInstantiation>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 375c95a30f4f60bb711e176cb6c2d0c5fd763e2f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049112"
---
# <a name="typeinstantiation-element-net-native"></a>\<Element > TypeInstantiation (.NET Native)
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
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název typu.|  
|`Arguments`|Obecné|Požadovaný atribut. Určuje argumenty obecného typu. Pokud je přítomno více argumentů, jsou odděleny čárkami.|  
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci, která <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> používá třídu.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci JSON, které <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> používají třídu.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci XML, které <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> používají třídu.|  
|`MarshalObject`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování struktur do nativního kódu.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Value|Popis|  
|-----------|-----------------|  
|*type_name*|Název typu. Pokud je `<TypeInstantiation>` tento prvek podřízeným [ \<oborem názvů >](namespace-element-net-native.md) elementu, [ \<typu >](type-element-net-native.md) elementu nebo jiného `<TypeInstantiation>` prvku, *TYPE_NAME* může určit název typu bez jeho oboru názvů. Jinak musí *TYPE_NAME* obsahovat plně kvalifikovaný název typu. Název typu není upravený. Například pro <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> objekt `<TypeInstantiation>` může být element vypadat takto:<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Arguments – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|*type_argument*|Určuje argumenty obecného typu. Pokud je přítomno více argumentů, jsou odděleny čárkami. Každý argument musí obsahovat plně kvalifikovaný název typu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Value|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro konstruovaný obecný typ. Možné hodnoty jsou `All`, `Auto`, `Excluded` ,`PublicAndInternal`,, ,`Required PublicAndInternal`a. `Required Public` `Public` `Required All` Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> Události](event-element-net-native.md)|Aplikuje zásadu odrazu na událost, která patří k tomuto typu.|  
|[\<> Pole](field-element-net-native.md)|Aplikuje zásadu odrazu na pole patřící do tohoto typu.|  
|[\<ImpliesType>](impliestype-element-net-native.md)|Použije zásady na typ, pokud byly tyto zásady použity na typ reprezentovaný nadřazeným `<TypeInstantiation>` prvkem.|  
|[\<Method>](method-element-net-native.md)|Aplikuje zásadu odrazu na metodu, která patří tomuto typu.|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|Aplikuje zásady odrazu na vytvořenou obecnou metodu, která patří k tomuto typu.|  
|[\<> Vlastnosti](property-element-net-native.md)|Aplikuje zásadu odrazu na vlastnost patřící tomuto typu.|  
|[\<Zadejte >](type-element-net-native.md)|Aplikuje zásadu odrazu na vnořený typ.|  
|`<TypeInstantiation>`|Aplikuje zásadu odrazu na vnořený konstruovaný obecný typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> Aplikace](application-element-net-native.md)|Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu.|  
|[\<> Sestavení](assembly-element-net-native.md)|Aplikuje zásady odrazu na všechny typy v zadaném sestavení.|  
|[\<Library>](library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typů, jejichž metadata jsou k dispozici pro reflexi v době běhu.|  
|[\<Namespace>](namespace-element-net-native.md)|Aplikuje zásady odrazu na všechny typy v oboru názvů.|  
|[\<Zadejte >](type-element-net-native.md)|Aplikuje zásadu odrazu na typ a všechny jeho členy.|  
|`<TypeInstantiation>`|Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Atributy reflexe, serializace a interoperability jsou volitelné. Musí se ale vyskytovat aspoň jeden.  
  
 Pokud je [ \<](assembly-element-net-native.md) [ \<](type-element-net-native.md) [ \<](namespace-element-net-native.md)prvek podřízenou položkou sestavení >, oboru názvů > nebo typu >, přepíše nastavení zásad definované nadřazeným elementem. `<TypeInstantiation>` `<TypeInstantiation>` [ Pokudtyp>prvekdefinujeodpovídajícídefiniciobecnéhotypu,elementpřepíšezásadyreflexezaběhupouzeproinstancezadaného\<](type-element-net-native.md) konstruovaného obecného typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá reflexi k načtení definice obecného typu z vytvořeného <xref:System.Collections.Generic.Dictionary%602> objektu. Také používá reflexi k zobrazení informací <xref:System.Type> o objektech, které reprezentují konstruované obecné typy a definice obecného typu. Proměnná `b` v příkladu <xref:Windows.UI.Xaml.Controls.TextBlock> je ovládací prvek.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
