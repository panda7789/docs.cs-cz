---
title: Element &lt;ImpliesType&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36620e8a8f6cb96b11f951ee5477e6edad9c925a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltimpliestypegt-element-net-native"></a>Element &lt;ImpliesType&gt; (.NET Native)
Platí zásady pro typu, v případě, že zásada obsahující typ nebo metoda.  
  
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
|*type_name*|Název typu. Pokud typ reprezentovaný tímto objektem `<ImpliesType>` prvek nachází v oboru názvů stejné jako jeho obsahující `<Type>` elementu *type_name* může zahrnovat název typu bez jeho obor názvů. V opačném *type_name* musí obsahovat typ plně kvalifikovaný název.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které chcete použít pro tento typ zásad. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Reflexe zásada se vztahuje na typ a všechny její členy.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Reflexe zásada se vztahuje na sestavené obecné typy a všechny její členy.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Reflexe zásada se vztahuje na metodu.|  
  
## <a name="remarks"></a>Poznámky  
 `<ImpliesType>` Element je primárně určený pro použití knihovny. Zaměřuje se na následující scénář:  
  
-   Pokud rutinu, která potřebuje, aby odpovídala v jeden typ, nutně vyžaduje, aby odpovídala v druhého typu.  
  
-   Metadata pro předpokládané instance druhý typ není k dispozici, protože statické analysis není označení, že je nezbytné.  
  
 Existují dva typy nejčastěji, jsou obecné konkretizací s argumenty sdílené typu.  
  
 `<ImpliesType>` Element byla definována za předpokladu, že potřebu reflexe v typu zadaném pomocí svého nadřízeného elementu znamená potřebu reflexe v typu zadaném pomocí `<ImpliesType>` elementu. Například následující direktivy reflexe použít dva typy `Explicit<T>` a `Implicit<T>`.  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 Tato direktiva nemá žádný vliv, pokud vytváření instancí z `Explicit` má definovanou `Dynamic` nastavení zásad. Například, pokud je to tento případ pro `Explicit<Int32>`, `Implicit<Int32>` je vytvořena s jeho veřejné členy root, a jejich metadat je přístupné pro dynamické programování.  
  
 Následuje příklad reálného, který se vztahuje na alespoň jeden serializátor. Direktivy zaznamenat požadavky, které odráží na něco zadán jako `IList<` *něco* `>` také zahrnuje odrážející na odpovídajícím `List<` *něco* `>` typu bez nutnosti jakékoli poznámky jednotlivých aplikací.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 `<ImpliesType>` Element se může zobrazit i v rámci `<Method>` elementu, protože v některých případech vytváření instancí obecná metoda znamená odrážející při vytváření instance typu. Představte si například obecná metoda `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` , danou knihovnu bude přistupovat dynamicky spolu s příslušnými <xref:System.Collections.Generic.List%601> a <xref:System.Array> typy. To může být vyjádřený jako:  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a>Viz také  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
