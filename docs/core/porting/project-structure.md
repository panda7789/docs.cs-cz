---
title: Uspořádání projektů pro .NET Framework a .NET Core
description: Pomáhat pro vlastníky projektů, kteří chtějí kompilovat své řešení před .NET Framework a .NET Core souběžně.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777336"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="b17a2-103">Uspořádání projektu pro podporu .NET Framework a .NET Core</span><span class="sxs-lookup"><span data-stu-id="b17a2-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="b17a2-104">Můžete vytvořit řešení, které se zkompiluje jak pro .NET Framework, tak i .NET Core vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="b17a2-104">You can create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="b17a2-105">Tento článek se věnuje několika možnostem projektu – organizace, které vám pomůžou dosáhnout tohoto cíle.</span><span class="sxs-lookup"><span data-stu-id="b17a2-105">This article covers several project-organization options to help you achieve this goal.</span></span> <span data-ttu-id="b17a2-106">Tady jsou některé typické scénáře, které je potřeba vzít v úvahu při rozhodování o tom, jak nastavit rozložení projektu pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b17a2-106">Here are some typical scenarios to consider when you're deciding how to set up your project layout with .NET Core.</span></span> <span data-ttu-id="b17a2-107">Seznam nemusí zahrnovat všechno, co potřebujete; nastavte prioritu podle potřeb vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="b17a2-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="b17a2-108">**Kombinování stávajících projektů a projektů .NET Core do samostatných projektů**</span><span class="sxs-lookup"><span data-stu-id="b17a2-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="b17a2-109">*Co je dobré pro:*</span><span class="sxs-lookup"><span data-stu-id="b17a2-109">*What this is good for:*</span></span>
  - <span data-ttu-id="b17a2-110">Zjednodušuje proces sestavení kompilací jednoho projektu, nikoli více projektů, které každý cílí na jinou .NET Framework verzi nebo platformu.</span><span class="sxs-lookup"><span data-stu-id="b17a2-110">Simplifies your build process by compiling a single project rather than multiple projects that each target a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="b17a2-111">Zjednodušuje správu zdrojového souboru u projektů s více cíli, protože je nutné spravovat jeden soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="b17a2-111">Simplifies source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="b17a2-112">Když přidáváte nebo odebíráte zdrojové soubory, alternativy vyžadují ruční synchronizaci těchto souborů s ostatními projekty.</span><span class="sxs-lookup"><span data-stu-id="b17a2-112">When adding or removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="b17a2-113">Jednoduše vygenerujte balíček NuGet pro spotřebu.</span><span class="sxs-lookup"><span data-stu-id="b17a2-113">Easily generate a NuGet package for consumption.</span></span>
  - <span data-ttu-id="b17a2-114">Umožňuje psát kód pro konkrétní .NET Frameworkovou verzi v knihovnách pomocí direktiv kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b17a2-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="b17a2-115">*Nepodporované scénáře:*</span><span class="sxs-lookup"><span data-stu-id="b17a2-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="b17a2-116">Pro otevření stávajících projektů vyžaduje, aby vývojáři používali Visual Studio 2017 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="b17a2-116">Requires developers to use Visual Studio 2017 or a later version to open existing projects.</span></span> <span data-ttu-id="b17a2-117">Aby bylo možné podporovat starší verze sady Visual Studio, je lepší volbou [souborů projektu v různých složkách](#support-vs) .</span><span class="sxs-lookup"><span data-stu-id="b17a2-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="b17a2-118">[**Zachovat existující projekty a nové projekty .NET Core oddělené**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="b17a2-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="b17a2-119">*Co je dobré pro:*</span><span class="sxs-lookup"><span data-stu-id="b17a2-119">*What this is good for:*</span></span>
  - <span data-ttu-id="b17a2-120">Podporuje vývoj u stávajících projektů vývojářům a přispěvatelům, kteří nemusí mít Visual Studio 2017 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="b17a2-120">Supports development on existing projects for developers and contributors who may not have Visual Studio 2017 or a later version.</span></span>
  - <span data-ttu-id="b17a2-121">Snižuje možnost vytvářet nové chyby v existujících projektech, protože v těchto projektech není nutné žádné změny v kódu.</span><span class="sxs-lookup"><span data-stu-id="b17a2-121">Decreases the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="b17a2-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="b17a2-122">Example</span></span>

<span data-ttu-id="b17a2-123">Vezměte v úvahu úložiště níže:</span><span class="sxs-lookup"><span data-stu-id="b17a2-123">Consider the repository below:</span></span>

![Existující projekt](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="b17a2-125">**Zdrojový kód**</span><span class="sxs-lookup"><span data-stu-id="b17a2-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="b17a2-126">Následující článek popisuje několik způsobů, jak přidat podporu pro .NET Core pro toto úložiště v závislosti na omezeních a složitosti stávajících projektů.</span><span class="sxs-lookup"><span data-stu-id="b17a2-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="b17a2-127">Nahradit existující projekty více cíleným projektem .NET Core</span><span class="sxs-lookup"><span data-stu-id="b17a2-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="b17a2-128">Znovu uspořádejte úložiště tak, aby všechny existující *\*soubory. csproj* byly odebrány a byl vytvořen jediný soubor *\*. csproj* , který cílí na více platforem.</span><span class="sxs-lookup"><span data-stu-id="b17a2-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="b17a2-129">Jedná se o skvělou možnost, protože jeden projekt je schopný kompilovat pro různá rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b17a2-129">This is a great option, because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="b17a2-130">Má také možnost zvládnout různé možnosti kompilace a závislosti na cílové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b17a2-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Vytvoření csproj, který se zaměřuje na více platforem](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="b17a2-132">**Zdrojový kód**</span><span class="sxs-lookup"><span data-stu-id="b17a2-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="b17a2-133">Změny poznámky jsou:</span><span class="sxs-lookup"><span data-stu-id="b17a2-133">Changes to note are:</span></span>

- <span data-ttu-id="b17a2-134">Nahrazení souboru *Packages. config* a *\*. csproj* novým [rozhraním .NET Core *\*. csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span><span class="sxs-lookup"><span data-stu-id="b17a2-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="b17a2-135">Balíčky NuGet se zadává pomocí `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="b17a2-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="b17a2-136">Zachovat existující projekty a vytvořit projekt .NET Core</span><span class="sxs-lookup"><span data-stu-id="b17a2-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="b17a2-137">Pokud existují projekty, které jsou cíleny na starší verze rozhraní, je vhodné ponechat tyto projekty nezměněný a použít projekt .NET Core k zacílení budoucích rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b17a2-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Projekt .NET Core se stávajícím projektem v jiné složce](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="b17a2-139">**Zdrojový kód**</span><span class="sxs-lookup"><span data-stu-id="b17a2-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="b17a2-140">Rozhraní .NET Core a existující projekty jsou uchovávány v samostatných složkách.</span><span class="sxs-lookup"><span data-stu-id="b17a2-140">The .NET Core and existing projects are kept in separate folders.</span></span> <span data-ttu-id="b17a2-141">Udržování projektů v samostatných složkách zabraňuje vynucení sady Visual Studio 2017 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="b17a2-141">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="b17a2-142">Můžete vytvořit samostatné řešení, které otevírá jenom staré projekty.</span><span class="sxs-lookup"><span data-stu-id="b17a2-142">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="b17a2-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b17a2-143">See also</span></span>

- [<span data-ttu-id="b17a2-144">Dokumentace k portům .NET Core</span><span class="sxs-lookup"><span data-stu-id="b17a2-144">.NET Core porting documentation</span></span>](index.md)
