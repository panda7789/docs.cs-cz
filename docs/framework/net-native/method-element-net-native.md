---
title: <Method> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 7b0e77e6dea29cbd5218ab3f6f992002efd51656
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128340"
---
# <a name="method-element-net-native"></a>Element > metody \<(.NET Native)
Aplikuje zásady reflexe za běhu na konstruktor nebo metodu.  
  
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
|`Signature`|Obecné|Nepovinný atribut. Určuje signaturu metody. Pokud je přítomno více parametrů, jsou odděleny čárkami. Například následující `<Method>` prvek definuje zásadu pro metodu <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29>.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Pokud atribut chybí, platí direktiva modulu runtime pro všechna přetížení metody.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování na informace o nebo výčet metody, ale neumožňuje žádné dynamické vyvolání za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu k konstruktoru nebo metodě pro povolení dynamického programování. Tato zásada zajišťuje, že člen může být v době běhu vyvolán dynamicky.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název metody. Typ metody je definován nadřazeným [\<typem >](type-element-net-native.md) nebo [\<elementu > TypeInstantiation](typeinstantiation-element-net-native.md) .|  
  
## <a name="signature-attribute"></a>Atribut podpisu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_signature*|Typy parametrů, které tvoří signaturu metody. Více parametrů je odděleno čárkami, například `"System.String,System.Int32,System.Int32)"`. Názvy typů parametrů by měly být plně kvalifikované.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít u tohoto typu zásad Možné hodnoty jsou `Auto`, `Excluded`, `Included`a `Required`. Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Parametr \<](parameter-element-net-native.md)|Použije zásady na typ argumentu předaného metodě.|  
|[\<GenericParameter >](genericparameter-element-net-native.md)|Použije zásady na typ parametru obecného typu nebo metody.|  
|[\<ImpliesType >](impliestype-element-net-native.md)|Použije zásady na typ, pokud byly tyto zásady použity pro metodu reprezentovanou obsahující `<Method>` element.|  
|[\<TypeParameter >](typeparameter-element-net-native.md)|Použije zásady na typ reprezentovaný argumentem <xref:System.Type> předaný metodě.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Typ\<](type-element-net-native.md)|Aplikuje zásadu odrazu na typ a všechny jeho členy.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 `<Method>` prvek obecné metody aplikuje zásady na všechny instance, které nemají vlastní zásady.  
  
 Atribut `Signature` lze použít k určení zásad pro konkrétní přetížení metody. V opačném případě, pokud atribut `Signature` chybí, platí direktiva modulu runtime pro všechna přetížení metody.  
  
 Nemůžete definovat zásady reflexe modulu runtime pro konstruktor pomocí elementu `<Method>`. Místo toho použijte atribut `Activate` [\<sestavení >](assembly-element-net-native.md), [\<oboru názvů >](namespace-element-net-native.md), [\<typ >](type-element-net-native.md)nebo [\<TypeInstantiation >](typeinstantiation-element-net-native.md) elementu.  
  
## <a name="example"></a>Příklad  
 Metoda `Stringify` v následujícím příkladu je metoda formátování pro obecné účely, která používá reflexi k převodu objektu na jeho řetězcovou reprezentaci. Kromě volání výchozí `ToString` metody objektu může metoda vytvořit formátovaný výsledný řetězec předáním `ToString` metody formátu řetězce formátu, implementace <xref:System.IFormatProvider> nebo obou. Může také volat jedno z <xref:System.Convert.ToString%2A?displayProperty=nameWithType> přetížení, které převádí číslo na binární, šestnáctkové nebo osmičkové vyjádření.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Metodu `Stringify` lze volat pomocí kódu podobného následujícímu:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Nicméně při kompilaci s .NET Native může příklad vyvolat několik výjimek za běhu, včetně <xref:System.NullReferenceException> a výjimek [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , k tomu dochází, protože metoda `Stringify` je určena hlavně pro podporu. dynamické formátování primitivních typů v knihovně tříd .NET Framework. Nicméně jejich metadata nejsou k dispozici ve výchozím souboru direktiv. I v případě, že jsou k dispozici jejich metadata, ale příklad vyvolá výjimku [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , protože příslušné implementace `ToString` nebyly zahrnuty do nativního kódu.  
  
 Tyto výjimky lze eliminovat pomocí [\<typ >](type-element-net-native.md) elementu k definování typů, jejichž metadata musí být přítomna, a přidáním `<Method>` prvků, aby bylo zajištěno, že implementace přetížení metody, která může být volána dynamicky, je také aktuální. Následuje výchozí soubor. Rd. XML, který eliminuje tyto výjimky a umožňuje, aby se tento příklad spustil bez chyby.  
  
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

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
- [\<element > MethodInstantiation](methodinstantiation-element-net-native.md)
