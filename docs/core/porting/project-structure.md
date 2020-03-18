---
title: Uspořádání projektů pro rozhraní .NET Framework a .NET Core
description: Nápověda pro vlastníky projektu, kteří chtějí zkompilovat své řešení proti rozhraní .NET Framework a .NET Core vedle sebe.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75777336"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="3df61-103">Uspořádání projektu pro podporu rozhraní .NET Framework i .NET Core</span><span class="sxs-lookup"><span data-stu-id="3df61-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="3df61-104">Můžete vytvořit řešení, které se zkompiluje pro rozhraní .NET Framework i .NET Core vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="3df61-104">You can create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="3df61-105">Tento článek popisuje několik možností organizace projektu, které vám pomohou dosáhnout tohoto cíle.</span><span class="sxs-lookup"><span data-stu-id="3df61-105">This article covers several project-organization options to help you achieve this goal.</span></span> <span data-ttu-id="3df61-106">Zde jsou některé typické scénáře, které je třeba zvážit při rozhodování o tom, jak nastavit rozložení projektu pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3df61-106">Here are some typical scenarios to consider when you're deciding how to set up your project layout with .NET Core.</span></span> <span data-ttu-id="3df61-107">Seznam nemusí zahrnovat vše, co chcete; priority na základě potřeb projektu.</span><span class="sxs-lookup"><span data-stu-id="3df61-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="3df61-108">**Sloučení stávajících projektů a základních projektů .NET do jednotlivých projektů**</span><span class="sxs-lookup"><span data-stu-id="3df61-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="3df61-109">*K čemu je to dobré:*</span><span class="sxs-lookup"><span data-stu-id="3df61-109">*What this is good for:*</span></span>
  - <span data-ttu-id="3df61-110">Zjednodušuje proces sestavení kompilací jednoho projektu, nikoli více projektů, které každý cílí na jinou verzi rozhraní .NET Framework nebo platformu.</span><span class="sxs-lookup"><span data-stu-id="3df61-110">Simplifies your build process by compiling a single project rather than multiple projects that each target a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="3df61-111">Zjednodušuje správu zdrojových souborů pro víceúčelové projekty, protože je nutné spravovat jeden soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="3df61-111">Simplifies source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="3df61-112">Při přidávání nebo odebírání zdrojových souborů vyžadují alternativy jejich ruční synchronizaci s ostatními projekty.</span><span class="sxs-lookup"><span data-stu-id="3df61-112">When adding or removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="3df61-113">Snadno generovat balíček NuGet pro spotřebu.</span><span class="sxs-lookup"><span data-stu-id="3df61-113">Easily generate a NuGet package for consumption.</span></span>
  - <span data-ttu-id="3df61-114">Umožňuje psát kód pro konkrétní verzi rozhraní .NET Framework v knihovnách pomocí direktiv kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="3df61-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="3df61-115">*Nepodporované scénáře:*</span><span class="sxs-lookup"><span data-stu-id="3df61-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="3df61-116">Vyžaduje, aby vývojáři k otevření existujících projektů používali Visual Studio 2017 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="3df61-116">Requires developers to use Visual Studio 2017 or a later version to open existing projects.</span></span> <span data-ttu-id="3df61-117">Chcete-li podporovat starší verze sady Visual Studio, je lepší volbou [uchovávat soubory projektu v různých složkách.](#support-vs)</span><span class="sxs-lookup"><span data-stu-id="3df61-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="3df61-118">[**Zachování samostatných existujících projektů a nových projektů .NET Core**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="3df61-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="3df61-119">*K čemu je to dobré:*</span><span class="sxs-lookup"><span data-stu-id="3df61-119">*What this is good for:*</span></span>
  - <span data-ttu-id="3df61-120">Podporuje vývoj existujících projektů pro vývojáře a přispěvatele, kteří nemusí mít Visual Studio 2017 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="3df61-120">Supports development on existing projects for developers and contributors who may not have Visual Studio 2017 or a later version.</span></span>
  - <span data-ttu-id="3df61-121">Snižuje možnost vytváření nových chyb v existujících projektech, protože v těchto projektech není vyžadována žádná konve kódu.</span><span class="sxs-lookup"><span data-stu-id="3df61-121">Decreases the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="3df61-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="3df61-122">Example</span></span>

<span data-ttu-id="3df61-123">Zvažte úložiště níže:</span><span class="sxs-lookup"><span data-stu-id="3df61-123">Consider the repository below:</span></span>

![Stávající projekt](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="3df61-125">**Zdrojový kód**</span><span class="sxs-lookup"><span data-stu-id="3df61-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="3df61-126">Následující popisuje několik způsobů, jak přidat podporu pro .NET Core pro toto úložiště v závislosti na omezení a složitost i existující projekty.</span><span class="sxs-lookup"><span data-stu-id="3df61-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="3df61-127">Nahrazení stávajících projektů víceúčelovým projektem .NET Core</span><span class="sxs-lookup"><span data-stu-id="3df61-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="3df61-128">Reorganizovat úložiště tak, aby všechny existující \* \*soubory .csproj\* byly odebrány a jeden \* \*soubor .csproj\* je vytvořen, který se zaměřuje na více rámců.</span><span class="sxs-lookup"><span data-stu-id="3df61-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="3df61-129">To je skvělá volba, protože jeden projekt je schopen kompilovat pro různé architektury.</span><span class="sxs-lookup"><span data-stu-id="3df61-129">This is a great option, because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="3df61-130">Má také pravomoc zpracovávat různé možnosti kompilace a závislosti na cílové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3df61-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Vytvořte csproj, který se zaměřuje na více rámců](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="3df61-132">**Zdrojový kód**</span><span class="sxs-lookup"><span data-stu-id="3df61-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="3df61-133">Změny poznámky jsou:</span><span class="sxs-lookup"><span data-stu-id="3df61-133">Changes to note are:</span></span>

- <span data-ttu-id="3df61-134">Nahrazení *packages.config* a \* \*.csproj\* novým [.NET Core \* \*.csproj\*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span><span class="sxs-lookup"><span data-stu-id="3df61-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="3df61-135">Balíčky NuGet `<PackageReference> ItemGroup`jsou určeny pomocí služby .</span><span class="sxs-lookup"><span data-stu-id="3df61-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="3df61-136">Zachovat existující projekty a vytvořit projekt .NET Core</span><span class="sxs-lookup"><span data-stu-id="3df61-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="3df61-137">Pokud existují existující projekty, které se zaměřují na starší architektury, můžete chtít ponechat tyto projekty nedotčené a použít projekt .NET Core k cílení budoucích architektur.</span><span class="sxs-lookup"><span data-stu-id="3df61-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Projekt .NET Core s existujícím projektem v jiné složce](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="3df61-139">**Zdrojový kód**</span><span class="sxs-lookup"><span data-stu-id="3df61-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="3df61-140">Jádro .NET a existující projekty jsou uloženy v samostatných složkách.</span><span class="sxs-lookup"><span data-stu-id="3df61-140">The .NET Core and existing projects are kept in separate folders.</span></span> <span data-ttu-id="3df61-141">Udržování projektů v samostatných složkách zabraňuje vynucení mít Visual Studio 2017 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="3df61-141">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="3df61-142">Můžete vytvořit samostatné řešení, které otevře pouze staré projekty.</span><span class="sxs-lookup"><span data-stu-id="3df61-142">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="3df61-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="3df61-143">See also</span></span>

- [<span data-ttu-id="3df61-144">Dokumentace k přenosu jádra .NET</span><span class="sxs-lookup"><span data-stu-id="3df61-144">.NET Core porting documentation</span></span>](index.md)
