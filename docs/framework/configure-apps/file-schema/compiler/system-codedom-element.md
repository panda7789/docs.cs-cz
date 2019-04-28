---
title: <system.codedom> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 0f47255bb4073007a847e4a8b85ccfd34100582b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674792"
---
# <a name="systemcodedom-element"></a>\<system.codedom> Element
Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.  
  
 \<Konfigurace > – Element  
\<system.codedom> Element  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="net-framework-version-20"></a>Rozhraní .NET framework verze 2.0  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element obsahuje konfigurační nastavení kompilátoru pro poskytovatele jazyk nainstalovaný v počítači se kromě výchozího zprostředkovatele, které jsou nainstalovány s rozhraním .NET Framework, jako <xref:Microsoft.CSharp.CSharpCodeProvider> a <xref:Microsoft.VisualBasic.VBCodeProvider>. [ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) prvek obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy. Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) prvek určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.  
  
 Vývojářům a dodavatelům kompilátoru můžete přidat konfigurační nastavení do konfiguračního souboru počítače (Machine.config) pro nový <xref:System.CodeDom.Compiler.CodeDomProvider> implementace. Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metoda jak programově vytvářet výčty výchozí jazyk poskytovatele i zprostředkovatelé jazyka identifikovaný kompilátor – nastavení konfigurace v počítači.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 1.0 a 1.1, výchozí jazyk poskytovatele dodané rozhraním .NET Framework jsou uvedené v [ \<compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu. V rozhraní .NET Framework verze 2.0, výchozí jazyk poskytovatele nejsou uvedené v [ \<kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu, ale mohou být uvedené použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metody.  
  
## <a name="net-framework-versions-10-and-11"></a>Rozhraní .NET framework verze 1.0 a 1.1  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element obsahuje konfigurační nastavení kompilátoru pro poskytovatele jazyka v počítači. [ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) prvek obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy. Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) prvek určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.  
  
 Rozhraní .NET Framework definuje počáteční kompilátor – nastavení v konfiguračním souboru počítače (Machine.config). Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro nové <xref:System.CodeDom.Compiler.CodeDomProvider> implementace. Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> způsob, jak programově vytvářet výčty zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít v konfiguračním souboru počítače a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje typické kompilátoru konfigurace.  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
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
