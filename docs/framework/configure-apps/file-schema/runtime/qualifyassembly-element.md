---
title: Element <qualifyAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 17cfe9fc39d65f146beef5d02c701f5e3e2fbbe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115787"
---
# <a name="qualifyassembly-element"></a>\<element > qualifyAssembly
Určuje úplný název sestavení, které by mělo být dynamicky načteno při použití částečného názvu.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<qualifyAssembly >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`partialName`|Požadovaný atribut.<br /><br /> Určuje částečný název sestavení, jak se zobrazí v kódu.|  
|`fullName`|Požadovaný atribut.<br /><br /> Určuje úplný název sestavení, který se zobrazí v globální mezipaměti sestavení (GAC).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Volání metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> s použitím částečných názvů sestavení způsobí, že modul CLR (Common Language Runtime) hledá sestavení pouze v základním adresáři aplikace. Pomocí elementu **\<qualifyAssembly >** v konfiguračním souboru aplikace poskytněte úplné informace o sestavení (název, verze, token veřejného klíče a jazykové verzi) a způsobí, že modul CLR (Common Language Runtime) vyhledá sestavení v globálním mezipaměť sestavení.  
  
 Atribut **FullName** musí zahrnovat čtyři pole identity sestavení: název, verze, token veřejného klíče a jazykovou verzi. Atribut **Partial** musí odkazovat na sestavení částečně. Je nutné zadat alespoň textový název sestavení (Nejběžnější případ), ale můžete také zahrnout verze, token veřejného klíče nebo jazykovou verzi (nebo libovolnou kombinaci čtyř, ale ne všech čtyř). Parametr **Partial** se musí shodovat s názvem zadaným ve vašem volání. Například nemůžete zadat `"math"` jako atribut **částečného** atributu do konfiguračního souboru a volat `Assembly.Load("math, Version=3.3.3.3")` ve vašem kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad logicky zapne volání `Assembly.Load("math")` do `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Jak běhové prostředí vyhledává sestavení](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Odkazy na částečné sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
