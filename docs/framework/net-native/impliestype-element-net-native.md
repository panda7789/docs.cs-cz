---
title: <ImpliesType> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 2f0ce1a1587e190627212cba07db298c12f4b30e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128394"
---
# <a name="impliestype-element-net-native"></a>\<element > ImpliesType (.NET Native)
Použije zásady na typ, pokud byly tyto zásady použity na obsahující typ nebo metodu.  
  
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
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci, která používá třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci JSON, které používají třídu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci XML, které používají třídu <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů hodnot do nativního kódu.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*type_name*|Název typu. Pokud je typ reprezentovaný tímto `<ImpliesType>` element umístěn ve stejném oboru názvů jako jeho element obsahující `<Type>`, *TYPE_NAME* může obsahovat název typu bez jeho oboru názvů. Jinak musí *TYPE_NAME* obsahovat plně kvalifikovaný název typu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít u tohoto typu zásad Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Typ\<](type-element-net-native.md)|Aplikuje zásadu odrazu na typ a všechny jeho členy.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.|  
|[Metoda\<](method-element-net-native.md)|Aplikuje zásadu reflexe na metodu.|  
  
## <a name="remarks"></a>Poznámky  
 Element `<ImpliesType>` je primárně určen pro použití v knihovnách. Řeší následující scénář:  
  
- Pokud rutina potřebuje reflektovat na jeden typ, musí být nutně odpovídat druhému typu.  
  
- Metadata pro implicitní instanci druhého typu jsou jinak nedostupná, protože statická analýza neindikuje, že je to nezbytné.  
  
 Nejčastěji jsou tyto dva typy obecné instance s argumenty sdíleného typu.  
  
 `<ImpliesType>` element byl definován s předpokladem, že nutnost reflexe u typu určeného jeho nadřazeným elementem implikuje nutnost reflexe u typu určeného `<ImpliesType>` prvkem. Například následující direktivy reflexe platí pro dva typy `Explicit<T>` a `Implicit<T>`.  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 Tato direktiva nemá žádný vliv, pokud vytvoření instance `Explicit` nemá definované nastavení zásad `Dynamic`. Pokud se například jedná o případ `Explicit<Int32>`, `Implicit<Int32>` se vytvoří instance se svými veřejnými členy rooted a jejich metadata jsou k dispozici pro dynamické programování.  
  
 Následuje příklad reálného světa, který se vztahuje alespoň na jeden serializátor. Direktivy zachytí požadavek, který se odráží na něco, co je `IList<`*něco*`>` zahrnuje také reflektování na odpovídající *`List<`typ*`>`, aniž by to vyžadovalo jednotlivé aplikace. poznámky.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 Element `<ImpliesType>` se může také zobrazit v elementu `<Method>`, protože v některých případech instance obecné metody implikuje odrážející typ instance. Představte si například obecnou metodu `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)`, že daná knihovna bude dynamicky přistupovat společně s přidruženými <xref:System.Collections.Generic.List%601> a <xref:System.Array> typy. Tato možnost může být vyjádřena takto:  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
