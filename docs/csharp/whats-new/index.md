---
title: Co je nového v jazyce C# – průvodce v C#
description: Jak se vyvíjí jazyka C#
keywords: C#, nejnovější funkce, co je nového, Roslyn
author: BillWagner
ms.author: wiwagn
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 719fbe826b0b115b19067dbaf0d04f14e6534890
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="whats-new-in-c"></a><span data-ttu-id="e0b16-104">Co je nového v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e0b16-104">What's new in C#</span></span> #

<span data-ttu-id="e0b16-105">Tato stránka obsahuje přehled nových funkcí v každé hlavní verzi jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e0b16-105">This page provides a roadmap of new features in each major release of the C# language.</span></span> <span data-ttu-id="e0b16-106">Následující odkazy obsahují podrobné informace na hlavní funkce přidané do jednotlivých verzí.</span><span class="sxs-lookup"><span data-stu-id="e0b16-106">The following links provide detailed information on the major features added in each release.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e0b16-107">Jazyk C# spoléhá na typy a metody v *standardní knihovna* pro některé funkce.</span><span class="sxs-lookup"><span data-stu-id="e0b16-107">The C# language relies on types and methods in a *standard library* for some of the features.</span></span> <span data-ttu-id="e0b16-108">Jedním z příkladů je zpracování výjimky.</span><span class="sxs-lookup"><span data-stu-id="e0b16-108">One example is exception processing.</span></span> <span data-ttu-id="e0b16-109">Každý `throw` příkaz nebo výraz je zaškrtnuto, aby objekt hlášeny je odvozený od <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="e0b16-109">Every `throw` statement or expression is checked to ensure the object being thrown is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="e0b16-110">Podobně každých `catch` je zaškrtnuta možnost zajistit, aby se zjistilo je odvozen od <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="e0b16-110">Similarly, every `catch` is checked to ensure that the type being caught is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="e0b16-111">Každá verze může přidat nové požadavky.</span><span class="sxs-lookup"><span data-stu-id="e0b16-111">Each version may add new requirements.</span></span> <span data-ttu-id="e0b16-112">Pokud chcete použít nejnovější funkce jazyka v starší prostředí, musíte nainstalovat specifické knihovny.</span><span class="sxs-lookup"><span data-stu-id="e0b16-112">To use the latest language features in older environments, you may need to install specific libraries.</span></span> <span data-ttu-id="e0b16-113">Tyto závislosti jsou popsané na stránce pro každou konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="e0b16-113">These dependencies are documented in the page for each specific version.</span></span> <span data-ttu-id="e0b16-114">Další informace o [vztahy mezi jazyk a knihovna](relationships-between-language-and-library.md) pozadí na tuto závislost.</span><span class="sxs-lookup"><span data-stu-id="e0b16-114">You can learn more about the [relationships between language and library](relationships-between-language-and-library.md) for background on this dependency.</span></span> 


* <span data-ttu-id="e0b16-115">[C# 7.2](csharp-7-2.md):</span><span class="sxs-lookup"><span data-stu-id="e0b16-115">[C# 7.2](csharp-7-2.md):</span></span>
    - <span data-ttu-id="e0b16-116">Tato stránka popisuje nejnovější funkce v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="e0b16-116">This page describes the latest features in the C# language.</span></span> <span data-ttu-id="e0b16-117">Je nyní k dispozici v C# 7.2 [Visual Studio 2017 verze 15,5](https://www.visualstudio.com/vs/whatsnew/)a v [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="e0b16-117">C# 7.2 is currently available in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="e0b16-118">[C# 7.1](csharp-7-1.md):</span><span class="sxs-lookup"><span data-stu-id="e0b16-118">[C# 7.1](csharp-7-1.md):</span></span>
    - <span data-ttu-id="e0b16-119">Tato stránka popisuje funkce v C# 7.1.</span><span class="sxs-lookup"><span data-stu-id="e0b16-119">This page describes the features in C# 7.1.</span></span> <span data-ttu-id="e0b16-120">Tyto funkce byly přidány v [Visual Studio 2017 verze 15.3](https://www.visualstudio.com/vs/whatsnew/)a v [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="e0b16-120">These features were added in [Visual Studio 2017 version 15.3](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="e0b16-121">[C# 7](csharp-7.md):</span><span class="sxs-lookup"><span data-stu-id="e0b16-121">[C# 7](csharp-7.md):</span></span>
    - <span data-ttu-id="e0b16-122">Tato stránka popisuje funkce přidané v C# 7.</span><span class="sxs-lookup"><span data-stu-id="e0b16-122">This page describes the features added in C# 7.</span></span> <span data-ttu-id="e0b16-123">Tyto funkce byly přidány v [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) a [.NET Core 1.0](../../core/whats-new/index.md) a novější</span><span class="sxs-lookup"><span data-stu-id="e0b16-123">These features were added in [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) and [.NET Core 1.0](../../core/whats-new/index.md) and later</span></span>
     
* <span data-ttu-id="e0b16-124">[C# 6](csharp-6.md):</span><span class="sxs-lookup"><span data-stu-id="e0b16-124">[C# 6](csharp-6.md):</span></span>
    - <span data-ttu-id="e0b16-125">Tato stránka popisuje funkce přidané v C# 6.</span><span class="sxs-lookup"><span data-stu-id="e0b16-125">This page describes the features that were added in C# 6.</span></span> <span data-ttu-id="e0b16-126">Tyto funkce jsou k dispozici v sadě Visual Studio 2015 pro vývojáře v systému Windows a na .NET Core 1.0 pro vývojáře zkoumat C# v systému macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="e0b16-126">These features are available in Visual Studio 2015 for Windows developers, and on .NET Core 1.0 for developers exploring C# on macOS and Linux.</span></span>

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* <span data-ttu-id="e0b16-127">[Podpora různých platforem](../../core/index.md):</span><span class="sxs-lookup"><span data-stu-id="e0b16-127">[Cross Platform Support](../../core/index.md):</span></span>
    - <span data-ttu-id="e0b16-128">C#, prostřednictvím podpory .NET Core, běží ve více platformách.</span><span class="sxs-lookup"><span data-stu-id="e0b16-128">C#, through .NET Core support, runs on multiple platforms.</span></span> <span data-ttu-id="e0b16-129">Pokud vás zajímá pokusí C# v systému macOS nebo na jednu z dalších podporované distribuce systému Linux, přečtěte si další informace o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0b16-129">If you are interested in trying C# on macOS, or on one of the many supported Linux distributions, learn more about .NET Core.</span></span>

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a><span data-ttu-id="e0b16-130">Předchozí verze</span><span class="sxs-lookup"><span data-stu-id="e0b16-130">Previous Versions</span></span>
<span data-ttu-id="e0b16-131">Následující seznamy klíčové funkce, které byly zavedeny v předchozích verzích jazyka C# a Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="e0b16-131">The following lists key features that were introduced in previous versions of the C# language and Visual Studio .NET.</span></span>  
  
 * <span data-ttu-id="e0b16-132">Visual Studio .NET 2013:</span><span class="sxs-lookup"><span data-stu-id="e0b16-132">Visual Studio .NET 2013:</span></span> 
     - <span data-ttu-id="e0b16-133">Tato verze sady Visual Studio obsahovala opravy chyb, vylepšení výkonu a verze Preview technologie .NET kompilátoru platformy ("Roslyn"), který se stal .NET SDK platformy kompilátoru<!--Link to ../roslyn/index.md-->.</span><span class="sxs-lookup"><span data-stu-id="e0b16-133">This version of Visual Studio included bug fixes, performance improvements, and technology previews of .NET Compiler Platform ("Roslyn") which became the .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span></span>

 * <span data-ttu-id="e0b16-134">C# 5, Visual Studio .NET 2012:</span><span class="sxs-lookup"><span data-stu-id="e0b16-134">C# 5, Visual Studio .NET 2012:</span></span> 
     - <span data-ttu-id="e0b16-135">`Async` / `await`, a [informace o subjektu volajícím](../programming-guide/concepts/caller-information.md) atributy.</span><span class="sxs-lookup"><span data-stu-id="e0b16-135">`Async` / `await`, and [caller information](../programming-guide/concepts/caller-information.md) attributes.</span></span>

 * <span data-ttu-id="e0b16-136">C# 4, Visual Studio .NET 2010:</span><span class="sxs-lookup"><span data-stu-id="e0b16-136">C# 4, Visual Studio .NET 2010:</span></span> 
     - <span data-ttu-id="e0b16-137">`Dynamic`, [s názvem argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md), volitelnými parametry a obecného [kovarianci a opravné položky k odchylku](../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="e0b16-137">`Dynamic`, [named arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md), optional parameters, and generic [covariance and contra variance](../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

 * <span data-ttu-id="e0b16-138">C# 3, Visual Studio .NET 2008:</span><span class="sxs-lookup"><span data-stu-id="e0b16-138">C# 3, Visual Studio .NET 2008:</span></span> 
     - <span data-ttu-id="e0b16-139">Inicializátory objektu a kolekce, výrazů lambda, rozšiřující metody, anonymní typy, automatické vlastnosti, místní `var` odvození, typu a [jazyk integrovaného dotazu (LINQ)](../programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="e0b16-139">Object and collection initializers, lambda expressions, extension methods, anonymous types, automatic properties, local `var` type inference, and [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span></span>

 * <span data-ttu-id="e0b16-140">C# 2, Visual Studio .NET 2005:</span><span class="sxs-lookup"><span data-stu-id="e0b16-140">C# 2, Visual Studio .NET 2005:</span></span> 
     - <span data-ttu-id="e0b16-141">Anonymní metody, obecné typy, typy s možnou hodnotou Null, iterátory/yield `static` třídy a kovariance a opravné položky k odchylky pro delegáti.</span><span class="sxs-lookup"><span data-stu-id="e0b16-141">Anonymous methods, generics, nullable types, iterators/yield, `static` classes, and covariance and contra variance for delegates.</span></span>

 * <span data-ttu-id="e0b16-142">C# 1.1, Visual Studio .NET 2003:</span><span class="sxs-lookup"><span data-stu-id="e0b16-142">C# 1.1, Visual Studio .NET 2003:</span></span> 
     - <span data-ttu-id="e0b16-143">`#line`komentáře doc – Direktiva pragma a xml.</span><span class="sxs-lookup"><span data-stu-id="e0b16-143">`#line` pragma and xml doc comments.</span></span>

 * <span data-ttu-id="e0b16-144">C# 1, Visual Studio .NET 2002:</span><span class="sxs-lookup"><span data-stu-id="e0b16-144">C# 1, Visual Studio .NET 2002:</span></span> 
     - <span data-ttu-id="e0b16-145">První verze součásti [C#](../csharp.md).</span><span class="sxs-lookup"><span data-stu-id="e0b16-145">The first release of [C#](../csharp.md).</span></span>   
