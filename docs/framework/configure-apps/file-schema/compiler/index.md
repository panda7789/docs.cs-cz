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
manager: markl
ms.openlocfilehash: beb38c00c7055d8edfff6f574ec454902e3a9b14
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753687"
---
# <a name="compiler-and-language-provider-settings-schema"></a>Schéma nastavení kompilátoru a poskytovatele jazyka
Kompilátoru a poskytovatele nastavení jazyka zadejte kompilátor – elementy konfigurace pro zprostředkovatele dostupný jazyk. Každý prvek konfigurace kompilátoru Určuje kód název typu poskytovatele, parametry kompilátoru jazyka názvy podporu a podporu přípony souborů.  
  
 Rozhraní .NET Framework definuje nastavení počáteční kompilátoru v konfiguračním souboru počítače (Machine.config). Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementace. Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metoda prostřednictvím kódu programu výčet zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.  
  
 [\<Konfigurace > elementu](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<System.CodeDom – >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [\<Kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [\<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<System.CodeDom – >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Určuje kompilátor – nastavení konfigurace pro zprostředkovatele dostupný jazyk.|  
|[\<Kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Kontejner pro kompilátor – elementy konfigurace; obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.|  
|[\<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Kompilátor – konfigurační atributy Určuje jazyk zprostředkovatele.|  
  
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
 [\<kompilátoru > elementu](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
