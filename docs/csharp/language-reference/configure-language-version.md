---
title: C#jazykové verze – C# Průvodce
description: Přečtěte si informace C# o tom, jak je jazyková verze určena na základě vašeho projektu, a v různých hodnotách, na které lze ručně upravit.
ms.date: 07/10/2019
ms.openlocfilehash: fae36f5305e23fbfa1c55c5881e37391670f93ab
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040352"
---
# <a name="c-language-versioning"></a><span data-ttu-id="f0f5e-103">C#jazykové verze</span><span class="sxs-lookup"><span data-stu-id="f0f5e-103">C# language versioning</span></span>

<span data-ttu-id="f0f5e-104">Nejnovější C# kompilátor určuje výchozí jazykovou verzi v závislosti na cílovém rozhraní architektury vašeho projektu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-104">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="f0f5e-105">Důvodem je, že C# jazyk může obsahovat funkce, které spoléhají na typy nebo běhové komponenty, které nejsou k dispozici v každé implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="f0f5e-106">Tím se také zajistí, že pro jakýkoliv cíl, na který je projekt sestaven, získáte ve výchozím nastavení nejvyšší kompatibilní jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

<span data-ttu-id="f0f5e-107">Pravidla v tomto článku se vztahují na kompilátor dodaný se sadou Visual Studio 2019 nebo sadu .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-107">The rules in this article apply to the compiler delivered with Visual Studio 2019, or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="f0f5e-108">C# Kompilátory, které jsou součástí instalace sady Visual Studio 2017 nebo starší verze .NET Core SDK v cíli C# 7,0 ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-108">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span> 

## <a name="defaults"></a><span data-ttu-id="f0f5e-109">Ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="f0f5e-109">Defaults</span></span>

<span data-ttu-id="f0f5e-110">Kompilátor určuje výchozí hodnotu na základě těchto pravidel:</span><span class="sxs-lookup"><span data-stu-id="f0f5e-110">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="f0f5e-111">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="f0f5e-111">Target framework</span></span>|<span data-ttu-id="f0f5e-112">verze</span><span class="sxs-lookup"><span data-stu-id="f0f5e-112">version</span></span>|<span data-ttu-id="f0f5e-113">C#výchozí verze jazyka</span><span class="sxs-lookup"><span data-stu-id="f0f5e-113">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="f0f5e-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="f0f5e-114">.NET Core</span></span>|<span data-ttu-id="f0f5e-115">3.x</span><span class="sxs-lookup"><span data-stu-id="f0f5e-115">3.x</span></span>|<span data-ttu-id="f0f5e-116">C#8,0</span><span class="sxs-lookup"><span data-stu-id="f0f5e-116">C# 8.0</span></span>|
|<span data-ttu-id="f0f5e-117">.NET Core</span><span class="sxs-lookup"><span data-stu-id="f0f5e-117">.NET Core</span></span>|<span data-ttu-id="f0f5e-118">2.x</span><span class="sxs-lookup"><span data-stu-id="f0f5e-118">2.x</span></span>|<span data-ttu-id="f0f5e-119">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="f0f5e-119">C# 7.3</span></span>|
|<span data-ttu-id="f0f5e-120">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="f0f5e-120">.NET Standard</span></span>|<span data-ttu-id="f0f5e-121">všechny</span><span class="sxs-lookup"><span data-stu-id="f0f5e-121">all</span></span>|<span data-ttu-id="f0f5e-122">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="f0f5e-122">C# 7.3</span></span>|
|<span data-ttu-id="f0f5e-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="f0f5e-123">.NET Framework</span></span>|<span data-ttu-id="f0f5e-124">všechny</span><span class="sxs-lookup"><span data-stu-id="f0f5e-124">all</span></span>|<span data-ttu-id="f0f5e-125">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="f0f5e-125">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="f0f5e-126">Výchozí pro náhledy</span><span class="sxs-lookup"><span data-stu-id="f0f5e-126">Default for previews</span></span>

<span data-ttu-id="f0f5e-127">Když se váš projekt zaměřuje na architekturu verze Preview, která má odpovídající jazykovou verzi Preview, bude použit jazyk verze Preview.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-127">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="f0f5e-128">Tím zajistíte, že budete moci používat nejnovější funkce, u kterých je zaručená práce s touto verzí Preview v jakémkoli prostředí, aniž by to ovlivnilo projekty, které cílí na vydanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-128">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="f0f5e-129">Přepsat výchozí</span><span class="sxs-lookup"><span data-stu-id="f0f5e-129">Override a default</span></span>

<span data-ttu-id="f0f5e-130">Pokud je nutné explicitně zadat C# verzi, můžete to provést několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="f0f5e-130">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="f0f5e-131">Ručně upravte [soubor projektu](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="f0f5e-131">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="f0f5e-132">Nastaví jazykovou verzi [pro více projektů v](#configure-multiple-projects)podadresáři.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-132">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="f0f5e-133">Konfigurovat [možnost kompilátoru `-langversion`](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="f0f5e-133">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="f0f5e-134">Upravit soubor projektu</span><span class="sxs-lookup"><span data-stu-id="f0f5e-134">Edit the project file</span></span>

<span data-ttu-id="f0f5e-135">V souboru projektu můžete nastavit jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-135">You can set the language version in your project file.</span></span> <span data-ttu-id="f0f5e-136">Například pokud výslovně chcete získat přístup k funkcím verze Preview, přidejte prvek podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="f0f5e-136">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="f0f5e-137">Hodnota `preview` používá nejnovější verzi verze Preview C# , kterou podporuje kompilátor.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-137">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="f0f5e-138">Konfigurace více projektů</span><span class="sxs-lookup"><span data-stu-id="f0f5e-138">Configure multiple projects</span></span>

<span data-ttu-id="f0f5e-139">Můžete vytvořit soubor **Directory. Build. props** , který obsahuje `<LangVersion>` element pro konfiguraci více adresářů.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-139">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="f0f5e-140">Obvykle to provedete v adresáři řešení.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-140">You typically do that in your solution directory.</span></span> <span data-ttu-id="f0f5e-141">Přidejte následující do souboru **Directory. Build. props** v adresáři řešení:</span><span class="sxs-lookup"><span data-stu-id="f0f5e-141">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="f0f5e-142">Nyní sestavení v každém podadresáři adresáře obsahujícího tento soubor použije verzi Preview C# .</span><span class="sxs-lookup"><span data-stu-id="f0f5e-142">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="f0f5e-143">Další informace naleznete v článku o [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="f0f5e-143">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="f0f5e-144">C#Referenční informace o jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="f0f5e-144">C# language version reference</span></span>

<span data-ttu-id="f0f5e-145">V následující tabulce jsou uvedeny všechny C# aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-145">The following table shows all current C# language versions.</span></span> <span data-ttu-id="f0f5e-146">Kompilátor nemusí nutně pochopit každou hodnotu, pokud je starší.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-146">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="f0f5e-147">Pokud nainstalujete .NET Core 3,0, budete mít přístup ke všem uvedeným.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-147">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="f0f5e-148">Value</span><span class="sxs-lookup"><span data-stu-id="f0f5e-148">Value</span></span>|<span data-ttu-id="f0f5e-149">Význam</span><span class="sxs-lookup"><span data-stu-id="f0f5e-149">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="f0f5e-150">preview</span><span class="sxs-lookup"><span data-stu-id="f0f5e-150">preview</span></span>|<span data-ttu-id="f0f5e-151">Kompilátor přijímá všechny platné jazykové syntaxe z nejnovější verze Preview.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-151">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="f0f5e-152">latest</span><span class="sxs-lookup"><span data-stu-id="f0f5e-152">latest</span></span>|<span data-ttu-id="f0f5e-153">Kompilátor přijímá syntaxi z nejnovější vydané verze kompilátoru (včetně dílčí verze).</span><span class="sxs-lookup"><span data-stu-id="f0f5e-153">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="f0f5e-154">latestMajor</span><span class="sxs-lookup"><span data-stu-id="f0f5e-154">latestMajor</span></span>|<span data-ttu-id="f0f5e-155">Kompilátor přijímá syntaxi z poslední vydané hlavní verze kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-155">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="f0f5e-156">8.0</span><span class="sxs-lookup"><span data-stu-id="f0f5e-156">8.0</span></span>|<span data-ttu-id="f0f5e-157">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 8,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-157">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="f0f5e-158">7.3</span><span class="sxs-lookup"><span data-stu-id="f0f5e-158">7.3</span></span>|<span data-ttu-id="f0f5e-159">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,3 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-159">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="f0f5e-160">7.2</span><span class="sxs-lookup"><span data-stu-id="f0f5e-160">7.2</span></span>|<span data-ttu-id="f0f5e-161">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,2 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-161">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="f0f5e-162">7.1</span><span class="sxs-lookup"><span data-stu-id="f0f5e-162">7.1</span></span>|<span data-ttu-id="f0f5e-163">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,1 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-163">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="f0f5e-164">7</span><span class="sxs-lookup"><span data-stu-id="f0f5e-164">7</span></span>|<span data-ttu-id="f0f5e-165">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-165">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="f0f5e-166">6</span><span class="sxs-lookup"><span data-stu-id="f0f5e-166">6</span></span>|<span data-ttu-id="f0f5e-167">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 6,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-167">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="f0f5e-168">5</span><span class="sxs-lookup"><span data-stu-id="f0f5e-168">5</span></span>|<span data-ttu-id="f0f5e-169">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 5,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-169">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="f0f5e-170">4</span><span class="sxs-lookup"><span data-stu-id="f0f5e-170">4</span></span>|<span data-ttu-id="f0f5e-171">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 4,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-171">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="f0f5e-172">3</span><span class="sxs-lookup"><span data-stu-id="f0f5e-172">3</span></span>|<span data-ttu-id="f0f5e-173">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 3,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="f0f5e-173">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="f0f5e-174">ISO-2</span><span class="sxs-lookup"><span data-stu-id="f0f5e-174">ISO-2</span></span>|<span data-ttu-id="f0f5e-175">Kompilátor přijímá pouze syntaxi, která je obsažena v normě ISO C# /IEC 23270:2006 (2,0)</span><span class="sxs-lookup"><span data-stu-id="f0f5e-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="f0f5e-176">ISO-1</span><span class="sxs-lookup"><span data-stu-id="f0f5e-176">ISO-1</span></span>|<span data-ttu-id="f0f5e-177">Kompilátor přijímá pouze syntaxi, která je obsažena v normě ISO C# /IEC 23270:2003 (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="f0f5e-177">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
