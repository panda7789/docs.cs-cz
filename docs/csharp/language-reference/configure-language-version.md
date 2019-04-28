---
title: Vyberte C# jazykovou verzi - C# Průvodce
description: Konfigurace kompilátor provést ověření syntaxe pomocí specifické verzi kompilátoru
ms.date: 02/28/2019
ms.openlocfilehash: feb3e51a107f9830071b55c7985f202edc842f4a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662281"
---
# <a name="select-the-c-language-version"></a><span data-ttu-id="54285-103">Vyberte C# jazykovou verzi</span><span class="sxs-lookup"><span data-stu-id="54285-103">Select the C# language version</span></span>

<span data-ttu-id="54285-104">C# Kompilátor Určuje výchozí jazykovou verzi na základě cílové rozhraní projektu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="54285-104">The C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="54285-105">Když váš projekt cílí na verzi preview rozhraní, které obsahuje odpovídající jazykovou verzi preview, je jazyková verze používá jazykovou verzi preview.</span><span class="sxs-lookup"><span data-stu-id="54285-105">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="54285-106">Projekt není zacílená ve verzi preview rozhraní, jazykové verzi použít při nejnovější dílčí verzi.</span><span class="sxs-lookup"><span data-stu-id="54285-106">When your project doesn't target a preview framework, the language version used is the latest minor version.</span></span>

<span data-ttu-id="54285-107">Například během období preview pro .NET Core 3.0, libovolný projekt, který cílí `netcoreapp3.0` nebo `netstandard2.1` (ve verzi preview) se používají C# 8.0 – language (také ve verzi preview).</span><span class="sxs-lookup"><span data-stu-id="54285-107">For example, during the preview period for .NET Core 3.0, any project that targets `netcoreapp3.0` or `netstandard2.1` (both in preview) will use the C# 8.0 language (also in preview).</span></span> <span data-ttu-id="54285-108">Cílení na všechny vydané verzi použije C# 7.3 (nejnovější vydaná verze).</span><span class="sxs-lookup"><span data-stu-id="54285-108">Projects targeting any released version will use C# 7.3 (the latest released version).</span></span> <span data-ttu-id="54285-109">Toto chování znamená, že každý projekt cílí na rozhraní .NET Framework bude používat nejnovější verzi (C# 7.3).</span><span class="sxs-lookup"><span data-stu-id="54285-109">This behavior means that any project targeting .NET Framework will use latest (C# 7.3).</span></span> 

<span data-ttu-id="54285-110">Tato funkce odděluje rozhodnutí pro instalaci nové verze sady SDK a nástroje ve vašem vývojovém prostředí od rozhodnutí začlenit nové funkce jazyků v projektu.</span><span class="sxs-lookup"><span data-stu-id="54285-110">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="54285-111">Nejnovější sady SDK a nástroje můžete nainstalovat na počítače pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="54285-111">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="54285-112">Každý projekt se dá použít konkrétní verzi jazyka pro jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="54285-112">Each project can be configured to use a specific version of the language for its build.</span></span> <span data-ttu-id="54285-113">Výchozí chování znamená, že všechny jazykové funkce, které využívají nové typy nebo nové chování modulu CLR jsou povolené jenom v případě, že projekty jsou určené pro tyto architektury.</span><span class="sxs-lookup"><span data-stu-id="54285-113">The default behavior means that any language features that rely on new types or new CLR behavior are enabled only when projects target those frameworks.</span></span>

<span data-ttu-id="54285-114">Výchozí chování můžete přepsat zadáním jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="54285-114">You can override the default behavior by specifying a language version.</span></span> <span data-ttu-id="54285-115">Existuje několik způsobů, jak nastavit jazykovou verzi:</span><span class="sxs-lookup"><span data-stu-id="54285-115">There are several ways to set the language version:</span></span>

- <span data-ttu-id="54285-116">Spolehněte se na [sady Visual Studio rychle reagovat](#visual-studio-quick-action).</span><span class="sxs-lookup"><span data-stu-id="54285-116">Rely on a [Visual Studio quick action](#visual-studio-quick-action).</span></span>
- <span data-ttu-id="54285-117">Nastavení jazykové verze v [Visual Studio UI](#set-the-language-version-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="54285-117">Set the language version in the [Visual Studio UI](#set-the-language-version-in-visual-studio).</span></span>
- <span data-ttu-id="54285-118">Ručně upravit vaše [ **.csproj** souboru](#edit-the-csproj-file).</span><span class="sxs-lookup"><span data-stu-id="54285-118">Manually edit your [**.csproj** file](#edit-the-csproj-file).</span></span>
- <span data-ttu-id="54285-119">Nastavit jazykovou verzi [pro více projektů v podadresáři](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="54285-119">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="54285-120">Konfigurace [ `-langversion` – možnost kompilátoru](#set-the-langversion-compiler-option).</span><span class="sxs-lookup"><span data-stu-id="54285-120">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option).</span></span>

## <a name="visual-studio-quick-action"></a><span data-ttu-id="54285-121">Rychlé akce pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="54285-121">Visual Studio quick action</span></span>

<span data-ttu-id="54285-122">Visual Studio vám pomůže určit jazykové verze, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="54285-122">Visual Studio helps you determine the language version you need.</span></span> <span data-ttu-id="54285-123">Pokud používáte jazyk funkce, která není k dispozici pro aktuálně nakonfigurovaná verze, sada Visual Studio zobrazí potenciální opravu a aktualizovat verzi jazyka pro projekt.</span><span class="sxs-lookup"><span data-stu-id="54285-123">If you use a language feature that is not available for the currently configured version, Visual Studio shows a potential fix to update the language version for the project.</span></span>

## <a name="set-the-language-version-in-visual-studio"></a><span data-ttu-id="54285-124">Nastavení jazykové verze v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="54285-124">Set the language version in Visual Studio</span></span>

<span data-ttu-id="54285-125">Nastavte verzi v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="54285-125">You can set the version in Visual Studio.</span></span> <span data-ttu-id="54285-126">Klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="54285-126">Right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="54285-127">Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="54285-127">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="54285-128">V rozevíracím seznamu vyberte verzi.</span><span class="sxs-lookup"><span data-stu-id="54285-128">In the dropdown, select the version.</span></span> <span data-ttu-id="54285-129">Následující obrázek ukazuje "posledního" nastavení:</span><span class="sxs-lookup"><span data-stu-id="54285-129">The following image shows the "latest" setting:</span></span>

![Snímek obrazovky nastavení rozšířené sestavení, ve kterém můžete zadat jazykovou verzi](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> <span data-ttu-id="54285-131">Je-li aktualizovat soubory csproj pomocí rozhraní IDE sady Visual Studio, rozhraní IDE vytvoří samostatné uzly pro každou konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="54285-131">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="54285-132">Budete obvykle nastavena hodnotu stejné ve všech konfiguracích sestavení, ale je potřeba explicitně nastavena pro každou konfiguraci sestavení, nebo vyberte "Všechny konfigurace", když je toto nastavení změnit.</span><span class="sxs-lookup"><span data-stu-id="54285-132">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="54285-133">V souboru csproj se zobrazí následující:</span><span class="sxs-lookup"><span data-stu-id="54285-133">You'll see the following in your csproj file:</span></span>
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

## <a name="edit-the-csproj-file"></a><span data-ttu-id="54285-134">Upravte soubor csproj</span><span class="sxs-lookup"><span data-stu-id="54285-134">Edit the csproj file</span></span>

<span data-ttu-id="54285-135">Můžete nastavit jazykovou verzi vašeho **.csproj** souboru.</span><span class="sxs-lookup"><span data-stu-id="54285-135">You can set the language version in your **.csproj** file.</span></span> <span data-ttu-id="54285-136">Přidáte element takto:</span><span class="sxs-lookup"><span data-stu-id="54285-136">Add an element like the following:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="54285-137">Hodnota `latest` používá nejnovější dílčí verzi C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="54285-137">The value `latest` uses the latest minor version of the C# language.</span></span> <span data-ttu-id="54285-138">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="54285-138">Valid values are:</span></span>

|<span data-ttu-id="54285-139">Value</span><span class="sxs-lookup"><span data-stu-id="54285-139">Value</span></span>|<span data-ttu-id="54285-140">Význam</span><span class="sxs-lookup"><span data-stu-id="54285-140">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="54285-141">preview</span><span class="sxs-lookup"><span data-stu-id="54285-141">preview</span></span>|<span data-ttu-id="54285-142">Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější verze preview.</span><span class="sxs-lookup"><span data-stu-id="54285-142">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="54285-143">nejnovější</span><span class="sxs-lookup"><span data-stu-id="54285-143">latest</span></span>|<span data-ttu-id="54285-144">Kompilátor přijímá syntaxi z nejnovější vydanou verzi kompilátoru (včetně vedlejší verze aktualizace).</span><span class="sxs-lookup"><span data-stu-id="54285-144">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="54285-145">latestMajor</span><span class="sxs-lookup"><span data-stu-id="54285-145">latestMajor</span></span>|<span data-ttu-id="54285-146">Kompilátor přijímá syntaxi z nejnovější vydanou hlavní verzi kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="54285-146">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="54285-147">8.0</span><span class="sxs-lookup"><span data-stu-id="54285-147">8.0</span></span>|<span data-ttu-id="54285-148">Kompilátor přijímá pouze syntaxi, která je součástí C# 8.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="54285-148">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="54285-149">7.3</span><span class="sxs-lookup"><span data-stu-id="54285-149">7.3</span></span>|<span data-ttu-id="54285-150">Kompilátor přijímá pouze syntaxi, která je součástí C# 7.3 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="54285-150">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="54285-151">7.2</span><span class="sxs-lookup"><span data-stu-id="54285-151">7.2</span></span>|<span data-ttu-id="54285-152">Kompilátor přijímá pouze syntaxi, která je součástí C# 7.2 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="54285-152">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="54285-153">7.1</span><span class="sxs-lookup"><span data-stu-id="54285-153">7.1</span></span>|<span data-ttu-id="54285-154">Kompilátor přijímá pouze syntaxi, která je součástí C# 7.1 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="54285-154">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="54285-155">7</span><span class="sxs-lookup"><span data-stu-id="54285-155">7</span></span>|<span data-ttu-id="54285-156">Kompilátor přijímá pouze syntaxi, která je součástí C# 7.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="54285-156">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="54285-157">6</span><span class="sxs-lookup"><span data-stu-id="54285-157">6</span></span>|<span data-ttu-id="54285-158">Kompilátor přijímá pouze syntaxi, která je součástí C# 6.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="54285-158">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="54285-159">5</span><span class="sxs-lookup"><span data-stu-id="54285-159">5</span></span>|<span data-ttu-id="54285-160">Kompilátor přijímá pouze syntaxi, která je součástí C# 5.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="54285-160">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="54285-161">4</span><span class="sxs-lookup"><span data-stu-id="54285-161">4</span></span>|<span data-ttu-id="54285-162">Kompilátor přijímá pouze syntaxi, která je součástí C# 4.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="54285-162">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="54285-163">3</span><span class="sxs-lookup"><span data-stu-id="54285-163">3</span></span>|<span data-ttu-id="54285-164">Kompilátor přijímá pouze syntaxi, která je součástí C# 3.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="54285-164">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="54285-165">ISO-2</span><span class="sxs-lookup"><span data-stu-id="54285-165">ISO-2</span></span>|<span data-ttu-id="54285-166">Kompilátor přijímá pouze syntaxi, která je součástí 23270: ISO/IEC 2006 C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="54285-166">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="54285-167">ISO-1</span><span class="sxs-lookup"><span data-stu-id="54285-167">ISO-1</span></span>|<span data-ttu-id="54285-168">Kompilátor přijímá pouze syntaxi, která je součástí 23270: ISO/IEC 2003 C# (1.0 nebo 1.2)</span><span class="sxs-lookup"><span data-stu-id="54285-168">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |

## <a name="configure-multiple-projects"></a><span data-ttu-id="54285-169">Konfigurace více projektů</span><span class="sxs-lookup"><span data-stu-id="54285-169">Configure multiple projects</span></span>

<span data-ttu-id="54285-170">Můžete vytvořit **Directory.Build.props** soubor, který obsahuje `<LangVersion>` prvek, který chcete nakonfigurovat více adresářů.</span><span class="sxs-lookup"><span data-stu-id="54285-170">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="54285-171">Obvykle to uděláte ve svém adresáři řešení.</span><span class="sxs-lookup"><span data-stu-id="54285-171">You typically do that in your solution directory.</span></span> <span data-ttu-id="54285-172">Přidejte následující text do **Directory.Build.props** soubor v adresáři řešení:</span><span class="sxs-lookup"><span data-stu-id="54285-172">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="54285-173">Nyní, bude sestavení všechny podadresáře adresáře, který obsahuje tento soubor používají C# verzi 7.3 syntaxe.</span><span class="sxs-lookup"><span data-stu-id="54285-173">Now, builds in every subdirectory of the directory containing that file will use C# version 7.3 syntax.</span></span> <span data-ttu-id="54285-174">Další informace najdete v článku na [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="54285-174">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="54285-175">Nastavte langversion – možnost kompilátoru</span><span class="sxs-lookup"><span data-stu-id="54285-175">Set the langversion compiler option</span></span>

<span data-ttu-id="54285-176">Můžete použít `-langversion` možnost příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="54285-176">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="54285-177">Další informace najdete v článku na [- langversion](../language-reference/compiler-options/langversion-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="54285-177">For more information, see the article on the [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) compiler option.</span></span> <span data-ttu-id="54285-178">Seznam platných hodnot najdete tak, že zadáte `csc -langversion:?`.</span><span class="sxs-lookup"><span data-stu-id="54285-178">You can see a list of the valid values by typing  `csc -langversion:?`.</span></span>
