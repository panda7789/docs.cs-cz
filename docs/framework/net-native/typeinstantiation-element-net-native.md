---
title: Element &lt;TypeInstantiation&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5dc19038af220cca63417a331a37d4a7d3b9f96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttypeinstantiationgt-element-net-native"></a>Element &lt;TypeInstantiation&gt; (.NET Native)
Platí zásady reflexe modulu runtime pro vytvořený obecného typu.  
  
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
|`Arguments`|Obecné|Požadovaný atribut. Určuje argumenty obecného typu. Pokud jsou v něm více argumentů, jsou oddělené čárkami.|  
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
|*type_name*|Název typu. Pokud `<TypeInstantiation>` element je podřízeným [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md) elementu [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) element nebo jiné `<TypeInstantiation>` elementu *type_ název* můžete zadat název typu bez jeho obor názvů. V opačném *type_name* musí obsahovat typ plně kvalifikovaný název. Název typu není dekorované. Například <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> objekt, `<TypeInstantiation>` element může vypadat takto:<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Argumenty atributu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*type_argument*|Určuje argumenty obecného typu. Pokud jsou v něm více argumentů, jsou oddělené čárkami. Každý argument musí obsahovat plně kvalifikovaného názvu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které chcete použít pro tento typ zásad pro vytvořený obecného typu. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Událost >](../../../docs/framework/net-native/event-element-net-native.md)|Reflexe zásady se vztahují k události, které patří k tomuto typu.|  
|[\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)|Reflexe zásada se vztahuje na pole, které patří k tomuto typu.|  
|[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|Platí zásady pro typu, v případě, že zásada na typ zastoupený obsahující `<TypeInstantiation>` elementu.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Reflexe zásad platí pro metodu patřící do tohoto typu.|  
|[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Reflexe zásada se vztahuje na sestavené obecné metody, které patří k tomuto typu.|  
|[\<Vlastnost >](../../../docs/framework/net-native/property-element-net-native.md)|Reflexe zásad platí pro vlastnosti, které patří k tomuto typu.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Reflexe zásad platí pro vnořené typy.|  
|`<TypeInstantiation>`|Reflexe zásad platí pro vnořené sestavené obecného typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|Slouží jako kontejner pro celou aplikaci typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu.|  
|[\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|Reflexe zásad platí pro všechny typy v zadaném sestavení.|  
|[\<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Reflexe zásad platí pro všechny typy v oboru názvů.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Reflexe zásada se vztahuje na typ a všechny její členy.|  
|`<TypeInstantiation>`|Reflexe zásada se vztahuje na sestavené obecné typy a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Reflexe, serializace a atributů spolupráce jsou nepovinné. Alespoň jeden však musí být přítomen.  
  
 Pokud `<TypeInstantiation>` element je podřízeným [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), nebo [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md), elementu přepíše nastavení zásad, které jsou definované v nadřazeném prvku. Pokud [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) element definuje odpovídající definice obecného typu, `<TypeInstantiation>` element přednost před zásadami reflexe runtime pouze u instancí možnosti zadaný sestavené obecného typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá reflexe načíst definici obecného typu z vytvořený <xref:System.Collections.Generic.Dictionary%602> objektu. Reflexe také používá k zobrazení informací o <xref:System.Type> objekty, které představují sestavené obecné typy a definice obecného typu. Proměnná `b` v tomto příkladu je [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) ovládacího prvku.  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 Po sestavení s [!INCLUDE[net_native](../../../includes/net-native-md.md)] vyvolá nástroj řetězu příklad [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimky na řádek, který volá <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> metoda. Můžete eliminovat výjimku a poskytnout nezbytné metadata přidáním následující `<TypeInstantiation>` elementu, který chcete soubor direktivy modulu runtime:  
  
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
