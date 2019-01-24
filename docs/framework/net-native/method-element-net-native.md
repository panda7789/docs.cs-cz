---
title: Element &lt;Method&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdfec7ce93dd3954af03f6f4822ac00576a7e043
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562927"
---
# <a name="ltmethodgt-element-net-native"></a>Element &lt;Method&gt; (.NET Native)
Použije zásady reflexe runtime konstruktoru nebo metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název metody.|  
|`Signature`|Obecné|Nepovinný atribut. Určuje podpis metody. Pokud více parametrů jsou k dispozici, jsou odděleny čárkami. Například následující `<Method>` element definuje zásady pro <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> metody.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Pokud atribut chybí, direktivy modulu runtime se vztahuje na všechna přetížení metody.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o nebo vytváření výčtu metody, ale nepovolí všechny dynamické vyvolání za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktoru nebo metody, které chcete povolit dynamické programování. Tato zásada zajistí, že člen může být vyvolána dynamicky za běhu.|  
  
## <a name="name-attribute"></a>Název atributu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název metody. Typ metody je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.|  
  
## <a name="signature-attribute"></a>Atribut podpisu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_signature*|Typy parametrů, které tvoří podpisu metody. Více parametrů jsou odděleny čárkami, například `"System.String,System.Int32,System.Int32)"`. Názvy typů parametrů by měl být úplný.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Toto nastavení platí pro tento typ zásad. Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)|Použije zásady na typ argument předaný metodě.|  
|[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|Použije zásady na typ parametru obecného typu nebo metody.|  
|[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|Použije zásady na typ, pokud tyto zásady se nastavily pro metodu reprezentovanou obsahující `<Method>` elementu.|  
|[\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|Použije zásady na typ zastoupený <xref:System.Type> argument předaný metodě.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Použije zásady reflexe pro typ a všechny její členy.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 A `<Method>` elementu z obecné metody své zásady platí pro všechny instance, nesmí být svými vlastními zásadami.  
  
 Můžete použít `Signature` atribut určení zásad pro konkrétní metody přetížení. Jinak, pokud `Signature` atribut chybí, direktivy modulu runtime se vztahuje na všechna přetížení metody.  
  
 Nejde definovat zásady reflexe modulu runtime pro konstruktor s použitím `<Method>` elementu. Místo toho použijte `Activate` atribut [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md), nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.  
  
## <a name="example"></a>Příklad  
 `Stringify` Metodou v následujícím příkladu je pro obecné účely metody pro formátování, který používá reflexi k převedení objektu na jeho řetězcovou reprezentaci. Kromě volání objektu výchozí `ToString` metody, metoda může vytvořit formátovaný výsledný řetězec předáním objektu `ToString` metoda řetězec formátu <xref:System.IFormatProvider> implementace nebo obojí. Může také volat jeden z <xref:System.Convert.ToString%2A?displayProperty=nameWithType> přetížení, která převede číslo na binární, hexadecimální nebo osmičkové vyjádření.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 `Stringify` Metoda může být volán kód podobný tomuto:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Ale při kompilaci s .NET Native, v příkladu může vyvolat počet výskytů výjimek za běhu, včetně <xref:System.NullReferenceException> a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky, k tomu dochází, `Stringify` je – metoda určené primárně pro podporu dynamicky formátování primitivní typy v knihovně tříd rozhraní .NET Framework. Jejich metadata, ale není k dispozici ve výchozí soubor direktivy. I v případě, že jejich metadat je k dispozici, ale příklad vyvolá [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky protože odpovídající `ToString` implementace nebyly zahrnout nativního kódu.  
  
 Tyto výjimky lze všechny odstranit pomocí [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu k definování typů, jejichž metadata musí být k dispozici a to přidáním `<Method>` prvků, které se ujistěte se, že implementace metody přetížení který lze dynamicky volat je také k dispozici. Následuje default.rd.xml soubor, který eliminuje těchto výjimek a umožňuje v příkladu provádět bez chyb.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />           
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />           
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Viz také:
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [\<MethodInstantiation> Element](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)
