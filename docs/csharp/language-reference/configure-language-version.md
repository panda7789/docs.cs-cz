---
title: C#Správa verzí jazyka - C# Průvodce
description: Další informace o tom, jak C# jazykové verze je určena na základě vašeho projektu a jiné hodnoty lze upravit ručně ji.
ms.date: 07/10/2019
ms.openlocfilehash: e35fdf2bcdb1a31b752c760f3f6df59232e498a4
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236099"
---
# <a name="c-language-versioning"></a><span data-ttu-id="6b9a6-103">C#Správa verzí jazyka</span><span class="sxs-lookup"><span data-stu-id="6b9a6-103">C# language versioning</span></span>

<span data-ttu-id="6b9a6-104">C# Kompilátor Určuje výchozí jazykovou verzi na základě cílové rozhraní projektu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-104">The C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="6b9a6-105">Je to proto, C# jazyka může mít funkce, které závisí na typech nebo runtime komponenty, které nejsou k dispozici v každé implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="6b9a6-106">To také zajistí, že pro jakékoli cílové váš projekt se vytvořil proti, dostanete nejvyšší verze kompatibilní jazyka ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

## <a name="defaults"></a><span data-ttu-id="6b9a6-107">Ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="6b9a6-107">Defaults</span></span>

<span data-ttu-id="6b9a6-108">Kompilátor Určuje výchozí na základě těchto pravidel:</span><span class="sxs-lookup"><span data-stu-id="6b9a6-108">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="6b9a6-109">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="6b9a6-109">Target framework</span></span>|<span data-ttu-id="6b9a6-110">verze</span><span class="sxs-lookup"><span data-stu-id="6b9a6-110">version</span></span>|<span data-ttu-id="6b9a6-111">C#Výchozí verze jazyka</span><span class="sxs-lookup"><span data-stu-id="6b9a6-111">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="6b9a6-112">.NET Core</span><span class="sxs-lookup"><span data-stu-id="6b9a6-112">.NET Core</span></span>|<span data-ttu-id="6b9a6-113">3.x</span><span class="sxs-lookup"><span data-stu-id="6b9a6-113">3.x</span></span>|<span data-ttu-id="6b9a6-114">C#8.0</span><span class="sxs-lookup"><span data-stu-id="6b9a6-114">C# 8.0</span></span>|
|<span data-ttu-id="6b9a6-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="6b9a6-115">.NET Core</span></span>|<span data-ttu-id="6b9a6-116">2.x</span><span class="sxs-lookup"><span data-stu-id="6b9a6-116">2.x</span></span>|<span data-ttu-id="6b9a6-117">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="6b9a6-117">C# 7.3</span></span>|
|<span data-ttu-id="6b9a6-118">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="6b9a6-118">.NET Standard</span></span>|<span data-ttu-id="6b9a6-119">všechny</span><span class="sxs-lookup"><span data-stu-id="6b9a6-119">all</span></span>|<span data-ttu-id="6b9a6-120">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="6b9a6-120">C# 7.3</span></span>|
|<span data-ttu-id="6b9a6-121">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="6b9a6-121">.NET Framework</span></span>|<span data-ttu-id="6b9a6-122">všechny</span><span class="sxs-lookup"><span data-stu-id="6b9a6-122">all</span></span>|<span data-ttu-id="6b9a6-123">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="6b9a6-123">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="6b9a6-124">Výchozí nastavení pro verze Preview</span><span class="sxs-lookup"><span data-stu-id="6b9a6-124">Default for previews</span></span>

<span data-ttu-id="6b9a6-125">Když váš projekt cílí na verzi preview rozhraní, které obsahuje odpovídající jazykovou verzi preview, je jazyková verze používá jazykovou verzi preview.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-125">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="6b9a6-126">Tím se zajistí, že můžete použít nejnovější funkce, které jsou zaručeny pracovat v této verzi preview v jakémkoli prostředí bez ovlivnění vašich projektů cílených vydanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-126">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="overriding-a-default"></a><span data-ttu-id="6b9a6-127">Přepsání výchozího</span><span class="sxs-lookup"><span data-stu-id="6b9a6-127">Overriding a default</span></span>

<span data-ttu-id="6b9a6-128">Pokud je nutné zadat vaše C# verze explicitně, lze provést několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="6b9a6-128">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="6b9a6-129">Ručně upravit vaše [soubor projektu](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="6b9a6-129">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="6b9a6-130">Nastavit jazykovou verzi [pro více projektů v podadresáři](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="6b9a6-130">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="6b9a6-131">Konfigurace [ `-langversion` – možnost kompilátoru](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="6b9a6-131">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="6b9a6-132">Úprava souboru projektu</span><span class="sxs-lookup"><span data-stu-id="6b9a6-132">Edit the project file</span></span>

<span data-ttu-id="6b9a6-133">V souboru projektu můžete nastavit jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-133">You can set the language version in your project file.</span></span> <span data-ttu-id="6b9a6-134">Například pokud chcete explicitně přístup k funkce ve verzi preview, můžete přidat element následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6b9a6-134">For example, if you explicitly wanted access to preview features, you could do add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="6b9a6-135">Hodnota `preview` používá nejnovější dostupné verze preview C# jazyk, který kompilátor podporuje.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-135">The value `preview` uses the latest available preview C# language that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="6b9a6-136">Konfigurace více projektů</span><span class="sxs-lookup"><span data-stu-id="6b9a6-136">Configure multiple projects</span></span>

<span data-ttu-id="6b9a6-137">Můžete vytvořit **Directory.Build.props** soubor, který obsahuje `<LangVersion>` prvek, který chcete nakonfigurovat více adresářů.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-137">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="6b9a6-138">Obvykle to uděláte ve svém adresáři řešení.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-138">You typically do that in your solution directory.</span></span> <span data-ttu-id="6b9a6-139">Přidejte následující text do **Directory.Build.props** soubor v adresáři řešení:</span><span class="sxs-lookup"><span data-stu-id="6b9a6-139">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="6b9a6-140">Nyní, sestavení v každé podadresáře adresáře, který obsahuje tento soubor bude používat verzi preview C# verze.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-140">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="6b9a6-141">Další informace najdete v článku na [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="6b9a6-141">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="6b9a6-142">C#referenční informace k jazyku verze</span><span class="sxs-lookup"><span data-stu-id="6b9a6-142">C# language version reference</span></span>

<span data-ttu-id="6b9a6-143">V následující tabulce jsou uvedeny všechny aktuální C# jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-143">The following table shows all current C# language versions.</span></span> <span data-ttu-id="6b9a6-144">Váš kompilátor nemusí pochopit nutně každá hodnota, pokud je starší.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-144">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="6b9a6-145">Pokud nainstalujete .NET Core 3.0, bude mít přístup ke všemu, co jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-145">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="6b9a6-146">Value</span><span class="sxs-lookup"><span data-stu-id="6b9a6-146">Value</span></span>|<span data-ttu-id="6b9a6-147">Význam</span><span class="sxs-lookup"><span data-stu-id="6b9a6-147">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="6b9a6-148">preview</span><span class="sxs-lookup"><span data-stu-id="6b9a6-148">preview</span></span>|<span data-ttu-id="6b9a6-149">Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější verze preview.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-149">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="6b9a6-150">latest</span><span class="sxs-lookup"><span data-stu-id="6b9a6-150">latest</span></span>|<span data-ttu-id="6b9a6-151">Kompilátor přijímá syntaxi z nejnovější vydanou verzi kompilátoru (včetně vedlejší verze aktualizace).</span><span class="sxs-lookup"><span data-stu-id="6b9a6-151">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="6b9a6-152">latestMajor</span><span class="sxs-lookup"><span data-stu-id="6b9a6-152">latestMajor</span></span>|<span data-ttu-id="6b9a6-153">Kompilátor přijímá syntaxi z nejnovější vydanou hlavní verzi kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-153">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="6b9a6-154">8.0</span><span class="sxs-lookup"><span data-stu-id="6b9a6-154">8.0</span></span>|<span data-ttu-id="6b9a6-155">Kompilátor přijímá pouze syntaxi, která je součástí C# 8.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-155">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="6b9a6-156">7.3</span><span class="sxs-lookup"><span data-stu-id="6b9a6-156">7.3</span></span>|<span data-ttu-id="6b9a6-157">Kompilátor přijímá pouze syntaxi, která je součástí C# 7.3 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-157">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="6b9a6-158">7.2</span><span class="sxs-lookup"><span data-stu-id="6b9a6-158">7.2</span></span>|<span data-ttu-id="6b9a6-159">Kompilátor přijímá pouze syntaxi, která je součástí C# 7.2 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-159">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="6b9a6-160">7.1</span><span class="sxs-lookup"><span data-stu-id="6b9a6-160">7.1</span></span>|<span data-ttu-id="6b9a6-161">Kompilátor přijímá pouze syntaxi, která je součástí C# 7.1 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-161">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="6b9a6-162">7</span><span class="sxs-lookup"><span data-stu-id="6b9a6-162">7</span></span>|<span data-ttu-id="6b9a6-163">Kompilátor přijímá pouze syntaxi, která je součástí C# 7.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-163">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="6b9a6-164">6</span><span class="sxs-lookup"><span data-stu-id="6b9a6-164">6</span></span>|<span data-ttu-id="6b9a6-165">Kompilátor přijímá pouze syntaxi, která je součástí C# 6.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-165">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="6b9a6-166">5</span><span class="sxs-lookup"><span data-stu-id="6b9a6-166">5</span></span>|<span data-ttu-id="6b9a6-167">Kompilátor přijímá pouze syntaxi, která je součástí C# 5.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-167">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="6b9a6-168">4</span><span class="sxs-lookup"><span data-stu-id="6b9a6-168">4</span></span>|<span data-ttu-id="6b9a6-169">Kompilátor přijímá pouze syntaxi, která je součástí C# 4.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-169">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="6b9a6-170">3</span><span class="sxs-lookup"><span data-stu-id="6b9a6-170">3</span></span>|<span data-ttu-id="6b9a6-171">Kompilátor přijímá pouze syntaxi, která je součástí C# 3.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-171">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="6b9a6-172">ISO-2</span><span class="sxs-lookup"><span data-stu-id="6b9a6-172">ISO-2</span></span>|<span data-ttu-id="6b9a6-173">Kompilátor přijímá pouze syntaxi, která je součástí 23270: ISO/IEC 2006 C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="6b9a6-173">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="6b9a6-174">ISO-1</span><span class="sxs-lookup"><span data-stu-id="6b9a6-174">ISO-1</span></span>|<span data-ttu-id="6b9a6-175">Kompilátor přijímá pouze syntaxi, která je součástí 23270: ISO/IEC 2003 C# (1.0 nebo 1.2)</span><span class="sxs-lookup"><span data-stu-id="6b9a6-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
