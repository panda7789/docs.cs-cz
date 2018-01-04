---
title: Element &lt;Library&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd2663bbd5ca93341455b7bd036469d25d91f4a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltlibrarygt-element-net-native"></a>Element &lt;Library&gt; (.NET Native)
Definuje sestavení, které obsahuje typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu.  
  
 \<Direktivy > elementu  
\<Knihovna > elementu  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Požadovaný atribut. Určuje název sestavení. Podřízené elementy tohoto `<Library>` element definovat zásady reflexe modulu runtime pro typy a členy typu najít v tomto sestavení.|  
  
## <a name="name-attribute"></a>Atribut Name.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*assembly_name*|Jednoduchý název sestavení, bez jeho přípona souboru. Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnost. Název sestavení s názvem Extensions.dll je například "Rozšíření". Najdete v části poznámky pro speciální formu *assembly_name* podmíněné zahrnutí metadat ze sestavení, která podporuje.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|Zásady platí pro všechny typy v určitém sestavení.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Zásady platí pro všechny typy v konkrétní oboru názvů.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Platí pro konkrétní typ, jako je například třídu nebo strukturu zásad.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Zásada se vztahuje na vytvořený obecného typu. Například [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element může definovat zásady pro `List<String>` typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Direktivy jazyka >](../../../docs/framework/net-native/directives-element-net-native.md)|Kořenový element souboru direktivy modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 [ \<Direktivy >](../../../docs/framework/net-native/directives-element-net-native.md) element může obsahovat nula, jednu nebo více `<Library>` elementy.  
  
 `<Library>` Element slouží jako kontejner pro definování program elementy, jejichž metadat je vyžadována v době běhu; tento element není vyjádření zásad. Při kompilaci, nástrojů kompilátoru vyhledávat pouze v knihovně, které jsou určené, které `<Library>` element pro program prvky identifikovaná její podřízené elementy. Na rozdíl od nástroje kompilátoru hledání všechny knihovny, including.NET Framework základní knihovny, pro program prvky identifikovaná podřízených elementů [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) element.  
  
 `<Library>`direktivy, lze podmíněně využívat. Pokud název `<Library>` element zahájení a ukončení s hvězdičkou (*), `<Library>` – direktiva má význam jen v případě, že zadaný v rozmezí hvězdičky sestavení odkazuje aplikace. Například následující direktivy modulu runtime platí jenom v případě, že Utillities.dll sestavení odkazuje aplikace.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Viz také  
 [\<Aplikace > elementu](../../../docs/framework/net-native/application-element-net-native.md)  
 [\<Direktivy > elementu](../../../docs/framework/net-native/directives-element-net-native.md)  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
