---
title: <Type>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
ms.openlocfilehash: 4e88b49b82513079ddcf6f0bafe02d44235a406a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73091857"
---
# <a name="type-element-net-native"></a>\<Type>– Element (.NET Native)

Aplikuje zásady modulu runtime na konkrétní typ, jako je třída nebo struktura.

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

|Atribut|Typ atributu|Description|
|---------------|--------------------|-----------------|
|`Name`|Obecné|Požadovaný atribut. Určuje název typu.|
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.|
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.|
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.|
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.|
|`DataContractSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci, která používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídu.|
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci JSON, které používají <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídu.|
|`XmlSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci XML, které používají <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídu.|
|`MarshalObject`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.|
|`MarshalDelegate`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.|
|`MarshalStructure`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů hodnot do nativního kódu.|

## <a name="name-attribute"></a>Atribut Name

|Hodnota|Description|
|-----------|-----------------|
|*type_name*|Název typu. Pokud `<Type>` je tento prvek podřízeným [\<Namespace>](namespace-element-net-native.md) elementem nebo jiným `<Type>` prvkem, *TYPE_NAME* může obsahovat název typu bez jeho oboru názvů. Jinak *TYPE_NAME* musí zahrnovat plně kvalifikovaný název typu.|

## <a name="all-other-attributes"></a>Všechny ostatní atributy

|Hodnota|Description|
|-----------|-----------------|
|*policy_setting*|Nastavení, které se má použít u tohoto typu zásad Možné hodnoty jsou `All` , `Auto` , `Excluded` , `Public` , `PublicAndInternal` , `Required Public` , a `Required PublicAndInternal` `Required All` . Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Description|
|-------------|-----------------|
|[\<AttributeImplies>](attributeimplies-element-net-native.md)|Pokud je nadřazeným typem atribut, definuje zásady modulu runtime pro prvky kódu, na které je atribut použit.|
|[\<Event>](event-element-net-native.md)|Aplikuje zásadu odrazu na událost, která patří k tomuto typu.|
|[\<Field>](field-element-net-native.md)|Aplikuje zásadu odrazu na pole patřící do tohoto typu.|
|[\<GenericParameter>](genericparameter-element-net-native.md)|Použije zásady na typ parametru obecného typu.|
|[\<ImpliesType>](impliestype-element-net-native.md)|Použije zásady na typ, pokud byly tyto zásady použity na typ reprezentovaný nadřazeným `<Type>` prvkem.|
|[\<Method>](method-element-net-native.md)|Aplikuje zásadu odrazu na metodu, která patří tomuto typu.|
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|Aplikuje zásady odrazu na vytvořenou obecnou metodu, která patří k tomuto typu.|
|[\<Property>](property-element-net-native.md)|Aplikuje zásadu odrazu na vlastnost patřící tomuto typu.|
|[\<Subtypes>](subtypes-element-net-native.md)|Aplikuje zásady modulu runtime na všechny třídy zděděné z nadřazeného typu.|
|`<Type>`|Aplikuje zásadu odrazu na vnořený typ.|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|[\<Application>](application-element-net-native.md)|Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu.|
|[\<Assembly>](assembly-element-net-native.md)|Aplikuje zásady odrazu na všechny typy v zadaném sestavení.|
|[\<Library>](library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typů, jejichž metadata jsou k dispozici pro reflexi v době běhu.|
|[\<Namespace>](namespace-element-net-native.md)|Aplikuje zásady odrazu na všechny typy v oboru názvů.|
|`<Type>`|Aplikuje zásadu odrazu na typ a všechny jeho členy.|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.|

## <a name="remarks"></a>Poznámky

Atributy reflexe, serializace a interoperability jsou volitelné. Pokud není žádné, `<Type>` element slouží jako kontejner, jehož podřízené typy definují zásady pro jednotlivé členy.

Pokud `<Type>` je prvek podřízený prvku [\<Assembly>](assembly-element-net-native.md) , [\<Namespace>](namespace-element-net-native.md) , `<Type>` nebo [\<TypeInstantiation>](typeinstantiation-element-net-native.md) , přepíše nastavení zásad definované nadřazeným prvkem.

`<Type>`Element obecného typu aplikuje zásady na všechny instance, které nemají vlastní zásady. Zásady konstruovaných obecných typů jsou definovány [\<TypeInstantiation>](typeinstantiation-element-net-native.md) prvkem.

Je-li typ obecný typ, jeho název je upraven symbolem čárky akcent ( \` ) následovaným jeho počtem obecných parametrů. Například `Name` atribut `<Type>` prvku pro <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> třídu se zobrazí jako ``Name="System.Collections.Generic.List`1"`` .

## <a name="example"></a>Příklad

Následující příklad používá reflexi k zobrazení informací o polích, vlastnostech a metodách <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> třídy. Proměnná `b` v příkladu je <xref:Windows.UI.Xaml.Controls.TextBlock> ovládací prvek. Vzhledem k tomu, že příklad jednoduše načte informace o typu, je dostupnost metadat řízena `Browse` nastavením zásad.

 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]

 Vzhledem k tomu, že metadata pro <xref:System.Collections.Generic.List%601> třídu nejsou automaticky obsažena v řetězu nástroje .NET Native, v příkladu se nezobrazí požadované informace o členu v době běhu. Chcete-li poskytnout potřebná metadata, přidejte následující `<Type>` prvek do souboru direktiv modulu runtime. Všimněte si, že vzhledem k tomu, že jsme poskytli nadřazený [<element oboru názvů \> ](namespace-element-net-native.md) , nemusíme v elementu zadat plně kvalifikovaný název typu `<Type>` .

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
 Následující příklad používá reflexi k načtení <xref:System.Reflection.PropertyInfo> objektu, který představuje <xref:System.String.Chars%2A?displayProperty=nameWithType> vlastnost. Pak použije <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metodu k načtení hodnoty sedmého znaku v řetězci a k zobrazení všech znaků v řetězci. Proměnná `b` v příkladu je <xref:Windows.UI.Xaml.Controls.TextBlock> ovládací prvek.

 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]

 Vzhledem k tomu, že metadata pro <xref:System.String> objekt nejsou k dispozici, volání <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody vyvolá <xref:System.NullReferenceException> výjimku za běhu při kompilování s řetězem nástrojů .NET Native. Chcete-li vyloučit výjimku a poskytnout potřebná metadata, přidejte `<Type>` do souboru direktiv modulu runtime následující element:

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
    <Type Name="System.String" Dynamic="Required Public"/> -->
  </Application>
</Directives>
```

## <a name="see-also"></a>Viz také

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
