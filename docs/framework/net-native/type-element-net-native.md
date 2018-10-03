---
title: Element &lt;Type&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaf5103dfee366466ff701ce3669bbabb97233ac
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48037466"
---
# <a name="lttypegt-element-net-native"></a>Element &lt;Type&gt; (.NET Native)
Použije zásady modulu runtime určitého typu, jako je například třídy nebo struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Type Name="type_name"  
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
|`Activate`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory Povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky, zadávání dotazů na informace o prvcích program, ale neumožňuje přístup modulu runtime.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.|  
|`MarshalObject`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásad pro zařazování odkazové typy Windows Runtime a modelu COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Určuje zásady pro zařazování typů hodnot do nativního kódu.|  
  
## <a name="name-attribute"></a>Název atributu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*type_name*|Název typu. Pokud tento `<Type>` element je podřízeným buď [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md) element nebo jiného `<Type>` elementu *type_name* může obsahovat název typu bez jeho obor názvů. V opačném případě *type_name* musí obsahovat plně kvalifikovaného názvu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Toto nastavení platí pro tento typ zásad. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|Pokud je obsahující typ atributu, definuje zásady modulu runtime pro prvky kódu, ke kterým se atribut používá.|  
|[\<Událost >](../../../docs/framework/net-native/event-element-net-native.md)|Použije zásady reflexe pro událost, které patří k tomuto typu.|  
|[\<pole >](../../../docs/framework/net-native/field-element-net-native.md)|Použije zásady reflexe pro pole, které patří k tomuto typu.|  
|[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|Použije zásady na typ parametru obecného typu.|  
|[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|Použije zásady na typ, pokud byl použit tyto zásady na typ zastoupený obsahující `<Type>` elementu.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Použije zásady reflexe pro metody, které patří k tomuto typu.|  
|[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Použije zásady reflexe konstruované obecné metody, které patří k tomuto typu.|  
|[\<Vlastnost >](../../../docs/framework/net-native/property-element-net-native.md)|Použije zásady reflexe pro vlastnosti, které patří k tomuto typu.|  
|[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|Zásady modulu runtime se vztahuje na všechny třídy dědí z nadřazeného typu.|  
|`<Type>`|Použije zásady reflexe vnořeného typu.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Použije zásady reflexe pro Konstruovaný obecný typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|Slouží jako kontejner pro celou aplikaci typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe v době běhu.|  
|[\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|Použije zásady reflexe pro všechny typy v zadané sestavení.|  
|[\<Knihovny >](../../../docs/framework/net-native/library-element-net-native.md)|Určuje sestavení, který obsahuje typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe v době běhu.|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Použije zásady reflexe pro všechny typy v oboru názvů.|  
|`<Type>`|Použije zásady reflexe pro typ a všechny její členy.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Reflexe, serializace a atributů spolupráce jsou nepovinné. Pokud nejsou k dispozici, `<Type>` prvek slouží jako kontejner, jehož podřízené typy definovat zásady pro jednotlivé členy.  
  
 Pokud `<Type>` element je podřízeným [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), `<Type>`, nebo [ \< TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu, přepíše nastavení zásad, které jsou definované v nadřazeném prvku.  
  
 A `<Type>` element obecného typu své zásady platí pro všechny instance, nesmí být svými vlastními zásadami. Je definována zásada sestavené obecné typy [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.  
  
 Pokud je typ obecný typ, jeho název je upravený symbol čárka (\`) následovaný jeho počet obecných parametrů. Například `Name` atribut `<Type>` – element pro <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> třída se objeví jako `Name="System.Collections.Generic.List`1"".  
  
## <a name="example"></a>Příklad  
 Následující příklad používá reflexi k zobrazení informací o pole, vlastnosti a metody <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> třídy. Proměnná `b` v tomto příkladu je [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) ovládacího prvku. Protože příklad jednoduše načte informace o typu, se řídí dostupnost metadat `Browse` nastavení zásad.  
  
 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]  
  
 Protože metadata pro <xref:System.Collections.Generic.List%601> třída není součástí automaticky [!INCLUDE[net_native](../../../includes/net-native-md.md)] řetězce nástrojů příkladu dojde k chybě zobrazíte informace o požadované členské v době běhu. Chcete-li zadat potřebná metadata, přidejte následující `<Type>` element do souboru direktiv modulu runtime. Všimněte si, že vzhledem k tomu, že poskytujeme nadřazený [< Namespace\> ](../../../docs/framework/net-native/namespace-element-net-native.md) elementu, nemusíme poskytovat plně kvalifikovaného názvu v `<Type>` elementu.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="*Application*" Dynamic="Required All" />  
      <Namespace Name ="System.Collections.Generic" >  
        <Type Name="List`1" Browse="Required All" />   
     </Namespace>  
   </Application>  
</Directives>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad používá reflexi k načtení <xref:System.Reflection.PropertyInfo> objekt, který reprezentuje <xref:System.String.Chars%2A?displayProperty=nameWithType> vlastnost. Poté použije <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody k načtení hodnoty sedmého znaku v řetězci a chcete-li zobrazit všechny znaky v řetězci. Proměnná `b` v tomto příkladu je [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) ovládacího prvku.  
  
 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]  
  
 Protože metadata pro <xref:System.String> objektu není k dispozici, volání <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> vyvolá metoda výjimku <xref:System.NullReferenceException> výjimka za běhu čas při kompilaci s [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězce. Chcete-li eliminovat výjimku a poskytněte metadata, která nezbytné, přidejte následující `<Type>` element do souboru direktiv modulu runtime:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
    <Type Name="System.String" Dynamic="Required Public"/> -->  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Viz také  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
