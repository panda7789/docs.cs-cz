---
title: Uspořádání projektů pro .NET Framework a .NET Core
description: Pomáhat pro vlastníky projektů, kteří chtějí kompilovat své řešení před .NET Framework a .NET Core souběžně.
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 1e120e1aee60e88ea33a8290f3bf36eb93bfc91c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698938"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="494ab-103">Uspořádání projektu pro podporu .NET Framework a .NET Core</span><span class="sxs-lookup"><span data-stu-id="494ab-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="494ab-104">Přečtěte si, jak vytvořit řešení, které se zkompiluje jak pro .NET Framework, tak i .NET Core souběžně.</span><span class="sxs-lookup"><span data-stu-id="494ab-104">Learn how to create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="494ab-105">Prohlédněte si několik možností uspořádání projektů, které vám pomůžou dosáhnout tohoto cíle.</span><span class="sxs-lookup"><span data-stu-id="494ab-105">See several options to organize projects to help you achieve this goal.</span></span> <span data-ttu-id="494ab-106">Tady jsou některé typické scénáře, které je potřeba vzít v úvahu při rozhodování, jak nastavit rozložení projektu pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="494ab-106">Here are some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="494ab-107">Seznam nemusí zahrnovat všechno, co potřebujete; nastavte prioritu podle potřeb vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="494ab-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* [<span data-ttu-id="494ab-108">**Kombinování stávajících projektů a projektů .NET Core do samostatných projektů**</span><span class="sxs-lookup"><span data-stu-id="494ab-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="494ab-109">*Co je dobré pro:*</span><span class="sxs-lookup"><span data-stu-id="494ab-109">*What this is good for:*</span></span>
  * <span data-ttu-id="494ab-110">Zjednodušení procesu sestavení kompilováním jediného projektu namísto kompilace více projektů, z nichž každý cílí na jinou .NET Framework verzi nebo platformu.</span><span class="sxs-lookup"><span data-stu-id="494ab-110">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="494ab-111">Zjednodušení správy zdrojového souboru pro projekty cílené na více lokalit, protože je nutné spravovat jeden soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="494ab-111">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="494ab-112">Když přidáváte nebo odebíráte zdrojové soubory, alternativy vyžadují ruční synchronizaci těchto souborů s ostatními projekty.</span><span class="sxs-lookup"><span data-stu-id="494ab-112">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="494ab-113">Snadné generování balíčku NuGet pro spotřebu</span><span class="sxs-lookup"><span data-stu-id="494ab-113">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="494ab-114">Umožňuje psát kód pro konkrétní .NET Frameworkovou verzi v knihovnách pomocí direktiv kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="494ab-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="494ab-115">*Nepodporované scénáře:*</span><span class="sxs-lookup"><span data-stu-id="494ab-115">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="494ab-116">Pro otevření stávajících projektů vyžaduje, aby vývojáři používali Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="494ab-116">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="494ab-117">Aby bylo možné podporovat starší verze sady Visual Studio, je lepší volbou [souborů projektu v různých složkách](#support-vs) .</span><span class="sxs-lookup"><span data-stu-id="494ab-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="494ab-118">[**Zachovat existující projekty a nové projekty .NET Core oddělené**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="494ab-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="494ab-119">*Co je dobré pro:*</span><span class="sxs-lookup"><span data-stu-id="494ab-119">*What this is good for:*</span></span>
  * <span data-ttu-id="494ab-120">Pokračování v podpoře vývoje u stávajících projektů bez nutnosti upgradu pro vývojáře a přispěvatele, kteří nemusí mít Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="494ab-120">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="494ab-121">Snížení možnosti vytváření nových chyb v existujících projektech, protože v těchto projektech nejsou vyžadovány žádné změny kódu.</span><span class="sxs-lookup"><span data-stu-id="494ab-121">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="494ab-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="494ab-122">Example</span></span>

<span data-ttu-id="494ab-123">Vezměte v úvahu úložiště níže:</span><span class="sxs-lookup"><span data-stu-id="494ab-123">Consider the repository below:</span></span>

![Existující projekt](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="494ab-125">**Zdrojový kód**</span><span class="sxs-lookup"><span data-stu-id="494ab-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="494ab-126">Následující článek popisuje několik způsobů, jak přidat podporu pro .NET Core pro toto úložiště v závislosti na omezeních a složitosti stávajících projektů.</span><span class="sxs-lookup"><span data-stu-id="494ab-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="494ab-127">Nahradit existující projekty více cíleným projektem .NET Core</span><span class="sxs-lookup"><span data-stu-id="494ab-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="494ab-128">Reorganizovat úložiště tak, aby všechny existující *@no__t soubory. csproj* byly odebrány a byl vytvořen jeden *@no__t -3. csproj* , který cílí na více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="494ab-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="494ab-129">Tato možnost je skvělá, protože jeden projekt je schopný kompilovat pro různá rozhraní.</span><span class="sxs-lookup"><span data-stu-id="494ab-129">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="494ab-130">Má také možnost zvládnout různé možnosti kompilace a závislosti na cílové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="494ab-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Vytvoření hodnoty csproj, která cílí na více platforem](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="494ab-132">**Zdrojový kód**</span><span class="sxs-lookup"><span data-stu-id="494ab-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="494ab-133">Změny poznámky jsou:</span><span class="sxs-lookup"><span data-stu-id="494ab-133">Changes to note are:</span></span>

* <span data-ttu-id="494ab-134">Nahrazení souboru *Packages. config* a *@no__t -2. csproj* pomocí nového [rozhraní .NET Core *@no__t -5. csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span><span class="sxs-lookup"><span data-stu-id="494ab-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="494ab-135">Balíčky NuGet jsou zadané s `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="494ab-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="494ab-136">Zachovat existující projekty a vytvořit projekt .NET Core</span><span class="sxs-lookup"><span data-stu-id="494ab-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="494ab-137">Pokud existují projekty, které jsou cíleny na starší verze rozhraní, je vhodné ponechat tyto projekty nezměněný a použít projekt .NET Core k zacílení budoucích rozhraní.</span><span class="sxs-lookup"><span data-stu-id="494ab-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Projekt .NET Core se stávajícím projektem v jiné složce](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="494ab-139">**Zdrojový kód**</span><span class="sxs-lookup"><span data-stu-id="494ab-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="494ab-140">Změny poznámky jsou:</span><span class="sxs-lookup"><span data-stu-id="494ab-140">Changes to note are:</span></span>

* <span data-ttu-id="494ab-141">Rozhraní .NET Core a existující projekty jsou uchovávány v samostatných složkách.</span><span class="sxs-lookup"><span data-stu-id="494ab-141">The .NET Core and existing projects are kept in separate folders.</span></span>
  * <span data-ttu-id="494ab-142">Udržování projektů v samostatných složkách zabraňuje vynucení sady Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="494ab-142">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="494ab-143">Můžete vytvořit samostatné řešení, které otevírá jenom staré projekty.</span><span class="sxs-lookup"><span data-stu-id="494ab-143">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="494ab-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="494ab-144">See also</span></span>

- [<span data-ttu-id="494ab-145">Dokumentace k portům .NET Core</span><span class="sxs-lookup"><span data-stu-id="494ab-145">.NET Core porting documentation</span></span>](index.md)
