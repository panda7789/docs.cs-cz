---
title: '&lt;Kompilátory&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 7d9deda5e0ffeb95483eebbbb0a63831db08ac0b
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083363"
---
# <a name="ltcompilersgt-element"></a>&lt;Kompilátory&gt; – Element
Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.  
  
 \<Konfigurace >  
\<system.codedom>  
\<Kompilátory > – Element  
  
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
|[\<Kompilátor > – Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Určuje kompilátor – konfigurační atributy pro poskytovatele jazyka.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Konfigurace > – Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|[\<system.codedom> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.|  
  
## <a name="remarks"></a>Poznámky  
 [ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element obsahuje konfigurační nastavení kompilátoru pro poskytovatele jazyka v počítači. Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) prvek určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.  
  
 Rozhraní .NET Framework definuje počáteční kompilátoru a poskytovatele nastavení jazyka v konfiguračním souboru počítače (Machine.config). Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro nové <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementace. Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> způsob, jak programově vytvářet výčty zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít v konfiguračním souboru počítače a konfigurační soubor aplikace.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Schéma nastavení kompilátoru a poskytovatele jazyka](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [\<Kompilátor > – Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
