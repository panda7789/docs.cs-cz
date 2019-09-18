---
title: <Namespace>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7be004776d2a2fd3b4c41fb21b3ac244946f2166
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049419"
---
# <a name="namespace-element-net-native"></a>\<Namespace – element > elementu (.NET Native)
Aplikuje zásady reflexe za běhu na všechny typy v zadaném oboru názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Namespace Name="namespace_name"   
           Activate="policy_type"   
           Browse="policy_type"  
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
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název oboru názvů.|  
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci, která <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> používá třídu.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci JSON, které <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> používají třídu.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci XML, které <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> používají třídu.|  
|`MarshalObject`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování struktur do nativního kódu.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Value|Popis|  
|-----------|-----------------|  
|*namespace_name*|Název oboru názvů. [ \<](library-element-net-native.md) [ \<](assembly-element-net-native.md) [ \<](application-element-net-native.md)Pokud je obornázvů>elementpodřízený>aplikace,knihovně>neboelementusestavení>,musíbýtnamespace_nameplněkvalifikované.\< název oboru názvů. Pokud je \<obor názvů > element podřízenosti jiného oboru názvů > elementu, namespace_name musí být relativní název oboru názvů. \<|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Value|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro všechny typy v oboru názvů Možné hodnoty jsou `All`, `Auto`, `Excluded` ,`PublicAndInternal`,, ,`Required PublicAndInternal`a. `Required Public` `Public` `Required All` Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`<Namespace>`|Aplikuje zásady reflexe za běhu na všechny typy v nadřazeném oboru názvů.|  
|[\<Zadejte >](type-element-net-native.md)|Aplikuje zásadu odrazu na typ.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> Aplikace](application-element-net-native.md)|Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu. > Element [ \<](assembly-element-net-native.md) aplikace může mít nula, jednu nebo více > prvků sestavení. [ \<](application-element-net-native.md)|  
|[\<> Sestavení](assembly-element-net-native.md)|Aplikuje zásady reflexe za běhu na všechny typy v zadaném sestavení.|  
|[\<Library>](library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typů, jejichž metadata jsou k dispozici pro reflexi v době běhu. Element > [ \<](assembly-element-net-native.md) knihovny může mít 0 nebo jedno sestavení > elementu. [ \<](library-element-net-native.md)|  
|`<Namespace>`|Aplikuje zásady odrazu na všechny typy v nadřazeném oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Atributy `Activate`, `Browse`, `Dynamic`a jsouvšechnyvolitelné.`Serialize` Pokud není žádné, `<Namespace>` prvek slouží jako kontejner pro podřízené elementy. Pokud jsou k dispozici, `<Namespace>` element aplikuje zásady reflexe modulu runtime na všechny typy v zadaném oboru názvů.  
  
 V`<Namespace>` případě, že se jedná o podřízený [ \<prvek sestavení >](assembly-element-net-native.md) , přepíše prvek zásady reflexe modulu runtime definované [ \<prvkem sestavení >](assembly-element-net-native.md) .  
  
## <a name="see-also"></a>Viz také:

- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
