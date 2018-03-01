---
title: "&lt;Hodnota providerOption&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: f28b7b43f2f782744a0dbc81bd0b91bbbcd8abba
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltprovideroptiongt-element"></a>&lt;Hodnota providerOption&gt; – Element
Určuje verzi atributy kompilátoru jazyka zprostředkovatele.  
  
 \<konfigurace elementu >  
\<system.codedom Element>  
\<compilers Element>  
\<compiler> Element  
\<Hodnota providerOption > elementu  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Požadovaný atribut.<br /><br /> Určuje název možnost; například "CompilerVersion".|  
|`value`|Požadovaný atribut.<br /><br /> Určuje hodnotu pro možnost; například "v3.5".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Konfigurace > elementu](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.|  
|[\<system.codedom> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Určuje kompilátor – nastavení konfigurace pro zprostředkovatele dostupný jazyk.|  
|[\<compilers> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Kontejner pro kompilátor – elementy konfigurace; obsahuje nula nebo více `<compiler>` elementy.|  
|[\<compiler> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Kompilátor – konfigurační atributy Určuje jazyk zprostředkovatele.|  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 3.5 zprostředkovatele kódu Code Document Object Model (CodeDOM) může podporovat možnosti specifický pro zprostředkovatele pomocí `<providerOption>` elementu.  
  
 Rozhraní .NET Framework 3.5 zahrnuje aktualizované sestavení rozhraní .NET Framework 2.0 a poskytuje nové verze 3.5 sestavení, které obsahují nové typy. Kód zprostředkovatele Microsoft C# a Visual Basic jsou obsaženy v sestavení rozhraní .NET Framework 2.0, ale byly aktualizovány pro podporu kompilátory verze 3.5. Ve výchozím nastavení zprostředkovatele aktualizovaný kódu generovat kód pro kompilátory verze 2.0. Můžete použít `<providerOption>` elementu, který chcete změnit na cílovou verzi kompilátoru až 3.5. Chcete-li to provést, zadejte "CompilerVersion" pro `name` atribut a "v3.5" pro `value` atribut. Je nutné před číslo verze s malým "v".  
  
 Můžete provést specifikace verze globální přidáním `<providerOption>` element pro rozhraní .NET Framework 2.0 souboru Machine.config nebo v kořenovém souboru Web.config. Pokud aktualizujete výchozí verze kompilátoru až 3.5 v souboru Machine.config, můžete ji změnit zpátky na 2.0 na základě jednotlivých aplikací pomocí `<providerOption>` element v konfiguračním souboru aplikace.  
  
 Implementátory zprostředkovatele codeDOM kódu může zpracovat vlastní možnosti tím, že poskytuje konstruktor, který přebírá `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zadat této verze 3.5 zprostředkovatele kódu C# má být použita.  
  
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
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
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
