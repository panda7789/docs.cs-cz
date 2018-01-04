---
title: Element &lt;Method&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 74aa7a683c8cf4c5ec61dc48ead3ed0f5a780cd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltmethodgt-element-net-native"></a>Element &lt;Method&gt; (.NET Native)
Platí zásady reflexe modulu runtime pro konstruktor nebo metoda.  
  
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
|`Signature`|Obecné|Nepovinný atribut. Určuje podpis metody. Pokud jsou v něm několik parametrů, jsou oddělené čárkami. Například následující `<Method>` element definuje zásady pro <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> metoda.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Pokud chybí atribut, direktivy modulu runtime platí pro všechny přetížení metody.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o nebo vytváření výčtu metodu, ale neumožňuje žádné dynamické volání za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktor nebo způsob povolení dynamické programování. Tato zásada zajistí, že člena nelze vyvolat dynamicky za běhu.|  
  
## <a name="name-attribute"></a>Atribut Name.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název metody. Typ metody je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.|  
  
## <a name="signature-attribute"></a>Atribut podpisu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_signature*|Typy parametrů, které vytvářejí podpis metody. Několik parametrů jsou oddělené čárkami, například `"System.String,System.Int32,System.Int32)"`. Typ názvy parametrů by měl být úplný.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které chcete použít pro tento typ zásad. Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)|Zásada se vztahuje na typ argument předaný metodě.|  
|[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|Zásada se vztahuje na typ parametru obecný typ nebo metoda.|  
|[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|Platí zásady pro typu, v případě, že zásada pro metodu reprezentovanou obsahující `<Method>` elementu.|  
|[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|Zásada se vztahuje na typ zastoupený <xref:System.Type> argument předaný metodě.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Reflexe zásada se vztahuje na typ a všechny její členy.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Reflexe zásada se vztahuje na sestavené obecné typy a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 A `<Method>` element obecná metoda svých zásad platí pro všechny konkretizací, které nemají své vlastní zásady.  
  
 Můžete použít `Signature` atribut určení zásad pro konkrétní metody přetížení. Jinak, pokud `Signature` chybí atribut, direktivy modulu runtime platí pro všechny přetížení metody.  
  
 Nelze definovat zásady reflexe modulu runtime pro konstruktor pomocí `<Method>` elementu. Místo toho použijte `Activate` atribut [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md), nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.  
  
## <a name="example"></a>Příklad  
 `Stringify` Metoda v následujícím příkladu je pro obecné účely formátování metoda, která používá reflexe převést řetězcovou reprezentaci objektu. Kromě volání objektu výchozí `ToString` metody metodu můžete vytvořit řetězec formátovaný výsledek předáním objektu `ToString` metoda řetězec formátu <xref:System.IFormatProvider> implementace, nebo obojí. Také jeden z může zavolat <xref:System.Convert.ToString%2A?displayProperty=nameWithType> přetížení, která převádí číslo na jeho binární, šestnáctkové nebo osmičková reprezentace.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 `Stringify` Nelze volat metodu kódem takto:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Ale když kompilujete s .NET Native, v příkladu můžete vyvolat představuje počet výjimek za běhu, včetně <xref:System.NullReferenceException> a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky, k tomu dochází proto `Stringify` je – metoda určená hlavně pro podporu dynamicky formátování primitivní typy v knihovně tříd rozhraní .NET Framework. Jejich metadat však není k dispozici ve výchozí soubor direktivy. I když jejich metadata jsou k dispozici, ale v příkladu vyvolá [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky protože odpovídající `ToString` implementace nebyly byla obsahovat v nativním kódu.  
  
 Tyto výjimky všechny jdou vyloučit pomocí [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu k definování typů, jejichž metadata musí být k dispozici a přidáním `<Method>` elementy zajistit, aby implementace přetížení metody které lze volat dynamicky se nachází. Zde je default.rd.xml soubor, který eliminuje tyto výjimky a umožňuje v příkladu provést bez chyby.  
  
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
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [\<MethodInstantiation > elementu](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)
