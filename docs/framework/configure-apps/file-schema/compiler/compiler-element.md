---
title: "&lt;kompilátoru&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 547c08e324066b872abb8df8b8b780ab3e4644a7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltcompilergt-element"></a>&lt;kompilátoru&gt; – Element
Kompilátor – konfigurační atributy Určuje jazyk zprostředkovatele.  
  
 \<konfigurace elementu >  
\<system.codedom Element>  
\<compilers Element>  
\<compiler> Element  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`compilerOptions`|Nepovinný atribut.<br /><br /> Určuje další argumenty kompilátoru specifické pro kompilaci. Hodnoty `compilerOptions` atribut jsou většinou najdete v tématu možnosti kompilátoru pro kompilátor. V dokumentaci sady Visual Studio 2005 můžete vyhledat možnosti pro kompilátor tak, že vyhledá "– možnosti kompilátoru" v indexu.|  
|`extension`|Požadovaný atribut.<br /><br /> Poskytuje středníky oddělený seznam přípon názvů souborů, používá zdrojové soubory pro jazyk zprostředkovatele. Například ".cs".|  
|`language`|Požadovaný atribut.<br /><br /> Poskytuje středníky oddělený seznam názvů jazyka zprostředkovatel jazyk. Například "c#; cs; csharp".|  
|`type`|Požadovaný atribut.<br /><br /> Určuje název typu zprostředkovatele jazyk, včetně název sestavení obsahujícího implementaci zprostředkovatele. Název typu musí splňovat požadavky definované v [určení plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`warningLevel`|Nepovinný atribut.<br /><br /> Určuje úroveň pro upozornění kompilátoru výchozí; Určuje úroveň, kdy zprostředkovatel jazyka zpracovává kompilace upozornění jako chyby.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<providerOption> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|Určuje atributy verze kompilátoru jazyka zprostředkovatele.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Konfigurace > elementu](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|[\<system.codedom> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Určuje kompilátor – nastavení konfigurace pro zprostředkovatele dostupný jazyk.|  
|[\<compilers> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Kontejner pro kompilátor – elementy konfigurace; obsahuje nula nebo více `<compiler>` elementy.|  
  
## <a name="remarks"></a>Poznámky  
 Každý `<compiler>` element určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele. Zprostředkovatel rozšiřuje <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> třídy pro konkrétní jazyk; `<compiler>` element definuje kompilátoru a nastavení generátor kódu pro jazyk zprostředkovatele.  
  
 Rozhraní .NET Framework definuje nastavení počáteční kompilátoru v konfiguračním souboru počítače (Machine.config). Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementace. Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metoda prostřednictvím kódu programu výčet zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.  
  
 Kompilátor – elementy v aplikaci nebo soubor webové konfigurace můžete doplnit nebo přepsat nastavení v konfiguračním souboru počítače. Pokud je více než jednu implementaci zprostředkovatele je nakonfigurován pro stejný název jazyka a stejnou příponu souboru, přepíše poslední odpovídající konfigurace zprostředkovatelů předchozí nakonfigurovaný pro tento jazyk název nebo příponu souboru.  
  
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
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<compilers> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [Určení úplných názvů typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [kompilátoru Element pro kompilátory pro kompilaci (schéma nastavení ASP.NET)](http://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
