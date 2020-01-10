---
title: C#jazykové verze – C# Průvodce
description: Přečtěte si informace C# o tom, jak je jazyková verze určena na základě vašeho projektu, a v různých hodnotách, na které lze ručně upravit.
ms.date: 07/10/2019
ms.openlocfilehash: 90624816a68de694cacd0017c6d3162f6a89431c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713877"
---
# <a name="c-language-versioning"></a><span data-ttu-id="d52d3-103">C#jazykové verze</span><span class="sxs-lookup"><span data-stu-id="d52d3-103">C# language versioning</span></span>

<span data-ttu-id="d52d3-104">Nejnovější C# kompilátor určuje výchozí jazykovou verzi v závislosti na cílovém rozhraní architektury vašeho projektu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d52d3-104">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="d52d3-105">Důvodem je, že C# jazyk může obsahovat funkce, které spoléhají na typy nebo běhové komponenty, které nejsou k dispozici v každé implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="d52d3-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="d52d3-106">Tím se také zajistí, že pro jakýkoliv cíl, na který je projekt sestaven, získáte ve výchozím nastavení nejvyšší kompatibilní jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="d52d3-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

<span data-ttu-id="d52d3-107">Pravidla v tomto článku se vztahují na kompilátor dodaný se sadou Visual Studio 2019 nebo sadu .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d52d3-107">The rules in this article apply to the compiler delivered with Visual Studio 2019, or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="d52d3-108">C# Kompilátory, které jsou součástí instalace sady Visual Studio 2017 nebo starší verze .NET Core SDK v cíli C# 7,0 ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="d52d3-108">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span> 

## <a name="defaults"></a><span data-ttu-id="d52d3-109">Ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="d52d3-109">Defaults</span></span>

<span data-ttu-id="d52d3-110">Kompilátor určuje výchozí hodnotu na základě těchto pravidel:</span><span class="sxs-lookup"><span data-stu-id="d52d3-110">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="d52d3-111">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="d52d3-111">Target framework</span></span>|<span data-ttu-id="d52d3-112">Verze nástroje</span><span class="sxs-lookup"><span data-stu-id="d52d3-112">version</span></span>|<span data-ttu-id="d52d3-113">C#výchozí verze jazyka</span><span class="sxs-lookup"><span data-stu-id="d52d3-113">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="d52d3-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d52d3-114">.NET Core</span></span>|<span data-ttu-id="d52d3-115">3.x</span><span class="sxs-lookup"><span data-stu-id="d52d3-115">3.x</span></span>|<span data-ttu-id="d52d3-116">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="d52d3-116">C# 8.0</span></span>|
|<span data-ttu-id="d52d3-117">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d52d3-117">.NET Core</span></span>|<span data-ttu-id="d52d3-118">2.x</span><span class="sxs-lookup"><span data-stu-id="d52d3-118">2.x</span></span>|<span data-ttu-id="d52d3-119">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="d52d3-119">C# 7.3</span></span>|
|<span data-ttu-id="d52d3-120">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="d52d3-120">.NET Standard</span></span>|<span data-ttu-id="d52d3-121">2.1</span><span class="sxs-lookup"><span data-stu-id="d52d3-121">2.1</span></span>|<span data-ttu-id="d52d3-122">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="d52d3-122">C# 8.0</span></span>|
|<span data-ttu-id="d52d3-123">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="d52d3-123">.NET Standard</span></span>|<span data-ttu-id="d52d3-124">2.0</span><span class="sxs-lookup"><span data-stu-id="d52d3-124">2.0</span></span>|<span data-ttu-id="d52d3-125">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="d52d3-125">C# 7.3</span></span>|
|<span data-ttu-id="d52d3-126">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="d52d3-126">.NET Standard</span></span>|<span data-ttu-id="d52d3-127">verze</span><span class="sxs-lookup"><span data-stu-id="d52d3-127">1.x</span></span>|<span data-ttu-id="d52d3-128">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="d52d3-128">C# 7.3</span></span>|
|<span data-ttu-id="d52d3-129">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d52d3-129">.NET Framework</span></span>|<span data-ttu-id="d52d3-130">vše</span><span class="sxs-lookup"><span data-stu-id="d52d3-130">all</span></span>|<span data-ttu-id="d52d3-131">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="d52d3-131">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="d52d3-132">Výchozí pro náhledy</span><span class="sxs-lookup"><span data-stu-id="d52d3-132">Default for previews</span></span>

<span data-ttu-id="d52d3-133">Když se váš projekt zaměřuje na architekturu verze Preview, která má odpovídající jazykovou verzi Preview, bude použit jazyk verze Preview.</span><span class="sxs-lookup"><span data-stu-id="d52d3-133">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="d52d3-134">Tím zajistíte, že budete moci používat nejnovější funkce, u kterých je zaručená práce s touto verzí Preview v jakémkoli prostředí, aniž by to ovlivnilo projekty, které cílí na vydanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d52d3-134">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="d52d3-135">Přepsat výchozí</span><span class="sxs-lookup"><span data-stu-id="d52d3-135">Override a default</span></span>

<span data-ttu-id="d52d3-136">Pokud je nutné explicitně zadat C# verzi, můžete to provést několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="d52d3-136">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="d52d3-137">Ručně upravte [soubor projektu](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="d52d3-137">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="d52d3-138">Nastaví jazykovou verzi [pro více projektů v podadresáři](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="d52d3-138">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="d52d3-139">Nakonfigurujte [možnost kompilátoru`-langversion`](compiler-options/langversion-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d52d3-139">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="d52d3-140">Upravit soubor projektu</span><span class="sxs-lookup"><span data-stu-id="d52d3-140">Edit the project file</span></span>

<span data-ttu-id="d52d3-141">V souboru projektu můžete nastavit jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="d52d3-141">You can set the language version in your project file.</span></span> <span data-ttu-id="d52d3-142">Například pokud výslovně chcete získat přístup k funkcím verze Preview, přidejte prvek podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="d52d3-142">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="d52d3-143">Hodnota `preview` používá nejnovější dostupnou jazykovou verzi C# Preview, kterou podporuje kompilátor.</span><span class="sxs-lookup"><span data-stu-id="d52d3-143">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="d52d3-144">Konfigurace více projektů</span><span class="sxs-lookup"><span data-stu-id="d52d3-144">Configure multiple projects</span></span>

<span data-ttu-id="d52d3-145">Můžete vytvořit soubor **Directory. Build. props** , který obsahuje prvek `<LangVersion>` pro konfiguraci více adresářů.</span><span class="sxs-lookup"><span data-stu-id="d52d3-145">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="d52d3-146">Obvykle to provedete v adresáři řešení.</span><span class="sxs-lookup"><span data-stu-id="d52d3-146">You typically do that in your solution directory.</span></span> <span data-ttu-id="d52d3-147">Přidejte následující do souboru **Directory. Build. props** v adresáři řešení:</span><span class="sxs-lookup"><span data-stu-id="d52d3-147">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="d52d3-148">Nyní sestavení v každém podadresáři adresáře obsahujícího tento soubor použije verzi Preview C# .</span><span class="sxs-lookup"><span data-stu-id="d52d3-148">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="d52d3-149">Další informace naleznete v článku o [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="d52d3-149">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="d52d3-150">C#Referenční informace o jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="d52d3-150">C# language version reference</span></span>

<span data-ttu-id="d52d3-151">V následující tabulce jsou uvedeny všechny C# aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="d52d3-151">The following table shows all current C# language versions.</span></span> <span data-ttu-id="d52d3-152">Kompilátor nemusí nutně pochopit každou hodnotu, pokud je starší.</span><span class="sxs-lookup"><span data-stu-id="d52d3-152">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="d52d3-153">Pokud nainstalujete .NET Core 3,0, budete mít přístup ke všem uvedeným.</span><span class="sxs-lookup"><span data-stu-id="d52d3-153">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="d52d3-154">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d52d3-154">Value</span></span>|<span data-ttu-id="d52d3-155">Význam</span><span class="sxs-lookup"><span data-stu-id="d52d3-155">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="d52d3-156">preview</span><span class="sxs-lookup"><span data-stu-id="d52d3-156">preview</span></span>|<span data-ttu-id="d52d3-157">Kompilátor přijímá všechny platné jazykové syntaxe z nejnovější verze Preview.</span><span class="sxs-lookup"><span data-stu-id="d52d3-157">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="d52d3-158">nejnovější</span><span class="sxs-lookup"><span data-stu-id="d52d3-158">latest</span></span>|<span data-ttu-id="d52d3-159">Kompilátor přijímá syntaxi z nejnovější vydané verze kompilátoru (včetně dílčí verze).</span><span class="sxs-lookup"><span data-stu-id="d52d3-159">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="d52d3-160">latestMajor</span><span class="sxs-lookup"><span data-stu-id="d52d3-160">latestMajor</span></span>|<span data-ttu-id="d52d3-161">Kompilátor přijímá syntaxi z poslední vydané hlavní verze kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d52d3-161">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="d52d3-162">8.0</span><span class="sxs-lookup"><span data-stu-id="d52d3-162">8.0</span></span>|<span data-ttu-id="d52d3-163">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 8,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="d52d3-163">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="d52d3-164">7.3</span><span class="sxs-lookup"><span data-stu-id="d52d3-164">7.3</span></span>|<span data-ttu-id="d52d3-165">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,3 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="d52d3-165">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="d52d3-166">7.2</span><span class="sxs-lookup"><span data-stu-id="d52d3-166">7.2</span></span>|<span data-ttu-id="d52d3-167">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,2 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="d52d3-167">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="d52d3-168">7,1</span><span class="sxs-lookup"><span data-stu-id="d52d3-168">7.1</span></span>|<span data-ttu-id="d52d3-169">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,1 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="d52d3-169">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="d52d3-170">7</span><span class="sxs-lookup"><span data-stu-id="d52d3-170">7</span></span>|<span data-ttu-id="d52d3-171">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="d52d3-171">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="d52d3-172">6</span><span class="sxs-lookup"><span data-stu-id="d52d3-172">6</span></span>|<span data-ttu-id="d52d3-173">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 6,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="d52d3-173">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="d52d3-174">5</span><span class="sxs-lookup"><span data-stu-id="d52d3-174">5</span></span>|<span data-ttu-id="d52d3-175">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 5,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="d52d3-175">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="d52d3-176">4</span><span class="sxs-lookup"><span data-stu-id="d52d3-176">4</span></span>|<span data-ttu-id="d52d3-177">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 4,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="d52d3-177">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="d52d3-178">3</span><span class="sxs-lookup"><span data-stu-id="d52d3-178">3</span></span>|<span data-ttu-id="d52d3-179">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 3,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="d52d3-179">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="d52d3-180">ISO-2</span><span class="sxs-lookup"><span data-stu-id="d52d3-180">ISO-2</span></span>|<span data-ttu-id="d52d3-181">Kompilátor přijímá pouze syntaxi, která je obsažena v normě ISO C# /IEC 23270:2006 (2,0)</span><span class="sxs-lookup"><span data-stu-id="d52d3-181">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="d52d3-182">ISO-1</span><span class="sxs-lookup"><span data-stu-id="d52d3-182">ISO-1</span></span>|<span data-ttu-id="d52d3-183">Kompilátor přijímá pouze syntaxi, která je obsažena v normě ISO C# /IEC 23270:2003 (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="d52d3-183">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
