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
ms.openlocfilehash: 43bc3c40bfc0b0ce4c0b18683092faf8b67e1c04
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927697"
---
# <a name="systemcodedom-element"></a>\<system.codedom> Element
Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.  
  
 \<Element > Konfigurace  
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
|[\<compilers>](compilers-element.md)|Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více [ \<elementů > kompilátoru](compiler-element.md) .|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> Konfigurace](../configuration-element.md)|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="net-framework-version-20"></a>.NET Framework verze 2,0  
 <xref:Microsoft.CSharp.CSharpCodeProvider> [ ElementSystem.CodeDom>obsahujenastaveníkonfiguracekompilátoruprojazykovézprostředkovatelenainstalovanévpočítačikroměvýchozíchzprostředkovatelů,kteříjsounainstalováni\<](system-codedom-element.md) s .NET Framework, například a <xref:Microsoft.VisualBasic.VBCodeProvider>. Kompilátory > element obsahuje nula nebo více [ \<elementů > kompilátoru](compiler-element.md) . [ \<](compilers-element.md) [ Každý\<kompilátor >](compiler-element.md) element určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.  
  
 Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení do konfiguračního souboru počítače (Machine. config) pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci. <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> Použijte metodu pro programové vytvoření výčtu výchozích zprostředkovatelů jazyků a poskytovatelů jazyka identifikovaných nastavením konfigurace kompilátoru v počítači.  
  
> [!NOTE]
> Ve verzích .NET Framework 1,0 a 1,1 jsou výchozí poskytovatelé jazyka dodané .NET Framework identifikováni v [ \<prvku > kompilátoru](compilers-element.md) . V .NET Framework verze 2,0 nejsou výchozí poskytovatelé jazyků identifikováni v [ \<>](compilers-element.md) elementu compilers, ale lze je <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> vyčíslit pomocí metody.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework verze 1,0 a 1,1  
 Element [System. CodeDom > obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků v počítači. \<](system-codedom-element.md) Kompilátory > element obsahuje nula nebo více [ \<elementů > kompilátoru](compiler-element.md) . [ \<](compilers-element.md) [ Každý\<kompilátor >](compiler-element.md) element určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.  
  
 .NET Framework definuje počáteční nastavení kompilátoru v konfiguračním souboru počítače (Machine. config). Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci. <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> Použijte metodu k programovému vytvoření výčtu poskytovatele jazyka a nastavení konfigurace kompilátoru v počítači.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schéma konfiguračního souboru](../index.md)
- [Schéma nastavení kompilátoru a poskytovatele jazyka](index.md)
- [\<> – element kompilátoru](compiler-element.md)
