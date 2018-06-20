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
# <a name="select-the-c-language-version"></a><span data-ttu-id="420fb-103">Vyberte verzi jazyka C#</span><span class="sxs-lookup"><span data-stu-id="420fb-103">Select the C# language version</span></span>

<span data-ttu-id="420fb-104">Kompilátor jazyka C# výchozí nejnovější hlavní verzi jazyka, který byl vydán.</span><span class="sxs-lookup"><span data-stu-id="420fb-104">The C# compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="420fb-105">Můžete se rozhodnout zkompilovat všechny projekt pomocí nové verze bodu jazyka.</span><span class="sxs-lookup"><span data-stu-id="420fb-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="420fb-106">Výběr novější verze jazyka, který umožňuje svým projektem zajistíte pomocí nejnovějších funkcí jazyka.</span><span class="sxs-lookup"><span data-stu-id="420fb-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="420fb-107">V jiných scénářích musíte ověřit, že projektu zkompiluje řádně při použití starší verze jazyka.</span><span class="sxs-lookup"><span data-stu-id="420fb-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="420fb-108">Tato funkce oddělí rozhodnutí pro instalaci nové verze sady SDK a nástroje ve vašem vývojovém prostředí z rozhodnutí o začlenit nové jazykové funkce v projektu.</span><span class="sxs-lookup"><span data-stu-id="420fb-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="420fb-109">Nejnovější sady SDK a nástrojů můžete nainstalovat na počítači pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="420fb-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="420fb-110">Každý projekt, lze nakonfigurovat k využívání na konkrétní verzi jazyka pro jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="420fb-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="420fb-111">Chcete-li nastavit jazyková verze několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="420fb-111">There are several ways to set the language version:</span></span>

- <span data-ttu-id="420fb-112">Závisí na [rychlé akce Visual Studio](#visual-studio-quick-action).</span><span class="sxs-lookup"><span data-stu-id="420fb-112">Rely on a [Visual Studio quick action](#visual-studio-quick-action).</span></span>
- <span data-ttu-id="420fb-113">Nastavení jazykové verze [rozhraní Visual Studia](#set-the-language-version-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="420fb-113">Set the language version in the [Visual Studio UI](#set-the-language-version-in-visual-studio).</span></span>
- <span data-ttu-id="420fb-114">Ručně upravit, pokud vaše [ **.csproj** soubor](#edit-the-csproj-file).</span><span class="sxs-lookup"><span data-stu-id="420fb-114">Manually edit your [**.csproj** file](#edit-the-csproj-file).</span></span>
- <span data-ttu-id="420fb-115">Nastavení jazykové verze [pro více projektů v podadresáři](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="420fb-115">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="420fb-116">Konfigurace [ `-langversion` – možnost kompilátoru](#set-the-langversion-compiler-option).</span><span class="sxs-lookup"><span data-stu-id="420fb-116">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option).</span></span>

## <a name="visual-studio-quick-action"></a><span data-ttu-id="420fb-117">Visual Studio rychlé akce</span><span class="sxs-lookup"><span data-stu-id="420fb-117">Visual Studio quick action</span></span>

<span data-ttu-id="420fb-118">Visual Studio vám pomůže určit jazyková verze, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="420fb-118">Visual Studio helps you determine the language version you need.</span></span> <span data-ttu-id="420fb-119">Pokud použijete jazyk funkce, která není k dispozici pro aktuálně nakonfigurované verze, Visual Studio zobrazí potenciální potíže se aktualizovat jazyková verze pro projekt.</span><span class="sxs-lookup"><span data-stu-id="420fb-119">If you use a language feature that is not available for the currently configured version, Visual Studio shows a potential fix to update the language version for the project.</span></span>

## <a name="set-the-language-version-in-visual-studio"></a><span data-ttu-id="420fb-120">Nastavení jazykové verze v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="420fb-120">Set the language version in Visual Studio</span></span>

<span data-ttu-id="420fb-121">Verze můžete nastavit v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="420fb-121">You can set the version in Visual Studio.</span></span> <span data-ttu-id="420fb-122">Klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="420fb-122">Right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="420fb-123">Vyberte **sestavení** a vyberte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="420fb-123">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="420fb-124">V rozevíracím seznamu vyberte verzi.</span><span class="sxs-lookup"><span data-stu-id="420fb-124">In the dropdown, select the version.</span></span> <span data-ttu-id="420fb-125">Následující obrázek ukazuje nastavení "posledního":</span><span class="sxs-lookup"><span data-stu-id="420fb-125">The following image shows the "latest" setting:</span></span>

![Snímek obrazovky nastavení pokročilé sestavení, kde můžete určit jazyková verze](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> <span data-ttu-id="420fb-127">Pokud používáte Visual Studio IDE aktualizace souborů csproj, rozhraní IDE vytvoří samostatné uzly pro každou konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="420fb-127">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="420fb-128">Budete obvykle nastavíte hodnotu stejné ve všech konfigurací sestavení, ale je potřeba explicitně nastaven pro každou konfiguraci sestavení, nebo vyberte "Všechny konfigurace" při změně tohoto nastavení.</span><span class="sxs-lookup"><span data-stu-id="420fb-128">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="420fb-129">V souboru csproj se zobrazí následující:</span><span class="sxs-lookup"><span data-stu-id="420fb-129">You'll see the following in your csproj file:</span></span>
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

## <a name="edit-the-csproj-file"></a><span data-ttu-id="420fb-130">Upravte soubor csproj</span><span class="sxs-lookup"><span data-stu-id="420fb-130">Edit the csproj file</span></span>

<span data-ttu-id="420fb-131">Jazyková verze můžete nastavit v vaše **.csproj** souboru.</span><span class="sxs-lookup"><span data-stu-id="420fb-131">You can set the language version in your **.csproj** file.</span></span> <span data-ttu-id="420fb-132">Přidáte element takto:</span><span class="sxs-lookup"><span data-stu-id="420fb-132">Add an element like the following:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="420fb-133">Hodnota `latest` používá nejnovější dílčí verzi jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="420fb-133">The value `latest` uses the latest minor version of the C# language.</span></span> <span data-ttu-id="420fb-134">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="420fb-134">Valid values are:</span></span>

|<span data-ttu-id="420fb-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="420fb-135">Value</span></span>|<span data-ttu-id="420fb-136">Význam</span><span class="sxs-lookup"><span data-stu-id="420fb-136">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="420fb-137">default</span><span class="sxs-lookup"><span data-stu-id="420fb-137">default</span></span>|<span data-ttu-id="420fb-138">Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější hlavní verzi, která může podporovat.</span><span class="sxs-lookup"><span data-stu-id="420fb-138">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="420fb-139">ISO-1</span><span class="sxs-lookup"><span data-stu-id="420fb-139">ISO-1</span></span>|<span data-ttu-id="420fb-140">Kompilátor přijímá pouze syntaxi, která je součástí ISO/IEC 23270: 2003 C# (1.0 nebo 1.2)</span><span class="sxs-lookup"><span data-stu-id="420fb-140">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
|<span data-ttu-id="420fb-141">ISO-2</span><span class="sxs-lookup"><span data-stu-id="420fb-141">ISO-2</span></span>|<span data-ttu-id="420fb-142">Kompilátor přijímá pouze syntaxi, která je součástí ISO/IEC 23270: 2006 C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="420fb-142">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="420fb-143">3</span><span class="sxs-lookup"><span data-stu-id="420fb-143">3</span></span>|<span data-ttu-id="420fb-144">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 3.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="420fb-144">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="420fb-145">4</span><span class="sxs-lookup"><span data-stu-id="420fb-145">4</span></span>|<span data-ttu-id="420fb-146">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 4.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="420fb-146">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="420fb-147">5</span><span class="sxs-lookup"><span data-stu-id="420fb-147">5</span></span>|<span data-ttu-id="420fb-148">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 5.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="420fb-148">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="420fb-149">6</span><span class="sxs-lookup"><span data-stu-id="420fb-149">6</span></span>|<span data-ttu-id="420fb-150">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 6.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="420fb-150">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="420fb-151">7</span><span class="sxs-lookup"><span data-stu-id="420fb-151">7</span></span>|<span data-ttu-id="420fb-152">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="420fb-152">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="420fb-153">7.1</span><span class="sxs-lookup"><span data-stu-id="420fb-153">7.1</span></span>|<span data-ttu-id="420fb-154">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.1 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="420fb-154">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="420fb-155">7.2</span><span class="sxs-lookup"><span data-stu-id="420fb-155">7.2</span></span>|<span data-ttu-id="420fb-156">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.2 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="420fb-156">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="420fb-157">7.3</span><span class="sxs-lookup"><span data-stu-id="420fb-157">7.3</span></span>|<span data-ttu-id="420fb-158">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.3 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="420fb-158">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="420fb-159">Nejnovější</span><span class="sxs-lookup"><span data-stu-id="420fb-159">latest</span></span>|<span data-ttu-id="420fb-160">Kompilátor přijímá všechny platné syntaxe jazyka, jakou může podporovat.</span><span class="sxs-lookup"><span data-stu-id="420fb-160">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="420fb-161">Speciální řetězce `default` a `latest` odkazující na nejnovější hlavní (C# 7.0) a (C# 7.3) jazyk podverze nainstalován v počítači sestavení v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="420fb-161">The special strings `default` and `latest` resolve to the latest major (C# 7.0) and minor (C# 7.3) language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="420fb-162">Konfigurace více projektů</span><span class="sxs-lookup"><span data-stu-id="420fb-162">Configure multiple projects</span></span>

<span data-ttu-id="420fb-163">Můžete vytvořit **Directory.build.props** soubor, který obsahuje `<LangVersion>` elementu, který chcete nakonfigurovat několik adresářů.</span><span class="sxs-lookup"><span data-stu-id="420fb-163">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="420fb-164">Obvykle to uděláte ve vašem adresáři řešení.</span><span class="sxs-lookup"><span data-stu-id="420fb-164">You typically do that in your solution directory.</span></span> <span data-ttu-id="420fb-165">Přidejte následující **Directory.build.props** soubor v adresáři řešení:</span><span class="sxs-lookup"><span data-stu-id="420fb-165">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="420fb-166">Nyní sestavení v každé podadresáři adresář obsahující tento soubor použije verze 7.3 syntaxe jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="420fb-166">Now, builds in every subdirectory of the directory containing that file will use C# version 7.3 syntax.</span></span> <span data-ttu-id="420fb-167">Další informace najdete v článku na [přizpůsobit buildu](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="420fb-167">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="420fb-168">Nastavte langversion – možnost kompilátoru</span><span class="sxs-lookup"><span data-stu-id="420fb-168">Set the langversion compiler option</span></span>

<span data-ttu-id="420fb-169">Můžete použít `-langversion` možnost příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="420fb-169">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="420fb-170">Další informace najdete v článku na [- langversion](../language-reference/compiler-options/langversion-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="420fb-170">For more information, see the article on the [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) compiler option.</span></span> <span data-ttu-id="420fb-171">Zobrazí se seznam platných hodnot zadáním `csc -langversion:?`.</span><span class="sxs-lookup"><span data-stu-id="420fb-171">You can see a list of the valid values by typing  `csc -langversion:?`.</span></span>
