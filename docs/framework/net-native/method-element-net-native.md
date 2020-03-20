---
title: <Method>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180990"
---
# <a name="method-element-net-native"></a>\<Metoda> element (nativní.NET)
Aplikuje zásady odrazu za běhu na konstruktor nebo metodu.  
  
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
|`Signature`|Obecné|Nepovinný atribut. Určuje podpis metody. Pokud jsou k dispozici více parametrů, jsou odděleny čárkami. Například následující `<Method>` prvek definuje zásady <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> pro metodu.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Pokud atribut chybí, direktiva runtime platí pro všechna přetížení metody.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování na informace o metodě nebo výčet metody, ale neumožňuje žádné dynamické vyvolání za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu k konstruktoru nebo metodě, která umožňuje dynamické programování. Tato zásada zajišťuje, že člen může být vyvolán dynamicky za běhu.|  
  
## <a name="name-attribute"></a>Atribut Název  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název metody. Typ metody je definován nadřazeným [ \<typem>](type-element-net-native.md) nebo [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) elementem.|  
  
## <a name="signature-attribute"></a>Atribut podpisu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_signature*|Typy parametrů, které tvoří podpis metody. Více parametrů je odděleno čárkami, `"System.String,System.Int32,System.Int32)"`například . Názvy typů parametrů by měly být plně kvalifikované.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad. Možné hodnoty `Auto` `Excluded`jsou `Included`, `Required`, a . Další informace naleznete v tématu [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>parametrů](parameter-element-net-native.md)|Platí zásadu pro typ argumentu předaný metodě.|  
|[\<GenericParameter>](genericparameter-element-net-native.md)|Použije zásadu pro typ parametru obecného typu nebo metody.|  
|[\<ImplikaceTyp>](impliestype-element-net-native.md)|Platí zásadu pro typ, pokud tato zásada byla použita `<Method>` pro metodu reprezentovanou obsahující prvek.|  
|[\<TypeParameter>](typeparameter-element-net-native.md)|Platí zásadu pro typ <xref:System.Type> reprezentované argumentem předaný metodě.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<Typ>](type-element-net-native.md)|Použije zásady reflexe na typ a všechny jeho členy.|  
|[\<TypRychlé>](typeinstantiation-element-net-native.md)|Použije zásady reflexe na vytvořený obecný typ a všechny jeho členy.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `<Method>` obecné metody použije své zásady pro všechny instance, které nemají své vlastní zásady.  
  
 `Signature` Atribut můžete použít k určení zásady pro přetížení určité metody. V opačném `Signature` případě, pokud atribut chybí, direktiva runtime platí pro všechna přetížení metody.  
  
 Nelze definovat zásady odrazu za běhu pro `<Method>` konstruktor pomocí prvku. Místo toho `Activate` použijte atribut>[ \<elementu Assembly>](assembly-element-net-native.md), [ \<Namespace>](namespace-element-net-native.md), [ \<Type>](type-element-net-native.md)nebo [ \<TypeInstantiation.](typeinstantiation-element-net-native.md)  
  
## <a name="example"></a>Příklad  
 Metoda `Stringify` v následujícím příkladu je metoda obecného formátování, která používá reflexi k převodu objektu na jeho řetězcovou reprezentaci. Kromě volání výchozí `ToString` metody objektu může metoda vytvořit formátovaný výsledný řetězec předáním `ToString` metody objektu <xref:System.IFormatProvider> formátovací řetězec, implementaci nebo obojí. Může také volat jeden <xref:System.Convert.ToString%2A?displayProperty=nameWithType> z přetížení, který převádí číslo na jeho binární, šestnáctkové nebo osmičkové reprezentace.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Metoda `Stringify` může být volána kódem, jako je následující:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Však při kompilaci s .NET Native, v příkladu může vyvolat <xref:System.NullReferenceException> počet výjimek za běhu, včetně a `Stringify` [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) výjimky, K tomu dochází, protože metoda je určena především pro podporu dynamicky formátování primitivní typy v knihovně tříd rozhraní .NET Framework. Jejich metadata však nejsou k dispozici ve výchozím souboru direktiv. I v případě, že jejich metadata je k dispozici, však v `ToString` příkladu vyvolá [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) výjimky, protože příslušné implementace nebyly zahrnuty v nativním kódu.  
  
 Tyto výjimky lze všechny odstranit pomocí [ \<Type>](type-element-net-native.md) prvek definovat typy, jejichž metadata musí být k dispozici, a přidáním `<Method>` prvků k zajištění, že implementace přetížení metody, které lze volat dynamicky je také k dispozici. Následuje soubor default.rd.xml, který tyto výjimky eliminuje a umožňuje provedení příkladu bez chyby.  
  
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
  
## <a name="see-also"></a>Viz také

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
- [\<MethodInstantiation> Element](methodinstantiation-element-net-native.md)
