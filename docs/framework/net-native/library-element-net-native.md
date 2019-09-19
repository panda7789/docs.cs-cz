---
title: <Library>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc3c85ab99574c96d8a68d4221f218a1340e4122
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049650"
---
# <a name="library-element-net-native"></a>\<Element > knihovny (.NET Native)
Definuje sestavení, které obsahuje typy a členy typů, jejichž metadata jsou k dispozici pro reflexi v době běhu.  
  
 \<Direktivy > element  
\<Element > knihovny  
  
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
  
|Value|Popis|  
|-----------|-----------------|  
|*assembly_name*|Jednoduchý název sestavení bez přípony souboru. Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnosti. Například název sestavení s názvem Extensions. dll je "Extensions". Zvláštní podobu *assembly_name* , která podporuje podmíněné zahrnutí metadat ze sestavení, naleznete v části poznámky.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> Sestavení](assembly-element-net-native.md)|Použije zásady na všechny typy v konkrétním sestavení.|  
|[\<Namespace>](namespace-element-net-native.md)|Použije zásady na všechny typy v konkrétním oboru názvů.|  
|[\<Zadejte >](type-element-net-native.md)|Použije zásady na konkrétní typ, jako je třída nebo struktura.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Použije zásady na konstruovaný obecný typ. Například `List<String>` [ \<element TypeInstantiation >](typeinstantiation-element-net-native.md) lze použít k definování zásad pro typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> Direktiv](directives-element-net-native.md)|Kořenový prvek souboru direktiv modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Direktivy > element může obsahovat nula, jeden nebo více `<Library>` prvků. [ \<](directives-element-net-native.md)  
  
 `<Library>` Element slouží jako kontejner pro definování prvků programu, jejichž metadata jsou potřebná v době běhu; tento prvek neposkytuje expresní zásady. V době kompilace Nástroj pro kompilátor vyhledává pouze knihovnu určenou `<Library>` prvkem pro prvky programu identifikované jeho podřízenými prvky. Naproti tomu nástroje kompilátoru hledají všechny knihovny, základní knihovny including.NET Framework pro prvky programu identifikované podřízenými prvky [ \<aplikace >](application-element-net-native.md) elementu.  
  
 `<Library>`direktivy mohou být využívány podmíněně. Pokud název `<Library>` elementu začíná a končí hvězdičkou (\*), má tato `<Library>` direktiva účinek pouze v případě, že je v aplikaci odkazováno na sestavení zadané mezi hvězdičkami. Například následující direktiva modulu runtime platí pouze v případě, že aplikace odkazuje na sestavení Utilities. dll.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Viz také:

- [\<> Element aplikace](application-element-net-native.md)
- [\<Direktivy > element](directives-element-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
