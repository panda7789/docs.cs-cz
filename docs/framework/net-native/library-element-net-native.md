---
title: <Library> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: f94bfe047fa7a95b6f24264bae0b27112c589dfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128367"
---
# <a name="library-element-net-native"></a>> element knihovny \<(.NET Native)
Definuje sestavení, které obsahuje typy a členy typů, jejichž metadata jsou k dispozici pro reflexi v době běhu.  
  
 \<direktivy > elementu  
> element knihovny \<  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Požadovaný atribut. Určuje název sestavení. Podřízené elementy tohoto `<Library>` elementu definují zásady reflexe modulu runtime pro typy a členy typů nalezené v tomto sestavení.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*assembly_name*|Jednoduchý název sestavení bez přípony souboru. Tento atribut odpovídá vlastnosti <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>. Například název sestavení s názvem Extensions. dll je "Extensions". Zvláštní podobu *assembly_name* , která podporuje podmíněné zahrnutí metadat ze sestavení, naleznete v části poznámky.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> sestavení](assembly-element-net-native.md)|Použije zásady na všechny typy v konkrétním sestavení.|  
|[Obor názvů \<](namespace-element-net-native.md)|Použije zásady na všechny typy v konkrétním oboru názvů.|  
|[Typ\<](type-element-net-native.md)|Použije zásady na konkrétní typ, jako je třída nebo struktura.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Použije zásady na konstruovaný obecný typ. Například [\<TypeInstantiation >](typeinstantiation-element-net-native.md) prvek lze použít k definování zásad pro typ `List<String>`.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Direktivy \<](directives-element-net-native.md)|Kořenový prvek souboru direktiv modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 [Direktivy\<](directives-element-net-native.md) element může obsahovat nula, jeden nebo více `<Library>` prvků.  
  
 Element `<Library>` slouží jako kontejner pro definování prvků programu, jejichž metadata jsou v době běhu potřeba; Tento prvek neposkytuje žádné zásady. V době kompilace Nástroj pro kompilátor vyhledává pouze knihovnu určenou elementem `<Library>` pro prvky programu identifikované jeho podřízenými prvky. Naproti tomu nástroje kompilátoru hledají všechny knihovny, základní knihovny including.NET Framework pro prvky programu identifikované podřízenými elementy [> elementu\<aplikace](application-element-net-native.md) .  
  
 direktivy `<Library>` mohou být podmíněně využívány. Pokud název elementu `<Library>` začíná a končí znakem hvězdičky (\*), má direktiva `<Library>` vliv pouze v případě, že je v aplikaci odkazováno na sestavení zadané mezi hvězdičkami. Například následující direktiva modulu runtime platí pouze v případě, že aplikace odkazuje na sestavení Utilities. dll.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Viz také:

- [\<> element aplikace](application-element-net-native.md)
- [\<direktivy > elementu](directives-element-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
