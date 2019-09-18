---
title: <Assembly>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1743264996680c6a0ce308619d7a5bafef5d07a5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049922"
---
# <a name="assembly-element-net-native"></a>\<> Element sestavení (.NET Native)
Aplikuje zásady reflexe za běhu na všechny typy v zadaném sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Assembly Name="assembly_name"   
          Activate="policy_setting"  
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
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje jednoduchý název sestavení.|  
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování na informace o nebo vytváření výčtu typů v sestavení, ale nepovoluje žádný dynamický přístup v době běhu.|  
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
|*assembly_name*|Jednoduchý název sestavení bez přípony souboru. Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnosti. Například název sestavení s názvem Extensions. dll je "Extensions".<br /><br /> Můžete také zadat řetězcový `*Application*` literál pro aplikování zásad na všechna sestavení v balíčku aplikace, zda jsou tato sestavení načtena nebo nikoli. `*Application*`nikdy nepoužije zásady na .NET Framework sestavení.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Value|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro všechny typy v sestavení. Možné hodnoty jsou `All`, `Auto`, `Excluded` ,`PublicAndInternal`,, ,`Required PublicAndInternal`a. `Required Public` `Public` `Required All` Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Namespace>](namespace-element-net-native.md)|Aplikuje zásady odrazu na všechny typy v podřízeném oboru názvů.|  
|[\<Zadejte >](type-element-net-native.md)|Aplikuje zásadu odrazu na typ.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> Aplikace](application-element-net-native.md)|Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi v době běhu. > Element `<Assembly>` aplikace může mít nulový, jeden nebo více prvků. [ \<](application-element-net-native.md)|  
|[\<Library>](library-element-net-native.md)|Definuje sestavení, které obsahuje typy a členy typů, jejichž metadata jsou k dispozici pro reflexi v době běhu. Element > `<Assembly>` knihovny může mít nula nebo jeden element. [ \<](library-element-net-native.md)|  
  
## <a name="remarks"></a>Poznámky  
 `<Assembly>` Element definuje zásady modulu runtime pro všechny typy v sestavení. Liší se od [ \<knihovny >](library-element-net-native.md) elementu, který určuje knihovnu, ale závisí na jejích podřízených prvcích k definování zásad reflexe modulu runtime. `<Assembly>` Element se vztahuje na všechny typy v sestavení, pokud nejsou přepsány podřízeným elementem.  
  
 Následující příklad ukazuje, jak můžete použít zásady modulu runtime pro všechny typy v sestaveních v rámci balíčku aplikace přiřazením `Name` atributu a hodnoty "* Application\*". Element musí být podřízeným [ \<elementem > aplikace.](application-element-net-native.md) `<Assembly>`  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 Atributy `Activate`, `Browse`, `Dynamic`a jsouvšechnyvolitelné.`Serialize` `<Assembly>` Element však musí obsahovat alespoň jeden z těchto atributů.  
  
## <a name="see-also"></a>Viz také:

- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
