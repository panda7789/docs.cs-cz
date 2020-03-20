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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155385"
---
# <a name="systemcodedom-element"></a>\<system.codedom> Element
Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.  
  
[**\<>konfigurace**](../configuration-element.md)  
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
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>kompilátorů](compilers-element.md)|Kontejner pro konfigurační prvky kompilátoru; obsahuje nula [ \<](compiler-element.md) nebo více>prvků kompilátoru.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>konfigurace](../configuration-element.md)|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="net-framework-version-20"></a>Rozhraní .NET Framework verze 2.0  
 Element [ \<system.codedom>](system-codedom-element.md) obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků nainstalovaných v počítači kromě výchozích <xref:Microsoft.VisualBasic.VBCodeProvider>zprostředkovatelů nainstalovaných pomocí rozhraní .NET Framework, například <xref:Microsoft.CSharp.CSharpCodeProvider> rozhraní a . [ \<Kompilátory>](compilers-element.md) element obsahuje nula nebo více [ \<>prvků kompilátoru.](compiler-element.md) Každý [ \<prvek>kompilátoru](compiler-element.md) určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.  
  
 Vývojáři a dodavatelé kompilátoru mohou přidat nastavení konfigurace do konfiguračního souboru počítače (Machine.config) pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci. Pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> této metody můžete programově vytvořit výčet výchozích poskytovatelů jazyků a poskytovatelů jazyků identifikovaných nastavením konfigurace kompilátoru v počítači.  
  
> [!NOTE]
> V rozhraní .NET Framework verze 1.0 a 1.1 jsou v [ \<kompilátorech>](compilers-element.md) elementu identifikováni výchozí poskytovatelé jazyků dodaná rozhraním .NET Framework. V rozhraní .NET Framework verze 2.0 nejsou výchozí poskytovatelé jazyka identifikováni v [ \<kompilátorech>](compilers-element.md) elementu, ale lze je vyjmenovat pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metody.  
  
## <a name="net-framework-versions-10-and-11"></a>Rozhraní .NET Framework verze 1.0 a 1.1  
 Element [ \<system.codedom>](system-codedom-element.md) obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků v počítači. [ \<Kompilátory>](compilers-element.md) element obsahuje nula nebo více [ \<>prvků kompilátoru.](compiler-element.md) Každý [ \<prvek>kompilátoru](compiler-element.md) určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.  
  
 Rozhraní .NET Framework definuje počáteční nastavení kompilátoru v konfiguračním souboru počítače (Machine.config). Vývojáři a dodavatelé kompilátoru <xref:System.CodeDom.Compiler.CodeDomProvider> mohou přidat nastavení konfigurace pro novou implementaci. Pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> této metody můžete programově vytvořit výčet nastavení poskytovatele jazyka a konfigurace kompilátoru v počítači.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento prvek lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.  
  
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
- [\<> element kompilátoru](compiler-element.md)
