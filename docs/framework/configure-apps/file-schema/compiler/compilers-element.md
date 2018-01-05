---
title: "&lt;Kompilátory&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: deb9f99253c4cf523c8fe5052b1f30823e5e9944
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcompilersgt-element"></a>&lt;Kompilátory&gt; – Element
Kontejner pro kompilátor – elementy konfigurace; obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.  
  
 \<Konfigurace >  
\<System.CodeDom – >  
\<Kompilátory > elementu  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<kompilátoru > elementu](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Kompilátor – konfigurační atributy Určuje jazyk zprostředkovatele.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Konfigurace > elementu](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|[\<System.CodeDom – > elementu](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Určuje kompilátor – nastavení konfigurace pro zprostředkovatele dostupný jazyk.|  
  
## <a name="remarks"></a>Poznámky  
 [ \<Kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element obsahuje konfigurační nastavení kompilátoru pro zprostředkovatelé jazyka v počítači. Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.  
  
 Rozhraní .NET Framework definuje počáteční kompilátoru a poskytovatele nastavení jazyka v konfiguračním souboru počítače (Machine.config). Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro novou <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementace. Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metoda prostřednictvím kódu programu výčet zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze v konfiguračním souboru počítače a konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje prvek typické kompilátoru konfigurace.  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Schéma nastavení kompilátoru a poskytovatele jazyka](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [\<kompilátoru > elementu](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
