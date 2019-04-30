---
title: <Library> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eda4f8d3819af05b022e0633d6883cca940f67e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866851"
---
# <a name="library-element-net-native"></a>\<Knihovna > – Element (.NET Native)
Určuje sestavení, který obsahuje typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe v době běhu.  
  
 \<Direktivy > – Element  
\<Knihovna > – Element  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Požadovaný atribut. Určuje název sestavení. Podřízené prvky tohoto `<Library>` element definovat zásady reflexe modulu runtime pro typy a členy typů nalezena v tomto sestavení.|  
  
## <a name="name-attribute"></a>Název atributu  
  
|Value|Popis|  
|-----------|-----------------|  
|*assembly_name*|Jednoduchý název sestavení, bez jeho přípona souboru. Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnost. Název sestavení s názvem Extensions.dll je například "Rozšíření". V části poznámky pro zvláštní forma *název_sestavení* , který podporuje podmíněné zahrnutí metadat ze sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|Použije zásady na všechny typy v konkrétním sestavení.|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Použije zásady na všechny typy v konkrétním oboru názvů.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Použije zásady na konkrétní typ, jako je například třídy nebo struktury.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Použije zásady na Konstruovaný obecný typ. Například [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element může použít k definování zásad pro `List<String>` typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Direktivy >](../../../docs/framework/net-native/directives-element-net-native.md)|Kořenový prvek souboru direktiv modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 [ \<Direktivy >](../../../docs/framework/net-native/directives-element-net-native.md) element může obsahovat nula, jeden nebo více `<Library>` elementy.  
  
 `<Library>` Prvek slouží jako kontejner pro definování prvky programu, jejichž metadat je potřeba za běhu; tento element není vyjádření zásad. V době kompilace, kompilačních nástrojů hledání pouze v knihovně, které jsou určené `<Library>` – element pro prvky programu identifikován jeho podřízené prvky. Naproti tomu kompilátoru nástroje hledání všech knihoven, včetně.NET Framework základní knihovny, pro prvky programu identifikovaný podřízených elementů [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) elementu.  
  
 `<Library>` direktivy může podmíněně využít. Pokud název `<Library>` prvek začíná a končí s hvězdičkou (\*), `<Library>` – direktiva má vliv pouze v případě, že sestavení určena v rozsahu mezi hvězdičky odkazuje aplikaci. Například následující direktivy modulu runtime platí jenom v případě, že Utillities.dll sestavení odkazuje aplikaci.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Viz také:

- [\<Aplikace > – Element](../../../docs/framework/net-native/application-element-net-native.md)
- [\<Direktivy > – Element](../../../docs/framework/net-native/directives-element-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
