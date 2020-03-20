---
title: <AttributeImplies>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 2ab1fdc71bc43f61f69a0d9b7bea7acb35e14ea5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181061"
---
# <a name="attributeimplies-element-net-native"></a>\<AttributeImplikuje> element (nativní.NET)
Definuje zásadu pro prvky kódu, na které je použit obsažený atribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<AttributeImplies Activate="policy_type"  
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
 Prvek `<AttributeImplies>` se používá, pokud jeho obsahující typ je atribut (to <xref:System.Attribute?displayProperty=nameWithType>znamená, že třída odvozená od ). Pokud je atribut použit pro určitý prvek programu, `<AttributeImplies>` zásada definovaná tímto prvkem se vztahuje na tento prvek programu.  
  
 Reflexe, serializace a interop atributy jsou volitelné, i když alespoň jeden by měl být přítomen.  
  
## <a name="see-also"></a>Viz také

- [\<Typ> element](type-element-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
