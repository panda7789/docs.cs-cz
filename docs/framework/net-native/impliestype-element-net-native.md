---
title: <ImpliesType>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 57f4208233cd5e8544b4f1c254e3b0e0eaacd508
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181007"
---
# <a name="impliestype-element-net-native"></a>\<ImplikaceTyp> element (nativní.NET)
Platí zásady pro typ, pokud tato zásada byla použita pro obsahující typ nebo metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<ImpliesType Name="type_name"  
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
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, aby bylo možné aktivovat instance.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování na informace o prvcích programu, ale neumožňuje žádný přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, aby bylo možné povolit dynamické programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby instance typu mohly být serializovány a deserializovány knihovnami, jako je například serializátor Newtonsoft JSON.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Řídí zásady serializace, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> která používá třídu.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci JSON, který používá třídu. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Řídí zásady serializace XML, která používá třídu. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>|  
|`MarshalObject`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů odkazů na prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkce do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů hodnot do nativního kódu.|  
  
## <a name="name-attribute"></a>Atribut Název  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*Type_name*|Název typu. Pokud je typ `<ImpliesType>` reprezentované tímto prvkem umístěn `<Type>` ve stejném oboru názvů jako jeho obsahující prvek, *type_name* může obsahovat název typu bez jeho oboru názvů. V opačném případě *musí type_name* obsahovat plně kvalifikovaný název typu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad. Možné hodnoty `All` `Auto`jsou `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , a . Další informace naleznete v tématu [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<Typ>](type-element-net-native.md)|Použije zásady reflexe na typ a všechny jeho členy.|  
|[\<TypRychlé>](typeinstantiation-element-net-native.md)|Použije zásady reflexe na vytvořený obecný typ a všechny jeho členy.|  
|[\<>metody](method-element-net-native.md)|Použije zásady reflexe na metodu.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `<ImpliesType>` je primárně určen pro použití v knihovnách. Řeší následující scénář:  
  
- Pokud rutina potřebuje přemýšlet o jednom typu, musí nutně odrážet na druhý typ.  
  
- Metadata pro implikované konkretizace druhého typu je jinak nedostupná, protože statická analýza neznamená, že je to nezbytné.  
  
 Nejčastěji dva typy jsou obecné instance s argumenty sdíleného typu.  
  
 Prvek `<ImpliesType>` byl definován s předpokladem, že potřeba reflexe na typ určený jeho nadřazený prvek znamená potřebu reflexe na typ určený elementem. `<ImpliesType>` Například následující direktivy reflexe `Explicit<T>` `Implicit<T>`platí pro dva typy a .  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 Tato směrnice nemá žádný účinek, `Explicit` pokud `Dynamic` konstanční má definované nastavení zásad. Například pokud tomu tak je `Explicit<Int32>` `Implicit<Int32>` pro , je vytvořena instance s jeho veřejné členy zakořeněné a jejich metadata je přístupná pro dynamické programování.  
  
 Následuje příklad reálného světa, který platí pro alespoň jeden serializátor. Direktivy zachycují požadavek, že `IList<`reflexe na něco zadali jako *něco* `>` také zahrnuje reflexi na odpovídající `List<` *něco* `>` typu bez nutnosti jakékoli poznámky pro aplikaci.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 Prvek `<ImpliesType>` může také zobrazit `<Method>` v rámci prvku, protože v některých případech vytváření instancí obecné metody znamená reflexi na typ instanování. Představte si například `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` obecnou metodu, ke které bude <xref:System.Collections.Generic.List%601> <xref:System.Array> daná knihovna dynamicky přistupovat spolu s přidruženými a typy. To lze vyjádřit takto:  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a>Viz také

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
