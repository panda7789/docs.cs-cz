---
title: Jazyková verze jazyka c# – Průvodce jazyka C#
description: Přečtěte si informace o tom, jak je jazyková verze jazyka C# určena na základě vašeho projektu a z důvodů na základě této volby. Přečtěte si, jak přepsat výchozí nastavení ručně.
ms.custom: updateeachrelease
ms.date: 05/20/2020
ms.openlocfilehash: a27f3210f399f1bed190c18d778cf3824772d576
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656848"
---
# <a name="c-language-versioning"></a><span data-ttu-id="e5b12-104">Správa verzí jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e5b12-104">C# language versioning</span></span>

<span data-ttu-id="e5b12-105">Nejnovější kompilátor C# určuje výchozí jazykovou verzi na základě cílových rozhraní architektury vašeho projektu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e5b12-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="e5b12-106">Visual Studio neposkytuje uživatelské rozhraní pro změnu hodnoty, ale můžete ho změnit úpravou souboru *csproj* .</span><span class="sxs-lookup"><span data-stu-id="e5b12-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="e5b12-107">Volba výchozí zajistí, že používáte nejnovější verzi jazyka kompatibilní s vaší cílovou architekturou.</span><span class="sxs-lookup"><span data-stu-id="e5b12-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="e5b12-108">Můžete využívat přístup k nejnovějším funkcím jazyka kompatibilním s cílem vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="e5b12-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="e5b12-109">Tato výchozí volba také zajišťuje, že nebudete používat jazyk, který vyžaduje typy nebo běhové chování, které není v cílové architektuře k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e5b12-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="e5b12-110">Výběr jazykové verze, která je novější než výchozí, může způsobit, že bude obtížné diagnostikovat chyby při kompilaci a za běhu.</span><span class="sxs-lookup"><span data-stu-id="e5b12-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="e5b12-111">Pravidla v tomto článku se vztahují na kompilátor dodaný se sadou Visual Studio 2019 nebo .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="e5b12-111">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="e5b12-112">Kompilátory jazyka C#, které jsou součástí instalace sady Visual Studio 2017 nebo starší verze .NET Core SDK v jazyce C# 7,0 ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e5b12-112">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span>

<span data-ttu-id="e5b12-113">C# 8,0 (a vyšší) jsou podporovány pouze v .NET Core 3. x a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="e5b12-113">C# 8.0 (and higher) is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="e5b12-114">Mnohé z nejnovějších funkcí vyžadují knihovnu a běhové funkce, které jsou představené v .NET Core 3. x:</span><span class="sxs-lookup"><span data-stu-id="e5b12-114">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="e5b12-115">[Implementace výchozího rozhraní](../whats-new/csharp-8.md#default-interface-methods) vyžaduje nové funkce v .net Core 3,0 CLR.</span><span class="sxs-lookup"><span data-stu-id="e5b12-115">[Default interface implementation](../whats-new/csharp-8.md#default-interface-methods) requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="e5b12-116">[Asynchronní datové proudy](../whats-new/csharp-8.md#asynchronous-streams) vyžadují nové typy <xref:System.IAsyncDisposable?displayProperty=nameWithType> , <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> a <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e5b12-116">[Async streams](../whats-new/csharp-8.md#asynchronous-streams) require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="e5b12-117">[Indexy a rozsahy](../whats-new/csharp-8.md#indices-and-ranges) vyžadují nové typy <xref:System.Index?displayProperty=nameWithType> a <xref:System.Range?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e5b12-117">[Indices and ranges](../whats-new/csharp-8.md#indices-and-ranges) require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="e5b12-118">[Typy odkazů s možnou hodnotou null](../whats-new/csharp-8.md#nullable-reference-types) umožňují použití několika [atributů](attributes/nullable-analysis.md) k poskytnutí lepších upozornění.</span><span class="sxs-lookup"><span data-stu-id="e5b12-118">[Nullable reference types](../whats-new/csharp-8.md#nullable-reference-types) make use of several [attributes](attributes/nullable-analysis.md) to provide better warnings.</span></span> <span data-ttu-id="e5b12-119">Tyto atributy se přidaly do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="e5b12-119">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="e5b12-120">Jiné cílové architektury nebyly opatřeny poznámkami žádné z těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="e5b12-120">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="e5b12-121">To znamená, že upozornění s možnou hodnotou null nemusí přesně odrážet možné problémy.</span><span class="sxs-lookup"><span data-stu-id="e5b12-121">That means nullable warnings may not accurately reflect potential issues.</span></span>

## <a name="defaults"></a><span data-ttu-id="e5b12-122">Ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="e5b12-122">Defaults</span></span>

<span data-ttu-id="e5b12-123">Kompilátor určuje výchozí hodnotu na základě těchto pravidel:</span><span class="sxs-lookup"><span data-stu-id="e5b12-123">The compiler determines a default based on these rules:</span></span>

| <span data-ttu-id="e5b12-124">Cílová architektura</span><span class="sxs-lookup"><span data-stu-id="e5b12-124">Target framework</span></span> | <span data-ttu-id="e5b12-125">verze</span><span class="sxs-lookup"><span data-stu-id="e5b12-125">version</span></span> | <span data-ttu-id="e5b12-126">Výchozí verze jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e5b12-126">C# language version default</span></span> |
|------------------|---------|-----------------------------|
| <span data-ttu-id="e5b12-127">.NET Core</span><span class="sxs-lookup"><span data-stu-id="e5b12-127">.NET Core</span></span>        | <span data-ttu-id="e5b12-128">3.x</span><span class="sxs-lookup"><span data-stu-id="e5b12-128">3.x</span></span>     | <span data-ttu-id="e5b12-129">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="e5b12-129">C# 8.0</span></span>                      |
| <span data-ttu-id="e5b12-130">.NET Core</span><span class="sxs-lookup"><span data-stu-id="e5b12-130">.NET Core</span></span>        | <span data-ttu-id="e5b12-131">2.x</span><span class="sxs-lookup"><span data-stu-id="e5b12-131">2.x</span></span>     | <span data-ttu-id="e5b12-132">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="e5b12-132">C# 7.3</span></span>                      |
| <span data-ttu-id="e5b12-133">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="e5b12-133">.NET Standard</span></span>    | <span data-ttu-id="e5b12-134">2.1</span><span class="sxs-lookup"><span data-stu-id="e5b12-134">2.1</span></span>     | <span data-ttu-id="e5b12-135">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="e5b12-135">C# 8.0</span></span>                      |
| <span data-ttu-id="e5b12-136">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="e5b12-136">.NET Standard</span></span>    | <span data-ttu-id="e5b12-137">2.0</span><span class="sxs-lookup"><span data-stu-id="e5b12-137">2.0</span></span>     | <span data-ttu-id="e5b12-138">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="e5b12-138">C# 7.3</span></span>                      |
| <span data-ttu-id="e5b12-139">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="e5b12-139">.NET Standard</span></span>    | <span data-ttu-id="e5b12-140">verze</span><span class="sxs-lookup"><span data-stu-id="e5b12-140">1.x</span></span>     | <span data-ttu-id="e5b12-141">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="e5b12-141">C# 7.3</span></span>                      |
| <span data-ttu-id="e5b12-142">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="e5b12-142">.NET Framework</span></span>   | <span data-ttu-id="e5b12-143">Vše</span><span class="sxs-lookup"><span data-stu-id="e5b12-143">all</span></span>     | <span data-ttu-id="e5b12-144">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="e5b12-144">C# 7.3</span></span>                      |

<span data-ttu-id="e5b12-145">Když se váš projekt zaměřuje na architekturu verze Preview, která má odpovídající jazykovou verzi Preview, bude použit jazyk verze Preview.</span><span class="sxs-lookup"><span data-stu-id="e5b12-145">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="e5b12-146">Nejnovější funkce v rámci této verze Preview můžete používat v jakémkoli prostředí, aniž by to ovlivnilo projekty, které cílí na vydanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5b12-146">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="e5b12-147">Přepsat výchozí</span><span class="sxs-lookup"><span data-stu-id="e5b12-147">Override a default</span></span>

<span data-ttu-id="e5b12-148">Pokud je nutné explicitně zadat verzi C#, můžete to provést několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="e5b12-148">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="e5b12-149">Ručně upravte [soubor projektu](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="e5b12-149">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="e5b12-150">Nastaví jazykovou verzi [pro více projektů v podadresáři](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="e5b12-150">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="e5b12-151">Nakonfigurujte [ `-langversion` možnost kompilátoru](compiler-options/langversion-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="e5b12-151">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="e5b12-152">Upravit soubor projektu</span><span class="sxs-lookup"><span data-stu-id="e5b12-152">Edit the project file</span></span>

<span data-ttu-id="e5b12-153">V souboru projektu můžete nastavit jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="e5b12-153">You can set the language version in your project file.</span></span> <span data-ttu-id="e5b12-154">Například pokud výslovně chcete získat přístup k funkcím verze Preview, přidejte prvek podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="e5b12-154">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="e5b12-155">Hodnota `preview` používá nejnovější verzi Preview jazyka C#, kterou podporuje kompilátor.</span><span class="sxs-lookup"><span data-stu-id="e5b12-155">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="e5b12-156">Konfigurace více projektů</span><span class="sxs-lookup"><span data-stu-id="e5b12-156">Configure multiple projects</span></span>

<span data-ttu-id="e5b12-157">Chcete-li konfigurovat více projektů, můžete vytvořit soubor **Directory. Build. props** , který obsahuje `<LangVersion>` element.</span><span class="sxs-lookup"><span data-stu-id="e5b12-157">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="e5b12-158">Obvykle to provedete v adresáři řešení.</span><span class="sxs-lookup"><span data-stu-id="e5b12-158">You typically do that in your solution directory.</span></span> <span data-ttu-id="e5b12-159">Přidejte následující do souboru **Directory. Build. props** v adresáři řešení:</span><span class="sxs-lookup"><span data-stu-id="e5b12-159">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="e5b12-160">Sestavení ve všech podadresářích adresáře obsahujícího tento soubor budou používat verzi Preview jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e5b12-160">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="e5b12-161">Další informace naleznete v článku o [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="e5b12-161">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="e5b12-162">Referenční informace o verzi jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e5b12-162">C# language version reference</span></span>

<span data-ttu-id="e5b12-163">V následující tabulce jsou uvedeny všechny aktuální jazykové verze jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e5b12-163">The following table shows all current C# language versions.</span></span> <span data-ttu-id="e5b12-164">Kompilátor nemusí nutně pochopit každou hodnotu, pokud je starší.</span><span class="sxs-lookup"><span data-stu-id="e5b12-164">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="e5b12-165">Pokud instalujete .NET Core 3,0 nebo novější, máte k dispozici přístup k všechno uvedenému.</span><span class="sxs-lookup"><span data-stu-id="e5b12-165">If you install .NET Core 3.0 or later, then you have access to everything listed.</span></span>

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> <span data-ttu-id="e5b12-166">Otevřete [Developer Command Prompt pro sadu Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md)a spuštěním následujícího příkazu zobrazte seznam jazykových verzí, které jsou na vašem počítači k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e5b12-166">Open the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), and run the following command to see the listing of language versions available on your machine.</span></span>
>
> ```CMD
> csc -langversion:?
> ```
>
> <span data-ttu-id="e5b12-167">Po dotazování možnosti kompilace [-langversion –](compiler-options/langversion-compiler-option.md) bude vytištěna podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e5b12-167">Questioning the [-langversion](compiler-options/langversion-compiler-option.md) compile option like this, will print something similar to the following:</span></span>
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0 (default)
> latestmajor
> preview
> latest
> ```
