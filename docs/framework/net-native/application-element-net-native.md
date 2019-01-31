---
title: <Application> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 366878fbfbfbe3e3951095c9ad82c1260638a0cb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270807"
---
# <a name="application-element-net-native"></a>\<Aplikace > – Element (.NET Native)
Slouží jako kontejner pro celou aplikaci typy a členy typu, jehož metadat je k dispozici pro účely reflexe v době běhu a platí zásady reflexe modulu runtime pro všechny prvky programu v aplikaci.  
  
 \<Direktivy > – Element  
\<Aplikace > – Element (rd.xml)  
  
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
 Následující části popisují atributy, podřízené prvky a nadřazené prvky. V tabulce podřízených elementů zásad odkazuje na typ, který metadata, která je k dispozici pro určitých prvků programu za běhu.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Activate`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory Povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Určuje dotazování na informace o nebo vytváření výčtů typy, ale neumožňuje dynamické přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON.|  
|`DataContractSerializer`|Serializace|Volitelný atribut. Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.|  
|`DataContractJsonSerializer`|Serializace|Volitelný atribut. Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.|  
|`XmlSerializer`|Serializace|Volitelný atribut. Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.|  
|`MarshalObject`|Zprostředkovatel komunikace s objekty|Volitelný atribut. Ovládací prvky zásad pro zařazování odkazové typy Windows Runtime a modelu COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace s objekty|Volitelný atribut. Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace s objekty|Volitelný atribut. Určuje zásady pro zařazování struktur do nativního kódu.|  
  
## <a name="all-attributes"></a>Všechny atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení pro tuto zásadu použít typy v aplikaci. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|Použije zásady na všechny typy v konkrétním sestavení.|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Použije zásady na všechny typy v konkrétním oboru názvů.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Použije zásady na konkrétní typ, jako je například třídy nebo struktury.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Použije zásady na Konstruovaný obecný typ. Například [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element může použít k definování zásad pro `List<String>` typu.|  
|[\<Method>](../../../docs/framework/net-native/method-element-net-native.md)|Použije zásady na metoda u určitého typu.|  
|[\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Použije zásady na konstruovanou obecnou metodu.|  
|[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)|Použije zásady na vlastnost určitého typu.|  
|[\<pole >](../../../docs/framework/net-native/field-element-net-native.md)|Použije zásady na pole určitého typu.|  
|[\<Event>](../../../docs/framework/net-native/event-element-net-native.md)|Použije zásady na událost u určitého typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Direktivy >](../../../docs/framework/net-native/directives-element-net-native.md)|Kořenový prvek souboru direktiv modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 [ \<Direktivy >](../../../docs/framework/net-native/directives-element-net-native.md) element může obsahovat nula nebo jedna `<Application>` elementu. Více `<Application>` elementy v souboru direktivy jeden reflexe nejsou podporovány.  
  
 `<Application>` Elementu lze použít v jednom ze dvou způsobů:  
  
-   Jako kontejner pro definování prvky programu, jejichž metadat je potřeba v době běhu. V takovém případě `<Application>` element nemusí mít žádné atributy. V době kompilace kompilátor nástroje hledání všech knihoven, včetně základní knihovny rozhraní .NET Framework, pro prvky programu identifikovaný podřízených elementů `<Application>` elementu. Naproti tomu kompilačních nástrojů hledání pouze v knihovně, které jsou určené [ \<knihovny >](../../../docs/framework/net-native/library-element-net-native.md) – element pro prvky programu identifikovaný podřízených elementů [ \<knihovny >](../../../docs/framework/net-native/library-element-net-native.md).  
  
-   Jako element, který nastaví zásadu platnou v celé aplikaci pro reflexi, serializace a zprostředkovatele komunikace s objekty. Atributy `<Application>` element definovat celou aplikaci zásady, které mohou být přepsána podřízené prvky definované `<Application>` nebo [ \<knihovny >](../../../docs/framework/net-native/library-element-net-native.md) elementu.  
  
## <a name="see-also"></a>Viz také:
- [\<Knihovna > – Element](../../../docs/framework/net-native/library-element-net-native.md)
- [\<Direktivy > – Element](../../../docs/framework/net-native/directives-element-net-native.md)
- [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
