---
title: "&lt;qualifyassembly –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 521bbccd83f224cc824dae41309715d65472454e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltqualifyassemblygt-element"></a>&lt;qualifyassembly –&gt; – Element
Určuje úplný název sestavení, které by měl být dynamicky načíst, pokud je použít částečný název.  
  
 \<Konfigurace >  
\<modul runtime >  
\<assemblybinding – >  
\<qualifyassembly – >  
  
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
|`partialName`|Požadovaný atribut.<br /><br /> Určuje částečné název sestavení, jak se objevuje v kódu.|  
|`fullName`|Požadovaný atribut.<br /><br /> Úplný název sestavení, určuje, jak se objevuje v globální mezipaměti sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Volání <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda pomocí názvů částečného sestavení způsobí, že modul common language runtime a hledat sestavení pouze v adresáři základní aplikace. Použití  **\<qualifyassembly – >** element v konfiguračním souboru aplikace k poskytování informací o úplné sestavení (název, verzi, token veřejného klíče a jazykovou verzi) a způsobit, že modul common language runtime pro vyhledávání pro sestavení v globální mezipaměti sestavení.  
  
 **FullName** atributu musí obsahovat čtyři pole identity sestavení: název, verzi, token veřejného klíče a jazykovou verzi. **PartialName** atributu musí odkazovat částečně sestavení. Musíte zadat alespoň název sestavení text (v případě nejběžnějších)), ale může také obsahovat verzi, token veřejného klíče, nebo jazykovou verzi (nebo libovolnou kombinaci čtyři, ale ne všechny čtyři). **PartialName** musí odpovídat názvu zadaná v volání. Například nelze zadat `"math"` jako **partialName** atribut v konfiguračním souboru a volání `Assembly.Load("math, Version=3.3.3.3")` v kódu.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [NIB: Částečné odkazy na sestavení](http://msdn.microsoft.com/en-us/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
