---
title: Element &lt;Application&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f4e4eebce1779f1b32a74819fea19fb23204b80c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltapplicationgt-element-net-native"></a>Element &lt;Application&gt; (.NET Native)
Slouží jako kontejner pro celou aplikaci typy a členy typu jejichž metadat je k dispozici pro reflexi v době běhu a platí zásady reflexe modulu runtime pro všechny prvky programu v aplikaci.  
  
 \<Direktivy > elementu  
\<Aplikace > elementu (rd.xml)  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Application Activate="policy_setting"  
             Browse="policy_setting"  
             Dynamic="policy_setting"  
             Serialize="policy_setting"  
             DataContractSerializer="policy_setting"  
             DataContractJsonSerializer="policy_setting"  
             XmlSerializer="policy_setting"  
             MarshalObject="policy_setting"  
             MarshalDelegate="policy_setting"  
             MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky. V tabulce podřízené elementy policy odkazuje na druh metadata, která je k dispozici pro elementy určitého programu za běhu.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Activate`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o nebo vytváření výčtu typy, ale neumožňuje žádné dynamické přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.|  
|`DataContractSerializer`|Serializace|Volitelný atribut. Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.|  
|`DataContractJsonSerializer`|Serializace|Volitelný atribut. Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.|  
|`XmlSerializer`|Serializace|Volitelný atribut. Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.|  
|`MarshalObject`|Zprostředkovatel komunikace s objekty|Volitelný atribut. Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace s objekty|Volitelný atribut. Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace s objekty|Volitelný atribut. Ovládací prvky zásady pro zařazování struktur nativního kódu.|  
  
## <a name="all-attributes"></a>Všechny atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení pro tuto zásadu použít typy v aplikaci. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|Zásady platí pro všechny typy v určitém sestavení.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Zásady platí pro všechny typy v konkrétní oboru názvů.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Platí pro konkrétní typ, jako je například třídu nebo strukturu zásad.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Zásada se vztahuje na vytvořený obecného typu. Například [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element může definovat zásady pro `List<String>` typu.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Zásady se vztahují k metodě na konkrétní typ.|  
|[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Zásada se vztahuje na sestavené obecné metody.|  
|[\<Vlastnost >](../../../docs/framework/net-native/property-element-net-native.md)|Platí pro vlastnost na konkrétní typ zásad.|  
|[\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)|Zásada se vztahuje na pole, podle konkrétního typu.|  
|[\<Událost >](../../../docs/framework/net-native/event-element-net-native.md)|Platí pro událost na konkrétní typ zásad.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Direktivy jazyka >](../../../docs/framework/net-native/directives-element-net-native.md)|Kořenový element souboru direktivy modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 [ \<Direktivy >](../../../docs/framework/net-native/directives-element-net-native.md) element může obsahovat nula nebo jedna `<Application>` elementu. Více `<Application>` elementy do jednoho reflexe direktivy souboru nejsou podporovány.  
  
 `<Application>` Element lze v jednom ze dvou způsobů:  
  
-   Jako kontejner pro definování program elementy, jejichž metadat je vyžadována v době běhu. V takovém případě `<Application>` prvek nemusí mít žádné atributy. Při kompilaci, kompilátoru nástrojů pro vyhledávání všech knihoven, včetně rozhraní .NET Framework základní knihovny pro program prvky identifikovaná podřízených elementů `<Application>` elementu. Naopak nástrojů kompilátoru vyhledávat pouze v knihovně, které jsou určené, které [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) element pro program prvky identifikovaná podřízených elementů [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md).  
  
-   Jako element, který nastaví celou aplikaci zásad reflexe, serializace a zprostředkovatel komunikace s objekty. Atributy `<Application>` element definovat zásady celé aplikace, které může být přepsána podřízené elementy definované `<Application>` nebo [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) element.  
  
## <a name="see-also"></a>Viz také  
 [\<Knihovna > elementu](../../../docs/framework/net-native/library-element-net-native.md)  
 [\<Direktivy > elementu](../../../docs/framework/net-native/directives-element-net-native.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Odkaz na soubor konfigurace modulu runtime direktivy (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
