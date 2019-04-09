---
title: <ImpliesType> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ef238a2cb852ecd7fa3f0e2dbe4048ff03a4139
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080875"
---
# <a name="impliestype-element-net-native"></a>\<ImpliesType > – Element (.NET Native)
Použije zásady na typ, pokud tyto zásady se nastavily pro nadřazený typ nebo metoda.  
  
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
|`Activate`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory Povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky, zadávání dotazů na informace o prvcích program, ale neumožňuje přístup modulu runtime.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.|  
|`MarshalObject`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásad pro zařazování odkazové typy Windows Runtime a modelu COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Určuje zásady pro zařazování typů hodnot do nativního kódu.|  
  
## <a name="name-attribute"></a>Název atributu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*type_name*|Název typu. Pokud typ reprezentovaný tímto objektem `<ImpliesType>` prvek nachází v oboru názvů stejný jako jeho obsahující `<Type>` elementu *type_name* může obsahovat název typu bez svůj obor názvů. V opačném případě *type_name* musí obsahovat plně kvalifikovaného názvu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Toto nastavení platí pro tento typ zásad. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Použije zásady reflexe pro typ a všechny její členy.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Použije zásady reflexe pro metodu.|  
  
## <a name="remarks"></a>Poznámky  
 `<ImpliesType>` Element je primárně určena pro použití knihovny. To řeší následující scénář:  
  
-   Pokud rutiny potřebuje tak, aby odrážely na jeden typ, nutně musí tak, aby odrážely u druhého typu.  
  
-   Metadata pro implicitní vytvoření instance typu druhý není k dispozici, jinak, protože statické analýzy neukazuje, že je nutné.  
  
 Nejčastěji jsou tyto dva typy obecných instancí s argumenty sdíleného typu.  
  
 `<ImpliesType>` Byl definován prvek za předpokladu, že potřebujete reflexe na typu určeného jeho nadřazený element znamená potřebu reflexe na typ určený `<ImpliesType>` elementu. Například následující direktivy reflection platí i pro dva typy `Explicit<T>` a `Implicit<T>`.  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 Tato direktiva nemá žádný vliv, pokud instance `Explicit` má definované `Dynamic` nastavení zásad. Například, pokud je to tento případ pro `Explicit<Int32>`, `Implicit<Int32>` je vytvořena instance s jeho veřejné členy root, a jejich metadat je přístupné pro dynamické programování.  
  
 Následuje příklad reálného světa, který platí pro jeden serializátor. Direktivy zaznamenání požadavku, že něco reflexi typu `IList<` *něco* `>` zahrnuje také reflexi u odpovídajícího `List<` *něco* `>` typ nevyžaduje žádnou poznámku jednotlivých aplikací.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 `<ImpliesType>` Element se může zobrazit i v rámci `<Method>` element, protože v některých případech vytváření instancí obecné metody zahrnuje vytvoření instance typu reflexi. Představte si například obecné metody `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` , který danou knihovnu bude mít přístup k dynamicky spolu s přidruženou <xref:System.Collections.Generic.List%601> a <xref:System.Array> typy. Tento rozdíl lze vyjádřit jako:  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
