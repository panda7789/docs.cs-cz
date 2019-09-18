---
title: <ImpliesType>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10fa3a0ac04038bb686311a4d86c99442c0fcf26
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049666"
---
# <a name="impliestype-element-net-native"></a>\<Element > ImpliesType (.NET Native)
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
|`DataContractSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci, která <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> používá třídu.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci JSON, které <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> používají třídu.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci XML, které <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> používají třídu.|  
|`MarshalObject`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů hodnot do nativního kódu.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Value|Popis|  
|-----------|-----------------|  
|*type_name*|Název typu. Pokud je typ reprezentovaný tímto `<ImpliesType>` prvkem umístěný ve stejném oboru názvů jako element, který `<Type>` obsahuje, *TYPE_NAME* může obsahovat název typu bez jeho oboru názvů. Jinak musí *TYPE_NAME* obsahovat plně kvalifikovaný název typu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Value|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít u tohoto typu zásad Možné hodnoty jsou `All`, `Auto`, `Excluded` ,`PublicAndInternal`,, ,`Required PublicAndInternal`a. `Required Public` `Public` `Required All` Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Zadejte >](type-element-net-native.md)|Aplikuje zásadu odrazu na typ a všechny jeho členy.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.|  
|[\<Method>](method-element-net-native.md)|Aplikuje zásadu reflexe na metodu.|  
  
## <a name="remarks"></a>Poznámky  
 `<ImpliesType>` Element je primárně určen pro použití v knihovnách. Řeší následující scénář:  
  
- Pokud rutina potřebuje reflektovat na jeden typ, musí být nutně odpovídat druhému typu.  
  
- Metadata pro implicitní instanci druhého typu jsou jinak nedostupná, protože statická analýza neindikuje, že je to nezbytné.  
  
 Nejčastěji jsou tyto dva typy obecné instance s argumenty sdíleného typu.  
  
 Element byl definován s předpokladem, že nutnost reflexe u typu určeného jeho nadřazeným elementem implikuje nutnost reflexe u typu určeného `<ImpliesType>` elementem. `<ImpliesType>` Například následující direktivy reflexe platí pro dva typy, `Explicit<T>` a `Implicit<T>`.  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 Tato direktiva nemá žádný vliv, pokud vytvoření instance `Explicit` má definované `Dynamic` nastavení zásad. Například pokud se jedná o případ `Explicit<Int32>`, `Implicit<Int32>` je vytvořena instance s jeho veřejnými členy rootd a jejich metadata jsou k dispozici pro dynamické programování.  
  
 Následuje příklad reálného světa, který se vztahuje alespoň na jeden serializátor. Direktivy zachytí požadavek, který reflektuje na něco napsaného `IList<`jako *něco* `>` zahrnuje také reflektování `List<`na odpovídající typ *něčeho* `>` , aniž by to vyžadovalo. Anotace jednotlivých aplikací.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 Element se může také objevit `<Method>` v rámci elementu, protože v některých případech instance obecné metody implikuje odrážející typ instance. `<ImpliesType>` Představte si například obecnou `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` metodu, kterou bude mít daná knihovna k dynamickému přístupu <xref:System.Collections.Generic.List%601> společně <xref:System.Array> s přidruženými typy a. Tato možnost může být vyjádřena takto:  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
