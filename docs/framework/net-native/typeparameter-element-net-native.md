---
title: <TypeParameter> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b03c87c70fa1bfcd331f468d369632f4164300bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110211"
---
# <a name="typeparameter-element-net-native"></a>\<TypeParameter > – Element (.NET Native)
Použije zásady na typ zastoupený argument typu předaný metodě.  
  
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
|`Name`|Obecné|Požadovaný atribut. Název parametru typu <xref:System.Type>. Například pro podpis metody `Type.GetInterfaceMap(Type interfaceType)`, hodnota `Name` atribut je "interfaceType".|  
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
  
|Value|Popis|  
|-----------|-----------------|  
|*parameter_name*|Název parametru typu <xref:System.Type>. Například pro podpis metody `Type.GetInterfaceMap(Type interfaceType)`, hodnota `Name` atribut je "interfaceType".|  
  
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
  
## <a name="remarks"></a>Poznámky  
 `<TypeParameter>` Element je podobný [ \<parametr >](../../../docs/framework/net-native/parameter-element-net-native.md) elementu, s tím rozdílem, že lze použít pouze u parametrů typu <xref:System.Type>. Platí zásady pro jakýkoli typ v době běhu reprezentována argument typu určeného `Name` atribut.  
  
 Serializátor NewtonSoft JSON patří třeba statickou `JsonConvert.DeserializeObject(String value, Type type)` metody. Následující direktivy reflection:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 Zadejte těchto metadat pro typ runtime reprezentována `type` argument by měl být k dispozici pro serializaci. Pokud tyto direktivy modulu runtime platí pro projekt, který obsahuje následující zdrojový kód:  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 direktivy reflection usnadňují metadat `StockQuote` typu, které jsou k dispozici pro serializátor NewtonSoft JSON v době běhu.  
  
## <a name="see-also"></a>Viz také:

- [\<Metoda > – Element](../../../docs/framework/net-native/method-element-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
