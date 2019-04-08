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
ms.openlocfilehash: 34753d538ff37ac4ae621f653d47ac92ac6749a0
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674461"
---
# <a name="compiler-element"></a>\<Kompilátor > – Element

Určuje kompilátor – konfigurační atributy pro poskytovatele jazyka.

\<configuration Element> \<system.codedom Element> \<compilers Element> \<compiler> Element

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
|`compilerOptions`|Nepovinný atribut.<br /><br /> Určuje další argumenty kompilátoru specifické pro kompilaci. Hodnoty `compilerOptions` atribut jsou obvykle uvedeny v tématu možnosti kompilátoru pro kompilátor.|
|`extension`|Požadovaný atribut.<br /><br /> Poskytuje středníkem oddělený seznam přípon názvů souborů používá zdrojové soubory pro poskytovatele jazyka. Například "cs".|
|`language`|Požadovaný atribut.<br /><br /> Poskytuje středníkem oddělený seznam názvů jazyka podporována zprostředkovatelem jazyka. Například "C#; cs; csharp".|
|`type`|Požadovaný atribut.<br /><br /> Určuje název typu poskytovatele jazyka, včetně název sestavení obsahujícího implementaci zprostředkovatele. Název typu, musí splňovat požadavky definované v [zadání plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|
|`warningLevel`|Nepovinný atribut.<br /><br /> Určuje výchozí úroveň upozornění kompilátoru; Určuje úroveň, kdy zprostředkovatel jazyka zpracuje kompilace upozornění jako chyby.|

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<provideroption – > – Element](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|Určuje atributy verze kompilátoru poskytovatele jazyka.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<Konfigurace > – Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|[\<system.codedom> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.|
|[\<Kompilátory > – Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více `<compiler>` elementy.|

## <a name="remarks"></a>Poznámky

Každý `<compiler>` prvek určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele. Zprostředkovatel rozšiřuje <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> třídy pro konkrétní jazyk; `<compiler>` element definuje kompilátoru a nastavení generátor kódu pro jazyk zprostředkovatele.

Rozhraní .NET Framework definuje počáteční kompilátor – nastavení v konfiguračním souboru počítače (Machine.config). Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro nové <xref:System.CodeDom.Compiler.CodeDomProvider> implementace. Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> způsob, jak programově vytvářet výčty zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.

Kompilátor elementy v adresáři aplikace nebo souboru konfigurace webu můžete doplnit nebo přepsat nastavení v konfiguračním souboru počítače. Pokud více než jednu implementaci zprostředkovatele je nakonfigurovaný pro stejný název jazyka nebo stejnou příponu, poslední odpovídající konfigurace přepíše jakékoli předchozí nakonfigurované zprostředkovatelé pro tento jazyk název nebo příponu souboru.

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru počítače a konfigurační soubor aplikace.

## <a name="example"></a>Příklad

Následující příklad ukazuje prvek typické kompilátoru konfigurace:

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
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<Kompilátory > – Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- [Určení úplných názvů typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [Kompilátor – Element pro kompilátory compilation (schéma nastavení technologie ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
