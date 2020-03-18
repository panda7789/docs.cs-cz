---
title: Jazyková správa jazyka C# – průvodce c#
description: Zjistěte, jak je určena jazyková verze jazyka C# na základě projektu a důvody této volby. Přečtěte si, jak ručně přepsat výchozí nastavení.
ms.date: 02/21/2020
ms.openlocfilehash: ef7275aad7638f52ecbfca1dfbdb962ae242fb48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399537"
---
# <a name="c-language-versioning"></a>Správa jazykových verzí jazyka C#

Nejnovější kompilátor Jazyka C# určuje výchozí jazykovou verzi na základě cílového rozhraní nebo rozhraní vašeho projektu. Visual Studio neposkytuje ui změnit hodnotu, ale můžete ji změnit úpravou souboru *csproj.* Volba výchozí zajišťuje, že používáte nejnovější jazykovou verzi kompatibilní s cílovým rozhraním. Můžete těžit z přístupu k nejnovějším jazykovým funkcím kompatibilním s cílem projektu. Tato výchozí volba také zajišťuje, že nepoužíváte jazyk, který vyžaduje typy nebo chování za běhu, které není k dispozici v cílovém rámci. Výběr jazykové verze novější než výchozí může způsobit těžko diagnostikovat chyby kompilace a běhu.

Pravidla v tomto článku platí pro kompilátor dodaný s Visual Studio 2019 nebo .NET Core 3.0 SDK. Kompilátory Jazyka C#, které jsou součástí instalace sady Visual Studio 2017 nebo starší verze sady .NET Core SDK, ve výchozím nastavení cílí na c# 7.0.

C# 8.0 (a vyšší) je podporována pouze na .NET Core 3.x a novější verze. Mnoho nejnovějších funkcí vyžaduje knihovnu a funkce runtime zavedené v rozhraní .NET Core 3.x:

- Výchozí implementace člena rozhraní vyžaduje nové funkce v clru .NET Core 3.0.
- Asynchronní datové proudy <xref:System.IAsyncDisposable?displayProperty=nameWithType> <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>vyžadují <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>nové typy , a .
- Indexy a rozsahy vyžadují <xref:System.Index?displayProperty=nameWithType> <xref:System.Range?displayProperty=nameWithType>nové typy a .
- Typy odkazů s možnou hodnotou Null využívají několik [atributů](../nullable-attributes.md) k zajištění lepších upozornění. Tyto atributy byly přidány do rozhraní .NET Core 3.0. Ostatní cílové rámce nebyly anotovány s některou z těchto atributů. To znamená, že upozornění, která lze zrušit, nemusí přesně odrážet potenciální problémy.

## <a name="defaults"></a>Ve výchozím nastavení

Kompilátor určuje výchozí nastavení na základě těchto pravidel:

|Cílový rámec|version|Výchozí jazyková verze jazyka C#|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2.0|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|.NET Framework|Vše|C# 7.3|

Pokud váš projekt cílí na rozhraní preview, které má odpovídající jazykovou verzi náhledu, použije se jazyková verze ve verzi preview. Nejnovější funkce s tímto náhledem se používají v libovolném prostředí, aniž by to ovlivnilo projekty, které cílí na vydanou verzi .NET Core.

## <a name="override-a-default"></a>Přepsat výchozí hodnotu

Pokud je nutné zadat verzi jazyka C# explicitně, můžete tak učinit několika způsoby:

- Ručně upravte [soubor projektu](#edit-the-project-file).
- Nastavte jazykovou verzi [pro více projektů v podadresáři](#configure-multiple-projects).
- Nakonfigurujte [ `-langversion` možnost kompilátoru](compiler-options/langversion-compiler-option.md).

### <a name="edit-the-project-file"></a>Úprava souboru projektu

Jazykovou verzi můžete nastavit v souboru projektu. Pokud například chcete explicitně získat přístup k funkcím náhledu, přidejte prvek, jako je tento:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Hodnota `preview` používá nejnovější dostupnou verzi jazyka jazyka Preview C#, kterou kompilátor podporuje.

### <a name="configure-multiple-projects"></a>Konfigurace více projektů

Chcete-li nakonfigurovat více projektů, můžete vytvořit soubor **Directory.Build.props,** který obsahuje `<LangVersion>` prvek. Obvykle to uděláte v adresáři řešení. Do souboru **Directory.Build.props** v adresáři řešení přidejte následující:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Vytvoří ve všech podadresářích adresáře obsahující tento soubor bude používat verzi náhledu C#. Další informace naleznete v článku [Přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>Odkaz na jazykovou verzi jazyka C#

V následující tabulce jsou uvedeny všechny aktuální jazykové verze jazyka C#. Kompilátor nemusí nutně pochopit každou hodnotu, pokud je starší. Pokud nainstalujete rozhraní .NET Core 3.0 nebo novější, máte přístup ke všem upsaným.

|Hodnota|Význam|
|------------|-------------|
|Náhled|Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější verze preview.|
|nejnovější|Kompilátor přijímá syntaxi z nejnovější vydané verze kompilátoru (včetně dílčí verze).|
|nejnovějšíMajor|Kompilátor přijímá syntaxi z nejnovější vydané hlavní verze kompilátoru.|
|8.0|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 8.0 nebo nižší.|
|7.3|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.3 nebo nižší.|
|7.2|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.2 nebo nižší.|
|7.1|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.1 nebo nižší.|
|7|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.0 nebo nižší.|
|6|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 6.0 nebo nižší.|
|5|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 5.0 nebo nižší.|
|4|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 4.0 nebo nižší.|
|3|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 3.0 nebo nižší.|
|ISO-2|Kompilátor přijímá pouze syntaxi, která je součástí ISO/IEC 23270:2006 C# (2.0). |
|ISO-1|Kompilátor přijímá pouze syntaxi, která je součástí ISO/IEC 23270:2003 C# (1.0/1.2). |
