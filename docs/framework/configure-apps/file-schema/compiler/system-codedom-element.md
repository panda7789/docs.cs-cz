---
title: <system.codedom> – element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155385"
---
# <a name="systemcodedom-element"></a>Element \<system.codedom>
Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
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
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více [\<compiler>](compiler-element.md) prvků.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="net-framework-version-20"></a>.NET Framework verze 2,0  
 [\<system.codedom>](system-codedom-element.md)Element obsahuje nastavení konfigurace kompilátoru pro jazykové zprostředkovatele nainstalované v počítači kromě výchozích zprostředkovatelů, které jsou nainstalovány s .NET Framework, jako jsou <xref:Microsoft.CSharp.CSharpCodeProvider> a <xref:Microsoft.VisualBasic.VBCodeProvider> . [\<compilers>](compilers-element.md)Element obsahuje nula nebo více [\<compiler>](compiler-element.md) prvků. Každý [\<compiler>](compiler-element.md) prvek určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.  
  
 Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení do konfiguračního souboru počítače (Machine. config) pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci. Použijte <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metodu pro programové vytvoření výčtu výchozích zprostředkovatelů jazyků a poskytovatelů jazyka identifikovaných nastavením konfigurace kompilátoru v počítači.  
  
> [!NOTE]
> V .NET Framework verzích 1,0 a 1,1 jsou v elementu identifikováni výchozí poskytovatelé jazyka poskytnuté .NET Framework [\<compilers>](compilers-element.md) . V .NET Framework verze 2,0 nejsou v elementu identifikováni výchozí poskytovatelé jazyka [\<compilers>](compilers-element.md) , ale lze je vyčíslit pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metody.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework verze 1,0 a 1,1  
 [\<system.codedom>](system-codedom-element.md)Element obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků v počítači. [\<compilers>](compilers-element.md)Element obsahuje nula nebo více [\<compiler>](compiler-element.md) prvků. Každý [\<compiler>](compiler-element.md) prvek určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.  
  
 .NET Framework definuje počáteční nastavení kompilátoru v konfiguračním souboru počítače (Machine. config). Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci. Použijte <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metodu k programovému vytvoření výčtu poskytovatele jazyka a nastavení konfigurace kompilátoru v počítači.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje typickou konfiguraci kompilátoru.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schéma konfiguračního souboru](../index.md)
- [Schéma nastavení kompilátoru a poskytovatele jazyka](index.md)
- [\<compiler>Objekt](compiler-element.md)
