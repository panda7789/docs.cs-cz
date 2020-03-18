---
title: Úvod do jazyka C# - seznamte se s vývojovými nástroji
description: Tento článek obsahuje základní úvod k nástrojům, které budete používat k vývoji aplikací jazyka C# a .NET v počítači.
ms.date: 10/23/2018
ms.openlocfilehash: 0b1df9e733eef92b1eeb0a7f3ba3ba49602f219d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156568"
---
# <a name="become-familiar-with-the-net-development-tools"></a><span data-ttu-id="2ee00-103">Seznamte se s nástroji pro vývoj rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="2ee00-103">Become familiar with the .NET development tools</span></span>

<span data-ttu-id="2ee00-104">Prvním krokem při spuštění kurzu na vašem počítači je nastavení vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="2ee00-104">The first step in running a tutorial on your machine is to set up a development environment.</span></span>
<span data-ttu-id="2ee00-105">Kurz .NET [Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="2ee00-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span>

<span data-ttu-id="2ee00-106">Případně můžete nainstalovat [.NET Core SDK](https://dotnet.microsoft.com/download) a [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="2ee00-106">Alternatively, you can install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="basic-application-development-flow"></a><span data-ttu-id="2ee00-107">Základní tok vývoje aplikací</span><span class="sxs-lookup"><span data-stu-id="2ee00-107">Basic application development flow</span></span>

<span data-ttu-id="2ee00-108">Budete vytvářet aplikace [`dotnet new`](../../../core/tools/dotnet-new.md) pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="2ee00-108">You'll create applications using the [`dotnet new`](../../../core/tools/dotnet-new.md) command.</span></span> <span data-ttu-id="2ee00-109">Tento příkaz generuje soubory a datové zdroje potřebné pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2ee00-109">This command generates the files and assets necessary for your application.</span></span> <span data-ttu-id="2ee00-110">Úvod do c# kurzy `console` všechny používat typ aplikace.</span><span class="sxs-lookup"><span data-stu-id="2ee00-110">The introduction to C# tutorials all use the `console` application type.</span></span> <span data-ttu-id="2ee00-111">Jakmile budete mít základy, můžete rozšířit na jiné typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="2ee00-111">Once you've got the basics, you can expand to other application types.</span></span>

<span data-ttu-id="2ee00-112">Ostatní příkazy, které budete [`dotnet build`](../../../core/tools/dotnet-build.md) používat, jsou k [`dotnet run`](../../../core/tools/dotnet-run.md) sestavení spustitelného souboru a ke spuštění spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="2ee00-112">The other commands you'll use are [`dotnet build`](../../../core/tools/dotnet-build.md) to build the executable, and [`dotnet run`](../../../core/tools/dotnet-run.md) to run the executable.</span></span>

## <a name="pick-your-tutorial"></a><span data-ttu-id="2ee00-113">Vyberte si svůj výukový program</span><span class="sxs-lookup"><span data-stu-id="2ee00-113">Pick your tutorial</span></span>

<span data-ttu-id="2ee00-114">Můžete začít s některou z následujících výukových programů:</span><span class="sxs-lookup"><span data-stu-id="2ee00-114">You can start with any of the following tutorials:</span></span>

## <a name="numbers-in-c"></a>[<span data-ttu-id="2ee00-115">Čísla v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2ee00-115">Numbers in C#</span></span>](numbers-in-csharp-local.md)

<span data-ttu-id="2ee00-116">V kurzu [Čísla v jazyce C#](numbers-in-csharp-local.md) se dozvíte, jak počítače ukládají čísla a jak provádět výpočty s různými číselnými typy.</span><span class="sxs-lookup"><span data-stu-id="2ee00-116">In the [Numbers in C#](numbers-in-csharp-local.md) tutorial, you'll learn how computers store numbers and how to perform calculations with different numeric types.</span></span> <span data-ttu-id="2ee00-117">Naučíte se základy zaokrouhlení a jak provádět matematické výpočty pomocí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="2ee00-117">You'll learn the basics of rounding and how to perform mathematical calculations using C#.</span></span>

<span data-ttu-id="2ee00-118">Tento kurz předpokládá, že jste dokončili lekci [hello world.](hello-world.yml)</span><span class="sxs-lookup"><span data-stu-id="2ee00-118">This tutorial assumes that you have finished the [Hello world](hello-world.yml) lesson.</span></span>

## <a name="branches-and-loops"></a>[<span data-ttu-id="2ee00-119">Větve a smyčky</span><span class="sxs-lookup"><span data-stu-id="2ee00-119">Branches and loops</span></span>](branches-and-loops-local.md)

<span data-ttu-id="2ee00-120">[Kurz Větve a smyčky](branches-and-loops-local.md) učí základy výběru různých cest provádění kódu na základě hodnot uložených v proměnných.</span><span class="sxs-lookup"><span data-stu-id="2ee00-120">The [Branches and loops](branches-and-loops-local.md) tutorial teaches the basics of selecting different paths of code execution based on the values stored in variables.</span></span> <span data-ttu-id="2ee00-121">Naučíte se základy toku řízení, což je základ toho, jak se programy rozhodují a vybírají různé akce.</span><span class="sxs-lookup"><span data-stu-id="2ee00-121">You'll learn the basics of control flow, which is the basis of how programs make decisions and choose different actions.</span></span>

<span data-ttu-id="2ee00-122">Tento kurz předpokládá, že jste dokončili [hello svět](hello-world.yml) a čísla [v c#](numbers-in-csharp-local.md) lekce.</span><span class="sxs-lookup"><span data-stu-id="2ee00-122">This tutorial assumes that you have finished the [Hello world](hello-world.yml) and [Numbers in C#](numbers-in-csharp-local.md) lessons.</span></span>

## <a name="list-collection"></a>[<span data-ttu-id="2ee00-123">Kolekce seznamu</span><span class="sxs-lookup"><span data-stu-id="2ee00-123">List collection</span></span>](arrays-and-collections.md)

<span data-ttu-id="2ee00-124">[List kolekce](arrays-and-collections.md) lekce poskytuje prohlídku list kolekce typu, který ukládá sekvence dat.</span><span class="sxs-lookup"><span data-stu-id="2ee00-124">The [List collection](arrays-and-collections.md) lesson gives you a tour of the List collection type that stores sequences of data.</span></span> <span data-ttu-id="2ee00-125">Dozvíte se, jak přidávat a odebírat položky, vyhledávat položky a seřadit seznamy.</span><span class="sxs-lookup"><span data-stu-id="2ee00-125">You'll learn how to add and remove items, search for items, and sort the lists.</span></span> <span data-ttu-id="2ee00-126">Budete zkoumat různé druhy seznamů.</span><span class="sxs-lookup"><span data-stu-id="2ee00-126">You'll explore different kinds of lists.</span></span>

<span data-ttu-id="2ee00-127">Tento kurz předpokládá, že jste dokončili výše uvedené lekce.</span><span class="sxs-lookup"><span data-stu-id="2ee00-127">This tutorial assumes that you have finished the lessons listed above.</span></span>

## <a name="introduction-to-classes"></a>[<span data-ttu-id="2ee00-128">Úvod do tříd</span><span class="sxs-lookup"><span data-stu-id="2ee00-128">Introduction to classes</span></span>](introduction-to-classes.md)

<span data-ttu-id="2ee00-129">Tento konečný úvod do kurzu Jazyka C# je k dispozici pouze ke spuštění v počítači pomocí vlastního prostředí místního vývoje a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ee00-129">This final introduction to C# tutorial is only available to run on your machine, using your own local development environment and .NET Core.</span></span>
<span data-ttu-id="2ee00-130">Vytvoříte konzolovou aplikaci a zobrazí tese základní objektově orientované funkce, které jsou součástí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="2ee00-130">You'll build a console application and see the basic object-oriented features that are part of the C# language.</span></span>
