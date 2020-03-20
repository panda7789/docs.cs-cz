---
title: <Subtypes>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: bb719449f3769c5dbbde6d05efdb865c18bb4ab2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180939"
---
# <a name="subtypes-element-net-native"></a>\<Podtypy> Element (nativní.NET)
Aplikuje zásady runtime na všechny třídy zděděné z obsahujícího typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Subtypes Activate="policy_type"  
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
  
## <a name="all-attributes"></a>Všechny atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad. Možné hodnoty `All` `Auto`jsou `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , a . Další informace naleznete v tématu [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<Typ>](type-element-net-native.md)|Použije zásady reflexe na typ a všechny jeho členy.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `<Subtypes>` platí zásady pro všechny podtypy jeho obsahující typ. Můžete použít, pokud chcete použít různé zásady odvozené typy a jejich základní třídy.  
  
 Reflexe, serializace a interop atributy jsou volitelné, i když alespoň jeden by měl být přítomen.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje třídu `BaseClass` s názvem `Derived1`a podtřídu s názvem .  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 Jak je znázorněno v následujícím kódu, soubor `Dynamic` direktiv runtime explicitně nastaví zásady a `Activate` pro `BaseClass` . `Excluded` Z tohoto důvodu objekty typu `BaseClass` nelze vytvořit instance dynamicky `BaseClass` nebo volání konstruktoru třídy. `<Subtypes>` Prvek však umožňuje třídy `BaseClass` odvozené z dynamicky a prostřednictvím volání jejich konstruktory třídy.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 Z důvodu `<Subtypes>` směrnice následující kód, který instanci `Derived1` instance dynamicky voláním <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> metody provede úspěšně.  Proměnná bloku je <xref:System.Windows.Controls.TextBlock> objekt v prázdné aplikaci pro Windows Store.  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a>Viz také

- [\<Typ> element](type-element-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
