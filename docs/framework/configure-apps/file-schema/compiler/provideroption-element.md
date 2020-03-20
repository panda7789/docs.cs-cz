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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155398"
---
# <a name="provideroption-element"></a>\<providerOption> Element
Určuje atributy verze kompilátoru pro poskytovatele jazyka.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>kompilátorů**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>kompilátoru**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>možnosti providerOption**

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
|`name`|Požadovaný atribut.<br /><br /> Určuje název této možnosti. například "CompilerVersion".|  
|`value`|Požadovaný atribut.<br /><br /> Určuje hodnotu pro tuto možnost; například "v3.5".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<konfigurace> Element](../configuration-element.md)|Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.|  
|[\<system.codedom> Element](system-codedom-element.md)|Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.|  
|[\<kompilátory> Element](compilers-element.md)|Kontejner pro konfigurační prvky kompilátoru; obsahuje nula `<compiler>` nebo více prvků.|  
|[\<> element kompilátoru](compiler-element.md)|Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.|  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 3.5 mohou zprostředkovatelé kódu Code Document Object Model `<providerOption>` (CodeDOM) podporovat možnosti specifické pro zprostředkovatele pomocí prvku.  
  
 Rozhraní .NET Framework 3.5 obsahuje aktualizovaná sestavení rozhraní .NET Framework 2.0 a poskytuje nová sestavení verze 3.5, která obsahují nové typy. Zprostředkovatelé kódu jazyka Microsoft C# a Visual Basic jsou obsaženy v sestaveních rozhraní .NET Framework 2.0, ale byly aktualizovány tak, aby podporovaly kompilátory verze 3.5. Ve výchozím nastavení poskytovatelé aktualizovaného kódu generují kód pro kompilátory verze 2.0. `<providerOption>` Prvek můžete použít ke změně verze cílového kompilátoru na 3.5. Chcete-li to provést, zadejte `name` "CompilerVersion" pro atribut `value` a "v3.5" pro atribut. Před číslem verze musíte předcházet s malou písmena "v".  
  
 Specifikace verze můžete vytvořit jako `<providerOption>` globální přidáním prvku do souboru .NET Framework 2.0 Machine.config nebo root Web.config. Pokud aktualizujete výchozí verzi kompilátoru na 3.5 v souboru Machine.config, můžete ji změnit zpět `<providerOption>` na 2.0 pro aplikaci pomocí prvku v konfiguračním souboru aplikace.  
  
 Implementátoři zprostředkovatele kódu CodeDOM mohou zpracovávat vlastní `providerOptions` možnosti <xref:System.Collections.Generic.IDictionary%602>poskytnutím konstruktoru, který přebírá parametr typu .  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že by měla být použita verze 3.5 zprostředkovatele kódu Jazyka C#.  
  
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
- [\<kompilátory> Element](compilers-element.md)
- [Určení úplných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [Element kompilátoru pro kompilátory pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
