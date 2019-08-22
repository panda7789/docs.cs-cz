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
ms.openlocfilehash: 37f4d8c5eeacd82f8fc37179c478d026ca25f459
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664306"
---
# <a name="provideroption-element"></a>\<providerOption – element >
Určuje atributy verze kompilátoru pro poskytovatele jazyka.  
  
 \<> element konfigurace  
\<system.codedom Element>  
\<> element compilers  
\<> – element kompilátoru  
\<providerOption – element >  
  
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
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Element > Konfigurace](../configuration-element.md)|Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.|  
|[\<system.codedom> Element](system-codedom-element.md)|Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.|  
|[\<kompilátory > element](compilers-element.md)|Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více `<compiler>` prvků.|  
|[\<> – element kompilátoru](compiler-element.md)|Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.|  
  
## <a name="remarks"></a>Poznámky  
 V .NET Framework verze 3,5 mohou poskytovatelé kódu Code Document Object Model (CodeDOM) podporovat možnosti specifické pro poskytovatele pomocí `<providerOption>` elementu.  
  
 .NET Framework 3,5 obsahuje aktualizované .NET Framework 2,0 sestavení a poskytuje nová 3,5 verze, která obsahuje sestavení, která obsahují nové typy. Poskytovatelé C# kódu Microsoft a Visual Basic jsou obsaženi v sestaveních .NET Framework 2,0, ale byly aktualizovány pro podporu kompilátorů verze 3,5. Ve výchozím nastavení Aktualizovaní poskytovatelé kódu generují kód pro kompilátory verze 2,0. Pomocí `<providerOption>` elementu můžete změnit cílovou verzi kompilátoru na 3,5. Chcete-li to provést, zadejte "CompilerVersion" `name` pro atribut a "v 3.5" `value` pro atribut. Číslo verze se musí nacházet s malým písmenem "v".  
  
 Specifikaci verze můžete vytvořit globální přidáním `<providerOption>` elementu do souboru .NET Framework 2,0 Machine. config nebo root web. config. Pokud aktualizujete výchozí verzi kompilátoru na 3,5 v souboru Machine. config, můžete ji změnit na 2,0 na základě jednotlivých aplikací pomocí `<providerOption>` elementu v konfiguračním souboru aplikace.  
  
 Implementátori poskytovatele kódu CodeDOM mohou zpracovat vlastní možnosti, a to poskytnutím konstruktoru, `providerOptions` který přijímá parametr <xref:System.Collections.Generic.IDictionary%602>typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že by měla být použita C# verze 3,5 poskytovatele kódu.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schéma konfiguračního souboru](../index.md)
- [\<kompilátory > element](compilers-element.md)
- [Určení úplných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [Element Compiler pro kompilátory pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
