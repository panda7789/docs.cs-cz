---
title: Element &lt;GenericParameter&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 601118d2dcc42f9e35da0e24c782b218efd7a025
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltgenericparametergt-element-net-native"></a>Element &lt;GenericParameter&gt; (.NET Native)
Zásada se vztahuje na typ parametru obecný typ nebo metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type" />  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Název obecný parametr. Například pro obecný delegát <xref:System.Func%603>, hodnota `Name` atribut je "TResult" pro použití zásad runtime delegáta návratovou hodnotu.|  
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
|*generic_parameter_name*|Požadovaný atribut. Název parametru obecného typu. Například pro obecný delegát <xref:System.Func%603>, *generic_parameter_name* hodnotu "TResult" platí zásady modulu runtime pro delegáta návratovou hodnotu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které chcete použít pro tento typ zásad. Možné hodnoty jsou `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Platí zásady reflexe modulu runtime pro konstruktor nebo metoda.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Platí pro konkrétní typ, jako je například třídu nebo strukturu zásady reflexe modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 `<GenericParameter>` Prvek je podřízeným buď [ \<metoda >](../../../docs/framework/net-native/method-element-net-native.md) nebo [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) element a se používá k aplikování zásad na konkrétní obecného typu parametr, který je zadat jeho název v obecný typ nebo metoda podpis.  
  
 `<GenericParameter>` Element je velmi užitečné při použití s serializátorů. Následující příklad používá `<GenericParameter>` elementu, který chcete použít pro typ zásady `T` ve voláních serializátor NewtonSoft JSON [JsonConvert.DeserializeObject\<T > (String)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm) přetížení metody.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a>Viz také  
 [\<Metoda > elementu](../../../docs/framework/net-native/method-element-net-native.md)  
 [\<Typ > elementu](../../../docs/framework/net-native/type-element-net-native.md)  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
