---
title: Seznámení se seznámení s nástroji pro C# vývoj
description: Tento článek poskytuje základní informace o nástrojích, které budete používat pro vývoj C# a aplikace .NET na vašem počítači.
ms.date: 10/23/2018
ms.openlocfilehash: b18c71c54e4450902f576a1074058abcd5e8aa91
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834078"
---
# <a name="become-familiar-with-the-net-development-tools"></a><span data-ttu-id="d0d13-103">Seznámení s nástroji pro vývoj v .NET</span><span class="sxs-lookup"><span data-stu-id="d0d13-103">Become familiar with the .NET development tools</span></span>

<span data-ttu-id="d0d13-104">Prvním krokem při spouštění kurzu na vašem počítači je nastavení vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="d0d13-104">The first step in running a tutorial on your machine is to set up a development environment.</span></span>
<span data-ttu-id="d0d13-105">Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS.</span><span class="sxs-lookup"><span data-stu-id="d0d13-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span>

<span data-ttu-id="d0d13-106">Alternativně můžete nainstalovat [.NET Core SDK](https://dotnet.microsoft.com/download) a [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="d0d13-106">Alternatively, you can install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="basic-application-development-flow"></a><span data-ttu-id="d0d13-107">Vývojový tok pro základní aplikace</span><span class="sxs-lookup"><span data-stu-id="d0d13-107">Basic application development flow</span></span>

<span data-ttu-id="d0d13-108">Aplikace vytvoříte pomocí příkazu [`dotnet new`](../../../core/tools/dotnet-new.md) .</span><span class="sxs-lookup"><span data-stu-id="d0d13-108">You'll create applications using the [`dotnet new`](../../../core/tools/dotnet-new.md) command.</span></span> <span data-ttu-id="d0d13-109">Tento příkaz vygeneruje soubory a prostředky nezbytné pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d0d13-109">This command generates the files and assets necessary for your application.</span></span> <span data-ttu-id="d0d13-110">Úvod do C# kurzů, které používají typ aplikace `console`.</span><span class="sxs-lookup"><span data-stu-id="d0d13-110">The introduction to C# tutorials all use the `console` application type.</span></span> <span data-ttu-id="d0d13-111">Jakmile budete mít základní informace, můžete je rozšířit na jiné typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="d0d13-111">Once you've got the basics, you can expand to other application types.</span></span>

<span data-ttu-id="d0d13-112">Ostatní příkazy, které použijete, jsou [`dotnet build`](../../../core/tools/dotnet-build.md) pro sestavení spustitelného souboru a [`dotnet run`](../../../core/tools/dotnet-run.md) pro spuštění spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="d0d13-112">The other commands you'll use are [`dotnet build`](../../../core/tools/dotnet-build.md) to build the executable, and [`dotnet run`](../../../core/tools/dotnet-run.md) to run the executable.</span></span>

## <a name="pick-your-tutorial"></a><span data-ttu-id="d0d13-113">Výběr kurzu</span><span class="sxs-lookup"><span data-stu-id="d0d13-113">Pick your tutorial</span></span>

<span data-ttu-id="d0d13-114">Můžete začít s některým z následujících kurzů:</span><span class="sxs-lookup"><span data-stu-id="d0d13-114">You can start with any of the following tutorials:</span></span>

## <a name="numbers-in-cnumbers-in-csharp-localmd"></a>[<span data-ttu-id="d0d13-115">Čísla v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d0d13-115">Numbers in C#</span></span>](numbers-in-csharp-local.md)

<span data-ttu-id="d0d13-116">V části [čísla v C# ](numbers-in-csharp-local.md) kurzu se dozvíte, jak počítače ukládají čísla a jak provádět výpočty s různými číselnými typy.</span><span class="sxs-lookup"><span data-stu-id="d0d13-116">In the [Numbers in C#](numbers-in-csharp-local.md) tutorial, you'll learn how computers store numbers and how to perform calculations with different numeric types.</span></span> <span data-ttu-id="d0d13-117">Naučíte se základy zaokrouhlování a postup, jak provádět matematické výpočty pomocí C#.</span><span class="sxs-lookup"><span data-stu-id="d0d13-117">You'll learn the basics of rounding and how to perform mathematical calculations using C#.</span></span>

<span data-ttu-id="d0d13-118">V tomto kurzu se předpokládá, že jste dokončili lekci [Hello World](hello-world.yml) .</span><span class="sxs-lookup"><span data-stu-id="d0d13-118">This tutorial assumes that you have finished the [Hello world](hello-world.yml) lesson.</span></span>

## <a name="branches-and-loopsbranches-and-loops-localmd"></a>[<span data-ttu-id="d0d13-119">Větve a smyčky</span><span class="sxs-lookup"><span data-stu-id="d0d13-119">Branches and loops</span></span>](branches-and-loops-local.md)

<span data-ttu-id="d0d13-120">Kurz [větvení a cyklů](branches-and-loops-local.md) učí základy výběru různých cest ke spuštění kódu na základě hodnot uložených v proměnných.</span><span class="sxs-lookup"><span data-stu-id="d0d13-120">The [Branches and loops](branches-and-loops-local.md) tutorial teaches the basics of selecting different paths of code execution based on the values stored in variables.</span></span> <span data-ttu-id="d0d13-121">Naučíte se základy řízení toku, což je základem způsobu, jakým programy provádí rozhodnutí a výběr různých akcí.</span><span class="sxs-lookup"><span data-stu-id="d0d13-121">You'll learn the basics of control flow, which is the basis of how programs make decisions and choose different actions.</span></span>

<span data-ttu-id="d0d13-122">V tomto kurzu se předpokládá, že jste [v C# ](numbers-in-csharp-local.md) lekci dokončili text [Hello World](hello-world.yml) a čísla.</span><span class="sxs-lookup"><span data-stu-id="d0d13-122">This tutorial assumes that you have finished the [Hello world](hello-world.yml) and [Numbers in C#](numbers-in-csharp-local.md) lessons.</span></span>

## <a name="list-collectionarrays-and-collectionsmd"></a>[<span data-ttu-id="d0d13-123">Kolekce seznamů</span><span class="sxs-lookup"><span data-stu-id="d0d13-123">List collection</span></span>](arrays-and-collections.md)

<span data-ttu-id="d0d13-124">V lekci [kolekce seznamu](arrays-and-collections.md) získáte prohlídku typu kolekce, ve kterém jsou uloženy sekvence dat.</span><span class="sxs-lookup"><span data-stu-id="d0d13-124">The [List collection](arrays-and-collections.md) lesson gives you a tour of the List collection type that stores sequences of data.</span></span> <span data-ttu-id="d0d13-125">Naučíte se, jak přidávat a odebírat položky, Hledat položky a třídit seznamy.</span><span class="sxs-lookup"><span data-stu-id="d0d13-125">You'll learn how to add and remove items, search for items, and sort the lists.</span></span> <span data-ttu-id="d0d13-126">Budete zkoumat různé druhy seznamů.</span><span class="sxs-lookup"><span data-stu-id="d0d13-126">You'll explore different kinds of lists.</span></span> 

<span data-ttu-id="d0d13-127">V tomto kurzu se předpokládá, že jste dokončili výše uvedené lekce.</span><span class="sxs-lookup"><span data-stu-id="d0d13-127">This tutorial assumes that you have finished the lessons listed above.</span></span>

## <a name="introduction-to-classesintroduction-to-classesmd"></a>[<span data-ttu-id="d0d13-128">Úvod do tříd</span><span class="sxs-lookup"><span data-stu-id="d0d13-128">Introduction to classes</span></span>](introduction-to-classes.md)

<span data-ttu-id="d0d13-129">Tento závěrečný Úvod C# do kurzu je k dispozici pouze ke spuštění na vašem počítači pomocí vlastního místního vývojového prostředí a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d0d13-129">This final introduction to C# tutorial is only available to run on your machine, using your own local development environment and .NET Core.</span></span>
<span data-ttu-id="d0d13-130">Vytvoříte konzolovou aplikaci a zobrazíte základní funkce orientované na objekty, které jsou součástí C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="d0d13-130">You'll build a console application and see the basic object-oriented features that are part of the C# language.</span></span>
