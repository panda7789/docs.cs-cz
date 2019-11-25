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
ms.openlocfilehash: a6718173e84ecffc4ba0641f6e865e777aa6b1a4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088677"
---
# <a name="provideroption-element"></a>\<element > providerOption
Určuje atributy verze kompilátoru pro poskytovatele jazyka.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. codedom >** ](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kompilátory**](compilers-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kompilátoru >** ](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<providerOption >**

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
|[> element konfigurace \<](../configuration-element.md)|Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.|  
|[\<> element System. CodeDom](system-codedom-element.md)|Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.|  
|[> elementu \<kompilátorů](compilers-element.md)|Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více `<compiler>` prvků.|  
|[\<element > kompilátoru](compiler-element.md)|Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.|  
  
## <a name="remarks"></a>Poznámky  
 V .NET Framework verze 3,5 mohou poskytovatelé kódu Code Document Object Model (CodeDOM) podporovat možnosti specifické pro poskytovatele pomocí elementu `<providerOption>`.  
  
 .NET Framework 3,5 obsahuje aktualizované .NET Framework 2,0 sestavení a poskytuje nová 3,5 verze, která obsahuje sestavení, která obsahují nové typy. Poskytovatelé C# kódu Microsoft a Visual Basic jsou obsaženi v sestaveních .NET Framework 2,0, ale byly aktualizovány pro podporu kompilátorů verze 3,5. Ve výchozím nastavení Aktualizovaní poskytovatelé kódu generují kód pro kompilátory verze 2,0. Pomocí elementu `<providerOption>` můžete změnit cílovou verzi kompilátoru na 3,5. To provedete tak, že zadáte "CompilerVersion" pro atribut `name` a "v 3.5" pro atribut `value`. Číslo verze se musí nacházet s malým písmenem "v".  
  
 Specifikaci verze můžete vytvořit globální přidáním prvku `<providerOption>` do souboru .NET Framework 2,0 Machine. config nebo do kořenového souboru Web. config. Pokud aktualizujete výchozí verzi kompilátoru na 3,5 v souboru Machine. config, můžete ji změnit zpět na 2,0 pro jednotlivé aplikace pomocí elementu `<providerOption>` v konfiguračním souboru aplikace.  
  
 Implementátori poskytovatele kódu CodeDOM mohou zpracovat vlastní možnosti, a to poskytnutím konstruktoru, který přebírá `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602>.  
  
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
- [> elementu \<kompilátorů](compilers-element.md)
- [Určení úplných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [Element Compiler pro kompilátory pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
