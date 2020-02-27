---
title: C#jazykové verze – C# Průvodce
description: Přečtěte si o C# tom, jak je jazyková verze určena na základě vašeho projektu a z důvodů na základě této volby. Přečtěte si, jak přepsat výchozí nastavení ručně.
ms.date: 02/21/2020
ms.openlocfilehash: 2be76fdac471a7175b661d896b0da2910b3609f3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626761"
---
# <a name="c-language-versioning"></a>C#jazykové verze

Nejnovější C# kompilátor určuje výchozí jazykovou verzi v závislosti na cílovém rozhraní architektury vašeho projektu nebo rozhraní. Visual Studio neposkytuje uživatelské rozhraní pro změnu hodnoty, ale můžete ho změnit úpravou souboru *csproj* . Volba výchozí zajistí, že používáte nejnovější verzi jazyka kompatibilní s vaší cílovou architekturou. Můžete využívat přístup k nejnovějším funkcím jazyka kompatibilním s cílem vašeho projektu. Tato výchozí volba také zajišťuje, že nebudete používat jazyk, který vyžaduje typy nebo běhové chování, které není v cílové architektuře k dispozici. Výběr jazykové verze, která je novější než výchozí, může způsobit, že bude obtížné diagnostikovat chyby při kompilaci a za běhu.

C#8,0 (a vyšší) se podporuje jenom v .NET Core 3. x a novějších verzích. Mnohé z nejnovějších funkcí vyžadují knihovnu a běhové funkce, které jsou představené v .NET Core 3. x:

- Výchozí implementace člena rozhraní vyžaduje nové funkce v .NET Core 3,0 CLR.
- Asynchronní datové proudy vyžadují nové typy <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>a <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.
- Indexy a rozsahy vyžadují nové typy <xref:System.Index?displayProperty=nameWithType> a <xref:System.Range?displayProperty=nameWithType>.
- Typy odkazů s možnou hodnotou null umožňují použití několika [atributů](../nullable-attributes.md) k poskytnutí lepších upozornění. Tyto atributy se přidaly do .NET Core 3,0. Jiné cílové architektury nebyly opatřeny poznámkami žádné z těchto atributů. To znamená, že upozornění s možnou hodnotou null nemusí přesně odrážet možné problémy.

## <a name="defaults"></a>Ve výchozím nastavení

Kompilátor určuje výchozí hodnotu na základě těchto pravidel:

|Cílová architektura|version|C#výchozí verze jazyka|
|----------------|-------|---------------------------|
|.NET Core|3.x|C#8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C#8.0|
|.NET Standard|2.0|C# 7.3|
|.NET Standard|verze|C# 7.3|
|.NET Framework|all|C# 7.3|

Když se váš projekt zaměřuje na architekturu verze Preview, která má odpovídající jazykovou verzi Preview, bude použit jazyk verze Preview. Nejnovější funkce v rámci této verze Preview můžete používat v jakémkoli prostředí, aniž by to ovlivnilo projekty, které cílí na vydanou verzi .NET Core.

## <a name="override-a-default"></a>Přepsat výchozí

Pokud je nutné explicitně zadat C# verzi, můžete to provést několika způsoby:

- Ručně upravte [soubor projektu](#edit-the-project-file).
- Nastaví jazykovou verzi [pro více projektů v podadresáři](#configure-multiple-projects).
- Nakonfigurujte [možnost kompilátoru`-langversion`](compiler-options/langversion-compiler-option.md).

### <a name="edit-the-project-file"></a>Upravit soubor projektu

V souboru projektu můžete nastavit jazykovou verzi. Například pokud výslovně chcete získat přístup k funkcím verze Preview, přidejte prvek podobný tomuto:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Hodnota `preview` používá nejnovější dostupnou jazykovou verzi C# Preview, kterou podporuje kompilátor.

### <a name="configure-multiple-projects"></a>Konfigurace více projektů

Chcete-li konfigurovat více projektů, můžete vytvořit soubor **Directory. Build. props** , který obsahuje prvek `<LangVersion>`. Obvykle to provedete v adresáři řešení. Přidejte následující do souboru **Directory. Build. props** v adresáři řešení:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Sestavení ve všech podadresářích adresáře obsahujícího tento soubor budou používat verzi C# Preview. Další informace naleznete v článku o [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>C#Referenční informace o jazykové verzi

V následující tabulce jsou uvedeny všechny C# aktuální jazykové verze. Kompilátor nemusí nutně pochopit každou hodnotu, pokud je starší. Pokud instalujete .NET Core 3,0 nebo novější, máte k dispozici přístup k všechno uvedenému.

|Hodnota|Význam|
|------------|-------------|
|preview|Kompilátor přijímá všechny platné jazykové syntaxe z nejnovější verze Preview.|
|nejnovější|Kompilátor přijímá syntaxi z nejnovější vydané verze kompilátoru (včetně dílčí verze).|
|latestMajor|Kompilátor přijímá syntaxi z poslední vydané hlavní verze kompilátoru.|
|8.0|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 8,0 nebo nižší.|
|7.3|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,3 nebo nižší.|
|7.2|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,2 nebo nižší.|
|7.1|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,1 nebo nižší.|
|7|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,0 nebo nižší.|
|6|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 6,0 nebo nižší.|
|5|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 5,0 nebo nižší.|
|4|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 4,0 nebo nižší.|
|3|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 3,0 nebo nižší.|
|ISO-2|Kompilátor přijímá pouze syntaxi, která je obsažena v normě ISO C# /IEC 23270:2006 (2,0). |
|ISO-1|Kompilátor přijímá pouze syntaxi, která je obsažena v normě ISO C# /IEC 23270:2003 (1.0/1.2). |
