---
title: <Application>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2183a64f4e30a5188940abd5108a7ca1bddfe120
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049934"
---
# <a name="application-element-net-native"></a>\<> Element aplikace (.NET Native)
Slouží jako kontejner pro typy celé aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi za běhu a aplikují zásady reflexe za běhu do všech prvků programu v aplikaci.  
  
 \<Direktivy > element  
\<> Element aplikace (RD. XML)  
  
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
 Následující části popisují atributy, podřízené prvky a nadřazené prvky. V tabulce podřízených elementů odkazuje zásada na druh metadat, který je k dispozici pro určité prvky programu za běhu.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování na informace o nebo vytváření výčtu typů, ale nepovoluje žádný dynamický přístup v době běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.|  
|`DataContractSerializer`|Serializace|Volitelný atribut. Řídí zásady pro serializaci, která <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> používá třídu.|  
|`DataContractJsonSerializer`|Serializace|Volitelný atribut. Řídí zásady pro serializaci JSON, které <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> používají třídu.|  
|`XmlSerializer`|Serializace|Volitelný atribut. Řídí zásady pro serializaci XML, které <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> používají třídu.|  
|`MarshalObject`|Zprostředkovatel komunikace|Volitelný atribut. Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace|Volitelný atribut. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace|Volitelný atribut. Řídí zásady pro zařazování struktur do nativního kódu.|  
  
## <a name="all-attributes"></a>Všechny atributy  
  
|Value|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení pro tuto zásadu platí pro typy v aplikaci. Možné hodnoty jsou `All`, `Auto`, `Excluded` ,`PublicAndInternal`,, ,`Required PublicAndInternal`a. `Required Public` `Public` `Required All` Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> Sestavení](assembly-element-net-native.md)|Použije zásady na všechny typy v konkrétním sestavení.|  
|[\<Namespace>](namespace-element-net-native.md)|Použije zásady na všechny typy v konkrétním oboru názvů.|  
|[\<Zadejte >](type-element-net-native.md)|Použije zásady na konkrétní typ, jako je třída nebo struktura.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Použije zásady na konstruovaný obecný typ. Například `List<String>` [ \<element TypeInstantiation >](typeinstantiation-element-net-native.md) lze použít k definování zásad pro typ.|  
|[\<Method>](method-element-net-native.md)|Použije zásady na metodu konkrétního typu.|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|Použije zásady na vytvořenou obecnou metodu.|  
|[\<> Vlastnosti](property-element-net-native.md)|Použije zásady na vlastnost u určitého typu.|  
|[\<> Pole](field-element-net-native.md)|Použije zásady na pole konkrétního typu.|  
|[\<> Události](event-element-net-native.md)|Použije zásady na událost konkrétního typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> Direktiv](directives-element-net-native.md)|Kořenový prvek souboru direktiv modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Direktivy > element může obsahovat nula nebo jeden `<Application>` element. [ \<](directives-element-net-native.md) Více `<Application>` elementů v jednom souboru směrnic reflexe není podporováno.  
  
 `<Application>` Element lze použít jedním ze dvou způsobů:  
  
- Jako kontejner pro definování prvků programu, jejichž metadata jsou potřebná v době běhu. V takovém případě `<Application>` element nemusí mít žádné atributy. V době kompilace nástroje kompilátoru hledají všechny knihovny, včetně .NET Framework základních knihoven, pro prvky programu identifikované podřízenými prvky `<Application>` elementu. Naproti tomu nástroje kompilátoru vyhledají pouze knihovnu určenou v [ \<knihovně >](library-element-net-native.md) element pro prvky programu identifikované podřízenými prvky [ \<knihovny >](library-element-net-native.md).  
  
- Jako prvek, který nastavuje zásady pro reflexi, serializaci a spolupráci pro celé aplikace. Atributy `<Application>` elementu definují zásady pro aplikace, které mohou být přepsány podřízenými prvky definovanými `<Application>` [ \<> knihovny](library-element-net-native.md) nebo elementu.  
  
## <a name="see-also"></a>Viz také:

- [\<Element > knihovny](library-element-net-native.md)
- [\<Direktivy > element](directives-element-net-native.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
