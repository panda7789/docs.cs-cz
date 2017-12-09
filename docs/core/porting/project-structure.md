---
title: "Uspořádání projektu pro podporu rozhraní .NET Framework a .NET Core"
description: "Nápověda pro vlastníky projektu, kteří chtějí zkompilovat své řešení pro rozhraní .NET Framework a .NET Core-souběžného."
keywords: "Rozhraní .NET, .NET core, rozhraní .NET Framework, rozložení projektu, více rozhraní"
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
ms.openlocfilehash: 93bec65e3bbee93855d6f5bce5e2d6cea8bb9f3d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a><span data-ttu-id="0ad80-104">Uspořádání projektu pro podporu rozhraní .NET Framework a .NET Core</span><span class="sxs-lookup"><span data-stu-id="0ad80-104">Organizing your project to support .NET Framework and .NET Core</span></span>

<span data-ttu-id="0ad80-105">Tento článek pomůže vlastníky projektu, kteří chtějí zkompilovat své řešení pro rozhraní .NET Framework a .NET Core-souběžného.</span><span class="sxs-lookup"><span data-stu-id="0ad80-105">This article helps project owners who want to compile their solution against .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="0ad80-106">Nabízí několik možností pro uspořádání projekty tak, aby pomoci vývojářům při dosažení tohoto cíle.</span><span class="sxs-lookup"><span data-stu-id="0ad80-106">It provides several options to organize projects to help developers achieve this goal.</span></span> <span data-ttu-id="0ad80-107">Následující seznam uvádí některé typické scénáře, které je třeba zvážit, když jste rozhodování, jak nastavit rozložení projektu s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ad80-107">The following list provides some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="0ad80-108">V seznamu nemusí zahrnovat všechny objekty, které chcete zjistit. určení priority podle potřeb vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="0ad80-108">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* <span data-ttu-id="0ad80-109">[**Existující projekty a .NET Core projekty zkombinovat do jednoho projektů**][option-csproj]</span><span class="sxs-lookup"><span data-stu-id="0ad80-109">[**Combine existing projects and .NET Core projects into single projects**][option-csproj]</span></span>

  <span data-ttu-id="0ad80-110">*Co to je vhodné pro:*</span><span class="sxs-lookup"><span data-stu-id="0ad80-110">*What this is good for:*</span></span>
  * <span data-ttu-id="0ad80-111">Ke zjednodušení procesu sestavení kompilování jeden projekt spíše než kompilování více projektů každý cílení na různé verze rozhraní .NET Framework nebo platformu.</span><span class="sxs-lookup"><span data-stu-id="0ad80-111">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="0ad80-112">Ke zjednodušení souboru správy zdrojů pro cílové více projektů, protože se musí spravovat jediného souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="0ad80-112">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="0ad80-113">Při přidávání nebo odebírání zdrojových souborů, alternativ vyžadují, abyste tato nastavení u jiných projekty synchronizovat ručně.</span><span class="sxs-lookup"><span data-stu-id="0ad80-113">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="0ad80-114">Snadno generování balíčku NuGet pro používání.</span><span class="sxs-lookup"><span data-stu-id="0ad80-114">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="0ad80-115">Můžete napsat kód pro konkrétní verzi rozhraní .NET Framework ve vašich knihovnách prostřednictvím direktivy kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0ad80-115">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="0ad80-116">*Nepodporované scénáře:*</span><span class="sxs-lookup"><span data-stu-id="0ad80-116">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="0ad80-117">Vyžaduje vývojářům používat Visual Studio 2017 otevřete existující projekty.</span><span class="sxs-lookup"><span data-stu-id="0ad80-117">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="0ad80-118">K podpoře starší verze sady Visual Studio, [udržování souborů projektu v různých složkách](#support-vs) není lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="0ad80-118">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="0ad80-119">[**Oddělit existující projekty a nové projekty .NET Core**][option-csproj-folder]</span><span class="sxs-lookup"><span data-stu-id="0ad80-119">[**Keep existing projects and new .NET Core projects separate**][option-csproj-folder]</span></span>

  <span data-ttu-id="0ad80-120">*Co to je vhodné pro:*</span><span class="sxs-lookup"><span data-stu-id="0ad80-120">*What this is good for:*</span></span>
  * <span data-ttu-id="0ad80-121">Pokračovat bez nutnosti upgradu pro vývojáře nebo přispěvatelé, kteří nemusí mít Visual Studio 2017 podporují vývoj na existující projekty.</span><span class="sxs-lookup"><span data-stu-id="0ad80-121">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="0ad80-122">Snížení možnost vytvoření nové chyby v existující projekty, protože žádné změny kódu se vyžaduje v těchto projektech.</span><span class="sxs-lookup"><span data-stu-id="0ad80-122">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="0ad80-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ad80-123">Example</span></span>

<span data-ttu-id="0ad80-124">Vezměte v úvahu následující úložiště:</span><span class="sxs-lookup"><span data-stu-id="0ad80-124">Consider the repository below:</span></span>

<span data-ttu-id="0ad80-125">![Existující projekt][example-initial-project]</span><span class="sxs-lookup"><span data-stu-id="0ad80-125">![Existing project][example-initial-project]</span></span>

<span data-ttu-id="0ad80-126">[**Zdrojový kód**][example-initial-project-code]</span><span class="sxs-lookup"><span data-stu-id="0ad80-126">[**Source Code**][example-initial-project-code]</span></span>

<span data-ttu-id="0ad80-127">Následující část popisuje několik způsobů, jak přidat podporu pro .NET Core pro toto úložiště v závislosti na složitosti existující projekty a omezení.</span><span class="sxs-lookup"><span data-stu-id="0ad80-127">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="0ad80-128">Nahradit existující projekty s projektem cílové více .NET Core</span><span class="sxs-lookup"><span data-stu-id="0ad80-128">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="0ad80-129">Reorganizovat úložiště, který všechny existující  *\*.csproj* soubory jsou odebrané a jednu  *\*.csproj* soubor je vytvořen zacílený více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0ad80-129">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="0ad80-130">Toto je skvělou možnost, protože jeden projekt je ke zkompilování pro různé rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0ad80-130">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="0ad80-131">Je také napájení pro zpracování různých kompilace možnosti a závislosti na cílové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0ad80-131">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

<span data-ttu-id="0ad80-132">![Vytvoření csproj, která je cílena více rozhraní][example-csproj]</span><span class="sxs-lookup"><span data-stu-id="0ad80-132">![Create an csproj that targets multiple frameworks][example-csproj]</span></span>

<span data-ttu-id="0ad80-133">[**Zdrojový kód**][example-csproj-code]</span><span class="sxs-lookup"><span data-stu-id="0ad80-133">[**Source Code**][example-csproj-code]</span></span>

<span data-ttu-id="0ad80-134">Poznámka: změny se:</span><span class="sxs-lookup"><span data-stu-id="0ad80-134">Changes to note are:</span></span>
* <span data-ttu-id="0ad80-135">Nahrazení *packages.config* a  *\*.csproj* s novou [.NET Core  *\*.csproj* ] [ example-csproj-netcore].</span><span class="sxs-lookup"><span data-stu-id="0ad80-135">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*][example-csproj-netcore].</span></span> <span data-ttu-id="0ad80-136">Balíčky NuGet se zadaným `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="0ad80-136">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="0ad80-137">Zachovat existující projekty a vytvoření projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="0ad80-137">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="0ad80-138">Pokud je existující projekty, které používají starší architektury, můžete ponechat beze změny těchto projektů a použití .NET Core projektu pro budoucí architektury.</span><span class="sxs-lookup"><span data-stu-id="0ad80-138">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

<span data-ttu-id="0ad80-139">![Projekt .NET core pomocí existující projekt v jiné složce][example-csproj-different-folder]</span><span class="sxs-lookup"><span data-stu-id="0ad80-139">![.NET Core project with existing project in different folder][example-csproj-different-folder]</span></span>

<span data-ttu-id="0ad80-140">[**Zdrojový kód**][example-csproj-different-code]</span><span class="sxs-lookup"><span data-stu-id="0ad80-140">[**Source Code**][example-csproj-different-code]</span></span>

<span data-ttu-id="0ad80-141">Poznámka: změny se:</span><span class="sxs-lookup"><span data-stu-id="0ad80-141">Changes to note are:</span></span>
* <span data-ttu-id="0ad80-142">.NET Core a existující projekty jsou uchovávány v samostatné složky.</span><span class="sxs-lookup"><span data-stu-id="0ad80-142">The .NET Core and existing projects are kept in separate folders.</span></span>
    * <span data-ttu-id="0ad80-143">Udržování projektů v samostatné složky zabraňuje vynucení, abyste měli Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="0ad80-143">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="0ad80-144">Můžete vytvořit samostatné řešení, které pouze otevře staré projekty.</span><span class="sxs-lookup"><span data-stu-id="0ad80-144">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ad80-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ad80-145">See Also</span></span>

<span data-ttu-id="0ad80-146">Podrobnosti najdete [.NET Core portování dokumentaci] [ porting-doc] o další pokyny k migraci na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ad80-146">Please see the [.NET Core porting documentation][porting-doc] for more guidance on migrating to .NET Core.</span></span>

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Existující projekt"
[example-initial-project-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Vytvoření csproj, která je cílena více rozhraní"
[example-csproj-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Projekt .NET core pomocí stávající PCL v jiné složce"
[example-csproj-different-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
