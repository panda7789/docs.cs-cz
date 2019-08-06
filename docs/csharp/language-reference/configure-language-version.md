---
title: C#jazykové verze – C# Průvodce
description: Přečtěte si informace C# o tom, jak je jazyková verze určena na základě vašeho projektu, a v různých hodnotách, na které lze ručně upravit.
ms.date: 07/10/2019
ms.openlocfilehash: 744cec0aac21f743648cccbdc93cf2977c32d644
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796529"
---
# <a name="c-language-versioning"></a><span data-ttu-id="b59b0-103">C#jazykové verze</span><span class="sxs-lookup"><span data-stu-id="b59b0-103">C# language versioning</span></span>

<span data-ttu-id="b59b0-104">C# Kompilátor určuje výchozí jazykovou verzi na základě cílových rozhraní architektury vašeho projektu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b59b0-104">The C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="b59b0-105">Důvodem je, že C# jazyk může obsahovat funkce, které spoléhají na typy nebo běhové komponenty, které nejsou k dispozici v každé implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="b59b0-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="b59b0-106">Tím se také zajistí, že pro jakýkoliv cíl, na který je projekt sestaven, získáte ve výchozím nastavení nejvyšší kompatibilní jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="b59b0-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

## <a name="defaults"></a><span data-ttu-id="b59b0-107">Ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="b59b0-107">Defaults</span></span>

<span data-ttu-id="b59b0-108">Kompilátor určuje výchozí hodnotu na základě těchto pravidel:</span><span class="sxs-lookup"><span data-stu-id="b59b0-108">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="b59b0-109">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="b59b0-109">Target framework</span></span>|<span data-ttu-id="b59b0-110">verze</span><span class="sxs-lookup"><span data-stu-id="b59b0-110">version</span></span>|<span data-ttu-id="b59b0-111">C#výchozí verze jazyka</span><span class="sxs-lookup"><span data-stu-id="b59b0-111">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="b59b0-112">.NET Core</span><span class="sxs-lookup"><span data-stu-id="b59b0-112">.NET Core</span></span>|<span data-ttu-id="b59b0-113">3.x</span><span class="sxs-lookup"><span data-stu-id="b59b0-113">3.x</span></span>|<span data-ttu-id="b59b0-114">C#8,0</span><span class="sxs-lookup"><span data-stu-id="b59b0-114">C# 8.0</span></span>|
|<span data-ttu-id="b59b0-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="b59b0-115">.NET Core</span></span>|<span data-ttu-id="b59b0-116">2.x</span><span class="sxs-lookup"><span data-stu-id="b59b0-116">2.x</span></span>|<span data-ttu-id="b59b0-117">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="b59b0-117">C# 7.3</span></span>|
|<span data-ttu-id="b59b0-118">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="b59b0-118">.NET Standard</span></span>|<span data-ttu-id="b59b0-119">všechny</span><span class="sxs-lookup"><span data-stu-id="b59b0-119">all</span></span>|<span data-ttu-id="b59b0-120">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="b59b0-120">C# 7.3</span></span>|
|<span data-ttu-id="b59b0-121">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="b59b0-121">.NET Framework</span></span>|<span data-ttu-id="b59b0-122">všechny</span><span class="sxs-lookup"><span data-stu-id="b59b0-122">all</span></span>|<span data-ttu-id="b59b0-123">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="b59b0-123">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="b59b0-124">Výchozí pro náhledy</span><span class="sxs-lookup"><span data-stu-id="b59b0-124">Default for previews</span></span>

<span data-ttu-id="b59b0-125">Když se váš projekt zaměřuje na architekturu verze Preview, která má odpovídající jazykovou verzi Preview, bude použit jazyk verze Preview.</span><span class="sxs-lookup"><span data-stu-id="b59b0-125">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="b59b0-126">Tím zajistíte, že budete moci používat nejnovější funkce, u kterých je zaručená práce s touto verzí Preview v jakémkoli prostředí, aniž by to ovlivnilo projekty, které cílí na vydanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b59b0-126">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="b59b0-127">Přepsat výchozí</span><span class="sxs-lookup"><span data-stu-id="b59b0-127">Override a default</span></span>

<span data-ttu-id="b59b0-128">Pokud je nutné explicitně zadat C# verzi, můžete to provést několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="b59b0-128">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="b59b0-129">Ručně upravte [soubor projektu](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="b59b0-129">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="b59b0-130">Nastaví jazykovou verzi [pro více projektů v](#configure-multiple-projects)podadresáři.</span><span class="sxs-lookup"><span data-stu-id="b59b0-130">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="b59b0-131">Konfigurovat [možnost kompilátoru `-langversion`](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="b59b0-131">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="b59b0-132">Upravit soubor projektu</span><span class="sxs-lookup"><span data-stu-id="b59b0-132">Edit the project file</span></span>

<span data-ttu-id="b59b0-133">V souboru projektu můžete nastavit jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="b59b0-133">You can set the language version in your project file.</span></span> <span data-ttu-id="b59b0-134">Například pokud výslovně chcete získat přístup k funkcím verze Preview, přidejte prvek podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="b59b0-134">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="b59b0-135">Hodnota `preview` používá nejnovější verzi verze Preview C# , kterou podporuje kompilátor.</span><span class="sxs-lookup"><span data-stu-id="b59b0-135">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="b59b0-136">Konfigurace více projektů</span><span class="sxs-lookup"><span data-stu-id="b59b0-136">Configure multiple projects</span></span>

<span data-ttu-id="b59b0-137">Můžete vytvořit soubor **Directory. Build. props** , který obsahuje `<LangVersion>` element pro konfiguraci více adresářů.</span><span class="sxs-lookup"><span data-stu-id="b59b0-137">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="b59b0-138">Obvykle to provedete v adresáři řešení.</span><span class="sxs-lookup"><span data-stu-id="b59b0-138">You typically do that in your solution directory.</span></span> <span data-ttu-id="b59b0-139">Přidejte následující do souboru **Directory. Build. props** v adresáři řešení:</span><span class="sxs-lookup"><span data-stu-id="b59b0-139">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="b59b0-140">Nyní sestavení v každém podadresáři adresáře obsahujícího tento soubor použije verzi Preview C# .</span><span class="sxs-lookup"><span data-stu-id="b59b0-140">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="b59b0-141">Další informace naleznete v článku o [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="b59b0-141">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="b59b0-142">C#Referenční informace o jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="b59b0-142">C# language version reference</span></span>

<span data-ttu-id="b59b0-143">V následující tabulce jsou uvedeny všechny C# aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="b59b0-143">The following table shows all current C# language versions.</span></span> <span data-ttu-id="b59b0-144">Kompilátor nemusí nutně pochopit každou hodnotu, pokud je starší.</span><span class="sxs-lookup"><span data-stu-id="b59b0-144">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="b59b0-145">Pokud nainstalujete .NET Core 3,0, budete mít přístup ke všem uvedeným.</span><span class="sxs-lookup"><span data-stu-id="b59b0-145">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="b59b0-146">Value</span><span class="sxs-lookup"><span data-stu-id="b59b0-146">Value</span></span>|<span data-ttu-id="b59b0-147">Význam</span><span class="sxs-lookup"><span data-stu-id="b59b0-147">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="b59b0-148">preview</span><span class="sxs-lookup"><span data-stu-id="b59b0-148">preview</span></span>|<span data-ttu-id="b59b0-149">Kompilátor přijímá všechny platné jazykové syntaxe z nejnovější verze Preview.</span><span class="sxs-lookup"><span data-stu-id="b59b0-149">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="b59b0-150">latest</span><span class="sxs-lookup"><span data-stu-id="b59b0-150">latest</span></span>|<span data-ttu-id="b59b0-151">Kompilátor přijímá syntaxi z nejnovější vydané verze kompilátoru (včetně dílčí verze).</span><span class="sxs-lookup"><span data-stu-id="b59b0-151">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="b59b0-152">latestMajor</span><span class="sxs-lookup"><span data-stu-id="b59b0-152">latestMajor</span></span>|<span data-ttu-id="b59b0-153">Kompilátor přijímá syntaxi z poslední vydané hlavní verze kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b59b0-153">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="b59b0-154">8.0</span><span class="sxs-lookup"><span data-stu-id="b59b0-154">8.0</span></span>|<span data-ttu-id="b59b0-155">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 8,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="b59b0-155">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="b59b0-156">7.3</span><span class="sxs-lookup"><span data-stu-id="b59b0-156">7.3</span></span>|<span data-ttu-id="b59b0-157">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,3 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="b59b0-157">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="b59b0-158">7.2</span><span class="sxs-lookup"><span data-stu-id="b59b0-158">7.2</span></span>|<span data-ttu-id="b59b0-159">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,2 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="b59b0-159">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="b59b0-160">7.1</span><span class="sxs-lookup"><span data-stu-id="b59b0-160">7.1</span></span>|<span data-ttu-id="b59b0-161">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,1 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="b59b0-161">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="b59b0-162">7</span><span class="sxs-lookup"><span data-stu-id="b59b0-162">7</span></span>|<span data-ttu-id="b59b0-163">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="b59b0-163">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="b59b0-164">6</span><span class="sxs-lookup"><span data-stu-id="b59b0-164">6</span></span>|<span data-ttu-id="b59b0-165">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 6,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="b59b0-165">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="b59b0-166">5</span><span class="sxs-lookup"><span data-stu-id="b59b0-166">5</span></span>|<span data-ttu-id="b59b0-167">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 5,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="b59b0-167">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="b59b0-168">4</span><span class="sxs-lookup"><span data-stu-id="b59b0-168">4</span></span>|<span data-ttu-id="b59b0-169">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 4,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="b59b0-169">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="b59b0-170">3</span><span class="sxs-lookup"><span data-stu-id="b59b0-170">3</span></span>|<span data-ttu-id="b59b0-171">Kompilátor přijímá pouze syntaxi, která je obsažena C# v 3,0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="b59b0-171">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="b59b0-172">ISO-2</span><span class="sxs-lookup"><span data-stu-id="b59b0-172">ISO-2</span></span>|<span data-ttu-id="b59b0-173">Kompilátor přijímá pouze syntaxi, která je obsažena v normě ISO C# /IEC 23270:2006 (2,0)</span><span class="sxs-lookup"><span data-stu-id="b59b0-173">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="b59b0-174">ISO-1</span><span class="sxs-lookup"><span data-stu-id="b59b0-174">ISO-1</span></span>|<span data-ttu-id="b59b0-175">Kompilátor přijímá pouze syntaxi, která je obsažena v normě ISO C# /IEC 23270:2003 (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="b59b0-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
