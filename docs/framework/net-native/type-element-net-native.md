---
title: Element &lt;Type&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
caps.latest.revision: "33"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 654f3a360038266d246438838c9ad5821b0a50b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttypegt-element-net-native"></a>Element &lt;Type&gt; (.NET Native)
Platí pro konkrétní typ, jako je například třídu nebo strukturu zásady modulu runtime.  
  
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
|`Activate`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.|  
|`MarshalObject`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásady pro zařazování typů hodnot do nativního kódu.|  
  
## <a name="name-attribute"></a>Atribut Name.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*type_name*|Název typu. Pokud `<Type>` element je podřízeným buď [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md) element nebo jiné `<Type>` elementu *type_name* může zahrnovat název typu bez jeho obor názvů. V opačném *type_name* musí obsahovat typ plně kvalifikovaný název.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které chcete použít pro tento typ zásad. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|Je-li obsahující typ atributu, definuje zásady modulu runtime pro elementy kódu, na které se použije atribut.|  
|[\<Událost >](../../../docs/framework/net-native/event-element-net-native.md)|Reflexe zásady se vztahují k události, které patří k tomuto typu.|  
|[\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)|Reflexe zásada se vztahuje na pole, které patří k tomuto typu.|  
|[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|Zásada se vztahuje na typ parametru obecného typu.|  
|[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|Platí zásady pro typu, v případě, že zásada na typ zastoupený obsahující `<Type>` elementu.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Reflexe zásad platí pro metodu patřící do tohoto typu.|  
|[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Reflexe zásada se vztahuje na sestavené obecné metody, které patří k tomuto typu.|  
|[\<Vlastnost >](../../../docs/framework/net-native/property-element-net-native.md)|Reflexe zásad platí pro vlastnosti, které patří k tomuto typu.|  
|[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|Modul runtime zásad platí pro všechny třídy dědí z nadřazeného typu.|  
|`<Type>`|Reflexe zásad platí pro vnořené typy.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Reflexe zásada se vztahuje na vytvořený obecného typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|Slouží jako kontejner pro celou aplikaci typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu.|  
|[\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|Reflexe zásad platí pro všechny typy v zadaném sestavení.|  
|[\<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Reflexe zásad platí pro všechny typy v oboru názvů.|  
|`<Type>`|Reflexe zásada se vztahuje na typ a všechny její členy.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Reflexe zásada se vztahuje na sestavené obecné typy a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Reflexe, serializace a atributů spolupráce jsou nepovinné. Pokud žádný není přítomen `<Type>` element slouží jako kontejner, jehož podřízené typy definovat zásady pro jednotlivé členy.  
  
 Pokud `<Type>` element je podřízeným [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), `<Type>`, nebo [ \< TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element, přepíše nastavení zásad, které jsou definované v nadřazeném prvku.  
  
 A `<Type>` element obecného typu svých zásad platí pro všechny konkretizací, které nemají své vlastní zásady. Je definované zásady sestavené obecné typy [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.  
  
 Pokud je typ obecného typu, jeho název opatřen odděluje symbol čárka (\`) následovaný jeho počet obecné parametry. Například `Name` atribut `<Type>` element pro <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> třídy se zobrazí jako `Name="System.Collections.Generic.List`1"'.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá k zobrazení informací o pole, vlastnosti a metody reflexe <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> třídy. Proměnná `b` v tomto příkladu je [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) ovládacího prvku. Vzhledem k tomu, že v příkladu jednoduše načte informace o typu, dostupnost metadata řídí `Browse` nastavení zásad.  
  
 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]  
  
 Protože metadata pro <xref:System.Collections.Generic.List%601> třída není v automaticky zahrnuty [!INCLUDE[net_native](../../../includes/net-native-md.md)] řetězu nástroj v příkladu se nepodaří zobrazit informace o požadované členské za běhu. Chcete-li zadat potřebná metadata, přidejte následující `<Type>` elementu, který chcete soubor direktivy modulu runtime. Všimněte si, že, protože nabízíme nadřazený [< Namespace\> ](../../../docs/framework/net-native/namespace-element-net-native.md) elementu nemáme k zadání názvu v plně kvalifikovaný typ `<Type>` elementu.  
  
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
 Následující příklad používá reflexe načíst <xref:System.Reflection.PropertyInfo> objekt, který reprezentuje <xref:System.String.Chars%2A?displayProperty=nameWithType> vlastnost. Poté použije <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda k načtení hodnoty sedmého znaku v řetězci a zobrazit všechny znaky v řetězci. Proměnná `b` v tomto příkladu je [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) ovládacího prvku.  
  
 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]  
  
 Protože metadata pro <xref:System.String> objektu není k dispozici, volání <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda vrátí <xref:System.NullReferenceException> výjimka v spustit čas při kompilovat s [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu. Odstranit výjimku a zadejte potřebná metadata, přidejte následující `<Type>` elementu, který chcete soubor direktivy modulu runtime:  
  
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
