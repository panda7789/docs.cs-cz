---
title: Vyberte C# jazykovou verzi - C# Průvodce
description: Konfigurace kompilátor provést ověření syntaxe pomocí specifické verzi kompilátoru
ms.date: 02/28/2019
ms.openlocfilehash: feb3e51a107f9830071b55c7985f202edc842f4a
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480739"
---
# <a name="select-the-c-language-version"></a>Vyberte C# jazykovou verzi

C# Kompilátor Určuje výchozí jazykovou verzi na základě cílové rozhraní projektu nebo rozhraní. Když váš projekt cílí na verzi preview rozhraní, které obsahuje odpovídající jazykovou verzi preview, je jazyková verze používá jazykovou verzi preview. Projekt není zacílená ve verzi preview rozhraní, jazykové verzi použít při nejnovější dílčí verzi.

Například během období preview pro .NET Core 3.0, libovolný projekt, který cílí `netcoreapp3.0` nebo `netstandard2.1` (ve verzi preview) se používají C# 8.0 – language (také ve verzi preview). Cílení na všechny vydané verzi použije C# 7.3 (nejnovější vydaná verze). Toto chování znamená, že každý projekt cílí na rozhraní .NET Framework bude používat nejnovější verzi (C# 7.3). 

Tato funkce odděluje rozhodnutí pro instalaci nové verze sady SDK a nástroje ve vašem vývojovém prostředí od rozhodnutí začlenit nové funkce jazyků v projektu. Nejnovější sady SDK a nástroje můžete nainstalovat na počítače pro sestavení. Každý projekt se dá použít konkrétní verzi jazyka pro jeho sestavení. Výchozí chování znamená, že všechny jazykové funkce, které využívají nové typy nebo nové chování modulu CLR jsou povolené jenom v případě, že projekty jsou určené pro tyto architektury.

Výchozí chování můžete přepsat zadáním jazykovou verzi. Existuje několik způsobů, jak nastavit jazykovou verzi:

- Spolehněte se na [sady Visual Studio rychle reagovat](#visual-studio-quick-action).
- Nastavení jazykové verze v [Visual Studio UI](#set-the-language-version-in-visual-studio).
- Ručně upravit vaše [ **.csproj** souboru](#edit-the-csproj-file).
- Nastavit jazykovou verzi [pro více projektů v podadresáři](#configure-multiple-projects).
- Konfigurace [ `-langversion` – možnost kompilátoru](#set-the-langversion-compiler-option).

## <a name="visual-studio-quick-action"></a>Rychlé akce pro Visual Studio

Visual Studio vám pomůže určit jazykové verze, které potřebujete. Pokud používáte jazyk funkce, která není k dispozici pro aktuálně nakonfigurovaná verze, sada Visual Studio zobrazí potenciální opravu a aktualizovat verzi jazyka pro projekt.

## <a name="set-the-language-version-in-visual-studio"></a>Nastavení jazykové verze v sadě Visual Studio

Nastavte verzi v sadě Visual Studio. Klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení a vyberte **vlastnosti**. Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko. V rozevíracím seznamu vyberte verzi. Následující obrázek ukazuje "posledního" nastavení:

![Snímek obrazovky nastavení rozšířené sestavení, ve kterém můžete zadat jazykovou verzi](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> Je-li aktualizovat soubory csproj pomocí rozhraní IDE sady Visual Studio, rozhraní IDE vytvoří samostatné uzly pro každou konfiguraci sestavení. Budete obvykle nastavena hodnotu stejné ve všech konfiguracích sestavení, ale je potřeba explicitně nastavena pro každou konfiguraci sestavení, nebo vyberte "Všechny konfigurace", když je toto nastavení změnit. V souboru csproj se zobrazí následující:
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

Můžete nastavit jazykovou verzi vašeho **.csproj** souboru. Přidáte element takto:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Hodnota `latest` používá nejnovější dílčí verzi C# jazyka. Platné hodnoty jsou:

|Value|Význam|
|------------|-------------|
|preview|Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější verze preview.|
|nejnovější|Kompilátor přijímá syntaxi z nejnovější vydanou verzi kompilátoru (včetně vedlejší verze aktualizace).|
|latestMajor|Kompilátor přijímá syntaxi z nejnovější vydanou hlavní verzi kompilátoru.|
|8.0|Kompilátor přijímá pouze syntaxi, která je součástí C# 8.0 nebo nižší.|
|7.3|Kompilátor přijímá pouze syntaxi, která je součástí C# 7.3 nebo nižší.|
|7.2|Kompilátor přijímá pouze syntaxi, která je součástí C# 7.2 nebo nižší.|
|7.1|Kompilátor přijímá pouze syntaxi, která je součástí C# 7.1 nebo nižší.|
|7|Kompilátor přijímá pouze syntaxi, která je součástí C# 7.0 nebo nižší.|
|6|Kompilátor přijímá pouze syntaxi, která je součástí C# 6.0 nebo nižší.|
|5|Kompilátor přijímá pouze syntaxi, která je součástí C# 5.0 nebo nižší.|
|4|Kompilátor přijímá pouze syntaxi, která je součástí C# 4.0 nebo nižší.|
|3|Kompilátor přijímá pouze syntaxi, která je součástí C# 3.0 nebo nižší.|
|ISO-2|Kompilátor přijímá pouze syntaxi, která je součástí 23270: ISO/IEC 2006 C# (2.0) |
|ISO-1|Kompilátor přijímá pouze syntaxi, která je součástí 23270: ISO/IEC 2003 C# (1.0 nebo 1.2) |

## <a name="configure-multiple-projects"></a>Konfigurace více projektů

Můžete vytvořit **Directory.Build.props** soubor, který obsahuje `<LangVersion>` prvek, který chcete nakonfigurovat více adresářů. Obvykle to uděláte ve svém adresáři řešení. Přidejte následující text do **Directory.Build.props** soubor v adresáři řešení:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

Nyní, bude sestavení všechny podadresáře adresáře, který obsahuje tento soubor používají C# verzi 7.3 syntaxe. Další informace najdete v článku na [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).

## <a name="set-the-langversion-compiler-option"></a>Nastavte langversion – možnost kompilátoru

Můžete použít `-langversion` možnost příkazového řádku. Další informace najdete v článku na [- langversion](../language-reference/compiler-options/langversion-compiler-option.md) – možnost kompilátoru. Seznam platných hodnot najdete tak, že zadáte `csc -langversion:?`.
