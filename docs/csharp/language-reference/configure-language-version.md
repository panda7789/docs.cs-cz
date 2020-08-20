---
title: Jazyková verze jazyka c# – Průvodce jazyka C#
description: Přečtěte si informace o tom, jak je jazyková verze jazyka C# určena na základě vašeho projektu a z důvodů na základě této volby. Přečtěte si, jak přepsat výchozí nastavení ručně.
ms.custom: updateeachrelease
ms.date: 05/20/2020
ms.openlocfilehash: a27f3210f399f1bed190c18d778cf3824772d576
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656848"
---
# <a name="c-language-versioning"></a>Správa verzí jazyka C#

Nejnovější kompilátor C# určuje výchozí jazykovou verzi na základě cílových rozhraní architektury vašeho projektu nebo rozhraní. Visual Studio neposkytuje uživatelské rozhraní pro změnu hodnoty, ale můžete ho změnit úpravou souboru *csproj* . Volba výchozí zajistí, že používáte nejnovější verzi jazyka kompatibilní s vaší cílovou architekturou. Můžete využívat přístup k nejnovějším funkcím jazyka kompatibilním s cílem vašeho projektu. Tato výchozí volba také zajišťuje, že nebudete používat jazyk, který vyžaduje typy nebo běhové chování, které není v cílové architektuře k dispozici. Výběr jazykové verze, která je novější než výchozí, může způsobit, že bude obtížné diagnostikovat chyby při kompilaci a za běhu.

Pravidla v tomto článku se vztahují na kompilátor dodaný se sadou Visual Studio 2019 nebo .NET Core 3,0 SDK. Kompilátory jazyka C#, které jsou součástí instalace sady Visual Studio 2017 nebo starší verze .NET Core SDK v jazyce C# 7,0 ve výchozím nastavení.

C# 8,0 (a vyšší) jsou podporovány pouze v .NET Core 3. x a novějších verzích. Mnohé z nejnovějších funkcí vyžadují knihovnu a běhové funkce, které jsou představené v .NET Core 3. x:

- [Implementace výchozího rozhraní](../whats-new/csharp-8.md#default-interface-methods) vyžaduje nové funkce v .net Core 3,0 CLR.
- [Asynchronní datové proudy](../whats-new/csharp-8.md#asynchronous-streams) vyžadují nové typy <xref:System.IAsyncDisposable?displayProperty=nameWithType> , <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> a <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> .
- [Indexy a rozsahy](../whats-new/csharp-8.md#indices-and-ranges) vyžadují nové typy <xref:System.Index?displayProperty=nameWithType> a <xref:System.Range?displayProperty=nameWithType> .
- [Typy odkazů s možnou hodnotou null](../whats-new/csharp-8.md#nullable-reference-types) umožňují použití několika [atributů](attributes/nullable-analysis.md) k poskytnutí lepších upozornění. Tyto atributy se přidaly do .NET Core 3,0. Jiné cílové architektury nebyly opatřeny poznámkami žádné z těchto atributů. To znamená, že upozornění s možnou hodnotou null nemusí přesně odrážet možné problémy.

## <a name="defaults"></a>Ve výchozím nastavení

Kompilátor určuje výchozí hodnotu na základě těchto pravidel:

| Cílová architektura | verze | Výchozí verze jazyka C# |
|------------------|---------|-----------------------------|
| .NET Core        | 3.x     | C# 8.0                      |
| .NET Core        | 2.x     | C# 7.3                      |
| .NET Standard    | 2.1     | C# 8.0                      |
| .NET Standard    | 2.0     | C# 7.3                      |
| .NET Standard    | verze     | C# 7.3                      |
| .NET Framework   | Vše     | C# 7.3                      |

Když se váš projekt zaměřuje na architekturu verze Preview, která má odpovídající jazykovou verzi Preview, bude použit jazyk verze Preview. Nejnovější funkce v rámci této verze Preview můžete používat v jakémkoli prostředí, aniž by to ovlivnilo projekty, které cílí na vydanou verzi .NET Core.

## <a name="override-a-default"></a>Přepsat výchozí

Pokud je nutné explicitně zadat verzi C#, můžete to provést několika způsoby:

- Ručně upravte [soubor projektu](#edit-the-project-file).
- Nastaví jazykovou verzi [pro více projektů v podadresáři](#configure-multiple-projects).
- Nakonfigurujte [ `-langversion` možnost kompilátoru](compiler-options/langversion-compiler-option.md).

### <a name="edit-the-project-file"></a>Upravit soubor projektu

V souboru projektu můžete nastavit jazykovou verzi. Například pokud výslovně chcete získat přístup k funkcím verze Preview, přidejte prvek podobný tomuto:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Hodnota `preview` používá nejnovější verzi Preview jazyka C#, kterou podporuje kompilátor.

### <a name="configure-multiple-projects"></a>Konfigurace více projektů

Chcete-li konfigurovat více projektů, můžete vytvořit soubor **Directory. Build. props** , který obsahuje `<LangVersion>` element. Obvykle to provedete v adresáři řešení. Přidejte následující do souboru **Directory. Build. props** v adresáři řešení:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Sestavení ve všech podadresářích adresáře obsahujícího tento soubor budou používat verzi Preview jazyka C#. Další informace naleznete v článku o [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>Referenční informace o verzi jazyka C#

V následující tabulce jsou uvedeny všechny aktuální jazykové verze jazyka C#. Kompilátor nemusí nutně pochopit každou hodnotu, pokud je starší. Pokud instalujete .NET Core 3,0 nebo novější, máte k dispozici přístup k všechno uvedenému.

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> Otevřete [Developer Command Prompt pro sadu Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md)a spuštěním následujícího příkazu zobrazte seznam jazykových verzí, které jsou na vašem počítači k dispozici.
>
> ```CMD
> csc -langversion:?
> ```
>
> Po dotazování možnosti kompilace [-langversion –](compiler-options/langversion-compiler-option.md) bude vytištěna podobně jako v následujícím příkladu:
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0 (default)
> latestmajor
> preview
> latest
> ```
