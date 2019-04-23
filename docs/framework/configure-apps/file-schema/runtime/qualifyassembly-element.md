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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a4741c6a4745bdba00fdb525b39b70d0b15e005
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109445"
---
# <a name="qualifyassembly-element"></a>\<qualifyassembly – > – Element
Určuje úplný název sestavení, které se mají dynamicky načíst při použití částečný název.  
  
 \<Konfigurace >  
\<modul runtime >  
\<assemblybinding – >  
\<qualifyAssembly>  
  
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
|`partialName`|Požadovaný atribut.<br /><br /> Částečný název sestavení, určuje, jak se zobrazí v kódu.|  
|`fullName`|Požadovaný atribut.<br /><br /> Určuje úplný název sestavení, jak se zobrazí v globální mezipaměti sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Volání <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda názvů částečného sestavení způsobí, že modul common language runtime vyhledat sestavení pouze v základní adresář aplikace. Použití  **\<qualifyassembly – >** prvku v konfiguračním souboru aplikace zadejte informace o úplné sestavení (název, verzi, token veřejného klíče a jazykovou verzi) a způsobit, že modul common language runtime pro hledání pro sestavení v globální mezipaměti sestavení.  
  
 **FullName** atribut musí obsahovat čtyři pole Identita sestavení: název, verzi, token veřejného klíče a jazykovou verzi. **PartialName** atribut částečně musí odkazovat na sestavení. Je potřeba určit nejmíň textový název sestavení (nejběžnější případy), ale může také obsahovat verzi, token veřejného klíče, nebo jazykové verze (nebo libovolnou kombinaci čtyři, ale ne všechny čtyři). **PartialName** musí odpovídat názvu zadané ve volání. Například nelze zadat `"math"` jako **partialName** atribut v konfiguračním souboru a volání `Assembly.Load("math, Version=3.3.3.3")` ve vašem kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad změní logicky volání `Assembly.Load("math")` do `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
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

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Jak běhové prostředí vyhledává sestavení](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Částečné odkazy na sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
