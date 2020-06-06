---
title: Element <providerOption>
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155398"
---
# <a name="provideroption-element"></a>Element \<providerOption>
Určuje atributy verze kompilátoru pro poskytovatele jazyka.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

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
|`name`|Požadovaný atribut.<br /><br /> Určuje název možnosti. například "CompilerVersion".|  
|`value`|Požadovaný atribut.<br /><br /> Určuje hodnotu možnosti; například "v 3.5".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<configuration>Objekt](../configuration-element.md)|Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.|  
|[\<system.codedom>Objekt](system-codedom-element.md)|Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.|  
|[\<compilers>Objekt](compilers-element.md)|Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více `<compiler>` prvků.|  
|[\<compiler>Objekt](compiler-element.md)|Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.|  
  
## <a name="remarks"></a>Poznámky  
 V .NET Framework verze 3,5 mohou poskytovatelé kódu Code Document Object Model (CodeDOM) podporovat možnosti specifické pro poskytovatele pomocí `<providerOption>` elementu.  
  
 .NET Framework 3,5 obsahuje aktualizované .NET Framework 2,0 sestavení a poskytuje nová 3,5 verze, která obsahuje sestavení, která obsahují nové typy. Poskytovatelé kódu Microsoft C# a Visual Basic jsou obsaženi v sestaveních .NET Framework 2,0, ale byly aktualizovány pro podporu kompilátorů verze 3,5. Ve výchozím nastavení Aktualizovaní poskytovatelé kódu generují kód pro kompilátory verze 2,0. Pomocí `<providerOption>` elementu můžete změnit cílovou verzi kompilátoru na 3,5. Chcete-li to provést, zadejte "CompilerVersion" pro `name` atribut a "v 3.5" pro `value` atribut. Číslo verze se musí nacházet s malým písmenem "v".  
  
 Specifikaci verze můžete vytvořit globální přidáním `<providerOption>` elementu do souboru .NET Framework 2,0 Machine. config nebo root web. config. Pokud aktualizujete výchozí verzi kompilátoru na 3,5 v souboru Machine. config, můžete ji změnit na 2,0 na základě jednotlivých aplikací pomocí `<providerOption>` elementu v konfiguračním souboru aplikace.  
  
 Implementátori poskytovatele kódu CodeDOM mohou zpracovat vlastní možnosti, a to poskytnutím konstruktoru, který přijímá `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602> .  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že by měla být použita verze 3,5 poskytovatele kódu jazyka C#.  
  
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

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schéma konfiguračního souboru](../index.md)
- [\<compilers>Objekt](compilers-element.md)
- [Určení úplných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [Element Compiler pro kompilátory pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
