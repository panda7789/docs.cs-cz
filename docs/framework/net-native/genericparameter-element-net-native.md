---
title: <GenericParameter> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40fef845a55412e5731ec08bd1e038d6b311694c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111654"
---
# <a name="genericparameter-element-net-native"></a>\<GenericParameter > – Element (.NET Native)
Použije zásady na typ parametru obecného typu nebo metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"  
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
|`Name`|Obecné|Požadovaný atribut. Název obecného parametru. Například pro obecný delegát <xref:System.Func%603>, hodnota `Name` atribut je "TResult" runtime zásadu chcete uplatnit na návratovou hodnotu tohoto delegáta.|  
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
|*generic_parameter_name*|Požadovaný atribut. Název parametru obecného typu. Například pro obecný delegát <xref:System.Func%603>, *generic_parameter_name* hodnotu "TResult" platí zásady modulu runtime pro vrácené hodnoty delegáta.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Value|Popis|  
|-----------|-----------------|  
|*policy_setting*|Toto nastavení platí pro tento typ zásad. Možné hodnoty jsou `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Method>](../../../docs/framework/net-native/method-element-net-native.md)|Použije zásady reflexe runtime konstruktoru nebo metody.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Použije zásady reflexe runtime určitého typu, jako je například třídy nebo struktury.|  
  
## <a name="remarks"></a>Poznámky  
 `<GenericParameter>` Element je podřízeným prvkem buď [ \<metoda >](../../../docs/framework/net-native/method-element-net-native.md) nebo [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu a se používá k aplikování zásad pro konkrétní typ obecný parametr, který je zadat pomocí jejího názvu do obecného typu nebo metodě podpis.  
  
 `<GenericParameter>` Element je nejužitečnější při použití se serializátory. V následujícím příkladu `<GenericParameter>` element uplatňovat zásady na typ `T` ve voláních serializátor NewtonSoft JSON [JsonConvert.DeserializeObject\<T > (řetězec)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) přetížení metody.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a>Viz také:

- [\<Metoda > – Element](../../../docs/framework/net-native/method-element-net-native.md)
- [\<Typ > – Element](../../../docs/framework/net-native/type-element-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
