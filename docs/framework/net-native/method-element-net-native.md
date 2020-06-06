---
title: <Method>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180990"
---
# <a name="method-element-net-native"></a>\<Method>– Element (.NET Native)
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
  
|Atribut|Typ atributu|Description|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název metody.|  
|`Signature`|Obecné|Nepovinný atribut. Určuje signaturu metody. Pokud je přítomno více parametrů, jsou odděleny čárkami. Například následující `<Method>` prvek definuje zásadu pro <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> metodu.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Pokud atribut chybí, platí direktiva modulu runtime pro všechna přetížení metody.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování na informace o nebo výčet metody, ale neumožňuje žádné dynamické vyvolání za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu k konstruktoru nebo metodě pro povolení dynamického programování. Tato zásada zajišťuje, že člen může být v době běhu vyvolán dynamicky.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Hodnota|Description|  
|-----------|-----------------|  
|*method_name*|Název metody. Typ metody je definován nadřazeným [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) prvkem nebo prvkem.|  
  
## <a name="signature-attribute"></a>Atribut podpisu  
  
|Hodnota|Description|  
|-----------|-----------------|  
|*method_signature*|Typy parametrů, které tvoří signaturu metody. Více parametrů je odděleno čárkami, například `"System.String,System.Int32,System.Int32)"` . Názvy typů parametrů by měly být plně kvalifikované.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Description|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít u tohoto typu zásad Možné hodnoty jsou `Auto` , `Excluded` , `Included` a `Required` . Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<Parameter>](parameter-element-net-native.md)|Použije zásady na typ argumentu předaného metodě.|  
|[\<GenericParameter>](genericparameter-element-net-native.md)|Použije zásady na typ parametru obecného typu nebo metody.|  
|[\<ImpliesType>](impliestype-element-net-native.md)|Použije zásady na typ, pokud byly tyto zásady použity na metodu reprezentovanou obsaženým `<Method>` prvkem.|  
|[\<TypeParameter>](typeparameter-element-net-native.md)|Použije zásady na typ představovaný <xref:System.Type> argumentem předaným metodě.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|Aplikuje zásadu odrazu na typ a všechny jeho členy.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 `<Method>`Element obecné metody aplikuje zásady na všechny instance, které nemají vlastní zásady.  
  
 Atribut lze použít `Signature` k určení zásad pro konkrétní přetížení metody. V opačném případě, pokud `Signature` atribut chybí, platí direktiva modulu runtime pro všechna přetížení metody.  
  
 Nemůžete definovat zásady reflexe modulu runtime pro konstruktor pomocí `<Method>` elementu. Místo toho použijte `Activate` atribut [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) prvku,, [\<Type>](type-element-net-native.md) nebo [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
## <a name="example"></a>Příklad  
 `Stringify`Metoda v následujícím příkladu je metoda formátování pro obecné účely, která používá reflexi k převodu objektu na jeho řetězcovou reprezentaci. Kromě volání výchozí `ToString` metody objektu může metoda vytvořit formátovaný výsledný řetězec předáním `ToString` metody objektu formátovacího řetězce, <xref:System.IFormatProvider> implementace nebo obojího. Může také volat jedno z <xref:System.Convert.ToString%2A?displayProperty=nameWithType> přetížení, které převádí číslo na binární, šestnáctkové nebo osmičkové vyjádření.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 `Stringify`Metodu lze volat pomocí kódu podobného následujícímu:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Nicméně při kompilaci s .NET Native může příklad vyvolat počet výjimek za běhu, včetně <xref:System.NullReferenceException> a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) výjimek, k tomu dochází, protože `Stringify` Metoda je určena hlavně pro podporu dynamického formátování primitivních typů v knihovně tříd .NET Framework. Nicméně jejich metadata nejsou k dispozici ve výchozím souboru direktiv. I v případě, že jsou k dispozici jejich metadata, ale příklad vyvolá výjimku [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , protože příslušné `ToString` implementace nebyly zahrnuty do nativního kódu.  
  
 Tyto výjimky lze eliminovat pomocí [\<Type>](type-element-net-native.md) elementu pro definování typů, jejichž metadata musí být přítomna, a přidáním prvků, aby `<Method>` bylo zajištěno, že je také k dispozici implementace přetížení metody, které lze volat dynamicky. Následuje výchozí soubor. Rd. XML, který eliminuje tyto výjimky a umožňuje, aby se tento příklad spustil bez chyby.  
  
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
- [\<MethodInstantiation>Objekt](methodinstantiation-element-net-native.md)
