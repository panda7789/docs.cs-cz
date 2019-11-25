---
title: Element <compilers>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: b09c2a1f67974a67a3f9d58af7cb8cf66a197026
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088701"
---
# <a name="compilers-element"></a>> elementu \<kompilátorů
Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více [\<> elementy kompilátoru](compiler-element.md) .  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. codedom >** ](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<ch kompilátorů >**

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
|[\<element > kompilátoru](compiler-element.md)|Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[> element konfigurace \<](../configuration-element.md)|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|[\<> element System. CodeDom](system-codedom-element.md)|Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.|  
  
## <a name="remarks"></a>Poznámky  
 [> Prvek\<compilers](compilers-element.md) obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků v počítači. Každý [\<kompilátor >](compiler-element.md) prvek určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.  
  
 .NET Framework definuje nastavení počátečního kompilátoru a poskytovatele jazyka v konfiguračním souboru počítače (Machine. config). Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení pro novou implementaci <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>. Použijte metodu <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> k programovému vytvoření výčtu poskytovatele jazyka a nastavení konfigurace kompilátoru v počítači.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje typický prvek konfigurace kompilátoru.  
  
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
- [Schéma konfiguračního souboru](../index.md)
- [Schéma nastavení kompilátoru a poskytovatele jazyka](index.md)
- [\<element > kompilátoru](compiler-element.md)
