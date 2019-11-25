---
title: Element <compiler>
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: 46676f25597f85596598d6f67c98930971cb0447
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088060"
---
# <a name="compiler-element"></a>\<element > kompilátoru

Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. codedom >** ](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kompilátory**](compilers-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<kompilátoru >**

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
|`compilerOptions`|Nepovinný atribut.<br /><br /> Určuje další argumenty specifické pro kompilátor pro kompilaci. Hodnoty atributu `compilerOptions` jsou obvykle uvedeny v tématu Možnosti kompilátoru pro kompilátor.|
|`extension`|Požadovaný atribut.<br /><br /> Poskytuje středníkem oddělený seznam přípon názvů souborů, které jsou používány zdrojovými soubory pro poskytovatele jazyka. Například ". cs".|
|`language`|Požadovaný atribut.<br /><br /> Nabízí středníkem oddělený seznam názvů jazyků podporovaných poskytovatelem jazyka. Například "c#; cs; CSharp".|
|`type`|Požadovaný atribut.<br /><br /> Určuje název typu poskytovatele jazyka, včetně názvu sestavení, které obsahuje implementaci poskytovatele. Název typu musí splňovat požadavky definované v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|
|`warningLevel`|Nepovinný atribut.<br /><br /> Určuje výchozí úroveň upozornění kompilátoru; Určuje úroveň, na které poskytovatel jazyka považuje upozornění kompilace za chyby.|

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<element > providerOption](provideroption-element.md)|Určuje atributy verze kompilátoru pro poskytovatele jazyka.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[> element konfigurace \<](../configuration-element.md)|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|[\<> element System. CodeDom](system-codedom-element.md)|Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.|
|[> elementu \<kompilátorů](compilers-element.md)|Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více `<compiler>` prvků.|

## <a name="remarks"></a>Poznámky

Každý prvek `<compiler>` určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka. Zprostředkovatel rozšiřuje třídu <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> pro konkrétní jazyk. element `<compiler>` definuje kompilátor a nastavení generátoru kódu pro poskytovatele jazyka.

.NET Framework definuje počáteční nastavení kompilátoru v konfiguračním souboru počítače (Machine. config). Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení pro novou implementaci <xref:System.CodeDom.Compiler.CodeDomProvider>. Použijte metodu <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> k programovému vytvoření výčtu poskytovatele jazyka a nastavení konfigurace kompilátoru v počítači.

Prvky kompilátoru v souboru aplikace nebo webové konfigurace mohou doplnit nebo přepsat nastavení v konfiguračním souboru počítače. Pokud je pro stejný název jazyka nebo stejnou příponu souboru nakonfigurovaná víc než jedna implementace zprostředkovatele, přepíše poslední odpovídající konfigurace všechny předchozí nakonfigurované zprostředkovatele pro daný název jazyka nebo příponu souboru.

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.

## <a name="example"></a>Příklad

Následující příklad ilustruje typický prvek konfigurace kompilátoru:

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

## <a name="see-also"></a>Viz také:

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schéma konfiguračního souboru](../index.md)
- [> elementu \<kompilátorů](compilers-element.md)
- [Určení úplných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [Element Compiler pro kompilátory pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
