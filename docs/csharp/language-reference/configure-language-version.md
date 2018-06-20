---
title: Vyberte C# verzi jazyka – průvodce v C#
description: Nastavení kompilátoru k provedení ověření syntaxe pomocí verze konkrétní kompilátoru
ms.date: 05/24/2018
ms.openlocfilehash: 9b91e62168ced0f373e1a55def8b279dc64833d8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208353"
---
# <a name="select-the-c-language-version"></a>Vyberte verzi jazyka C#

Kompilátor jazyka C# výchozí nejnovější hlavní verzi jazyka, který byl vydán. Můžete se rozhodnout zkompilovat všechny projekt pomocí nové verze bodu jazyka. Výběr novější verze jazyka, který umožňuje svým projektem zajistíte pomocí nejnovějších funkcí jazyka. V jiných scénářích musíte ověřit, že projektu zkompiluje řádně při použití starší verze jazyka.

Tato funkce oddělí rozhodnutí pro instalaci nové verze sady SDK a nástroje ve vašem vývojovém prostředí z rozhodnutí o začlenit nové jazykové funkce v projektu. Nejnovější sady SDK a nástrojů můžete nainstalovat na počítači pro sestavení. Každý projekt, lze nakonfigurovat k využívání na konkrétní verzi jazyka pro jeho sestavení.

Chcete-li nastavit jazyková verze několika způsoby:

- Závisí na [rychlé akce Visual Studio](#visual-studio-quick-action).
- Nastavení jazykové verze [rozhraní Visual Studia](#set-the-language-version-in-visual-studio).
- Ručně upravit, pokud vaše [ **.csproj** soubor](#edit-the-csproj-file).
- Nastavení jazykové verze [pro více projektů v podadresáři](#configure-multiple-projects).
- Konfigurace [ `-langversion` – možnost kompilátoru](#set-the-langversion-compiler-option).

## <a name="visual-studio-quick-action"></a>Visual Studio rychlé akce

Visual Studio vám pomůže určit jazyková verze, které potřebujete. Pokud použijete jazyk funkce, která není k dispozici pro aktuálně nakonfigurované verze, Visual Studio zobrazí potenciální potíže se aktualizovat jazyková verze pro projekt.

## <a name="set-the-language-version-in-visual-studio"></a>Nastavení jazykové verze v sadě Visual Studio

Verze můžete nastavit v sadě Visual Studio. Klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení a vyberte **vlastnosti**. Vyberte **sestavení** a vyberte **Upřesnit** tlačítko. V rozevíracím seznamu vyberte verzi. Následující obrázek ukazuje nastavení "posledního":

![Snímek obrazovky nastavení pokročilé sestavení, kde můžete určit jazyková verze](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> Pokud používáte Visual Studio IDE aktualizace souborů csproj, rozhraní IDE vytvoří samostatné uzly pro každou konfiguraci sestavení. Budete obvykle nastavíte hodnotu stejné ve všech konfigurací sestavení, ale je potřeba explicitně nastaven pro každou konfiguraci sestavení, nebo vyberte "Všechny konfigurace" při změně tohoto nastavení. V souboru csproj se zobrazí následující:
>
>```xml
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
>  <LangVersion>latest</LangVersion>
></PropertyGroup>
>
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
>  <LangVersion>latest</LangVersion>
> </PropertyGroup>
> ```
>

## <a name="edit-the-csproj-file"></a>Upravte soubor csproj

Jazyková verze můžete nastavit v vaše **.csproj** souboru. Přidáte element takto:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Hodnota `latest` používá nejnovější dílčí verzi jazyka C#. Platné hodnoty jsou:

|Hodnota|Význam|
|------------|-------------|
|default|Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější hlavní verzi, která může podporovat.|
|ISO-1|Kompilátor přijímá pouze syntaxi, která je součástí ISO/IEC 23270: 2003 C# (1.0 nebo 1.2) |
|ISO-2|Kompilátor přijímá pouze syntaxi, která je součástí ISO/IEC 23270: 2006 C# (2.0) |
|3|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 3.0 nebo nižší.|
|4|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 4.0 nebo nižší.|
|5|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 5.0 nebo nižší.|
|6|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 6.0 nebo nižší.|
|7|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.0 nebo nižší.|
|7.1|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.1 nebo nižší.|
|7.2|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.2 nebo nižší.|
|7.3|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.3 nebo nižší.|
|Nejnovější|Kompilátor přijímá všechny platné syntaxe jazyka, jakou může podporovat.|

Speciální řetězce `default` a `latest` odkazující na nejnovější hlavní (C# 7.0) a (C# 7.3) jazyk podverze nainstalován v počítači sestavení v uvedeném pořadí.

## <a name="configure-multiple-projects"></a>Konfigurace více projektů

Můžete vytvořit **Directory.build.props** soubor, který obsahuje `<LangVersion>` elementu, který chcete nakonfigurovat několik adresářů. Obvykle to uděláte ve vašem adresáři řešení. Přidejte následující **Directory.build.props** soubor v adresáři řešení:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

Nyní sestavení v každé podadresáři adresář obsahující tento soubor použije verze 7.3 syntaxe jazyka C#. Další informace najdete v článku na [přizpůsobit buildu](/visualstudio/msbuild/customize-your-build).

## <a name="set-the-langversion-compiler-option"></a>Nastavte langversion – možnost kompilátoru

Můžete použít `-langversion` možnost příkazového řádku. Další informace najdete v článku na [- langversion](../language-reference/compiler-options/langversion-compiler-option.md) – možnost kompilátoru. Zobrazí se seznam platných hodnot zadáním `csc -langversion:?`.
