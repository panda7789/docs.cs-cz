---
title: <Parameter>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c9a462e75df535504d0e98c22c34c11ff7af7d8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049349"
---
# <a name="parameter-element-net-native"></a>\<Parametr > element (.NET Native)
Aplikuje zásadu odrazu na typ argumentu předaného metodě.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Název parametru. Například pro signaturu `String.CompareTo(Object value)`metody hodnota `Name` atributu je "value".|  
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci, která <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> používá třídu.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci JSON, které <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> používají třídu.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci XML, které <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> používají třídu.|  
|`MarshalObject`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů odkazů do WinRT a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů hodnot do nativního kódu.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Value|Popis|  
|-----------|-----------------|  
|*parameter_name*|Název parametru metody, na který se zásada aplikuje. Například pro signaturu `String.CompareTo(Object value)`metody hodnota `Name` atributu je "value".|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Value|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít u tohoto typu zásad Možné hodnoty jsou `All`, `Public` `PublicAndInternal`,,, a`Required PublicAndInternal` .`Required All` `Required Public` Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|Aplikuje zásady reflexe za běhu na konstruktor nebo metodu.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek je podřízeným [ \<prvkem metody >](method-element-net-native.md) a slouží k aplikování zásad na konkrétní parametr metody. `<Parameter>` Konkrétní parametr metody je určen podle názvu, nikoli podle typu. Musí být přítomen alespoň jeden atribut, který představuje typ zásady, `Activate` například `Dynamic`nebo.  
  
## <a name="see-also"></a>Viz také:

- [\<Metoda > element](method-element-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
