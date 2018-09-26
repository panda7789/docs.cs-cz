---
title: Schéma nastavení kompilátoru a poskytovatele jazyka
ms.date: 03/30/2017
helpviewer_keywords:
- configuration settings [.NET Framework], compilers
- compiler configuration elements, schema
- compiler configuration elements
- language providers
- compiler configuration settings, schema
- configuration schema [.NET Framework], compiler settings
- language providers, settings schema
- compiler configuration settings
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c64dd85103e818ae603435c1a3f80f76e672ac84
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47069558"
---
# <a name="compiler-and-language-provider-settings-schema"></a>Schéma nastavení kompilátoru a poskytovatele jazyka
Nastavení poskytovatele jazyka a kompilátoru zadejte kompilátor – elementy konfigurace pro zprostředkovatele dostupných poskytovatelů jazyka. Každý prvek konfigurace kompilátor Určuje kód název typu poskytovatele, parametry kompilátoru nepodporuje názvy jazyků a podporované přípony souborů.  
  
 Rozhraní .NET Framework definuje počáteční kompilátor – nastavení v konfiguračním souboru počítače (Machine.config). Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro nové <xref:System.CodeDom.Compiler.CodeDomProvider> implementace. Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> způsob, jak programově vytvářet výčty zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.  
  
 [\<Konfigurace > – Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<System.CodeDom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [\<Kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [\<Kompilátor >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<System.CodeDom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.|  
|[\<Kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.|  
|[\<Kompilátor >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Určuje kompilátor – konfigurační atributy pro poskytovatele jazyka.|  
  
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
 [\<Kompilátor > – Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
