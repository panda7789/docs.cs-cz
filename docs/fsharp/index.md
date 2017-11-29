---
title: "Průvodce F #"
description: "Další informace o F # programovací jazyk, open-source jazyk pro platformu .NET, která poskytuje prvotřídní podporu pro funkční programování."
keywords: "Rozhraní .NET, .NET core"
author: jackfoxy
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 4ddd77cef6cf70a63f1af81359d82eda27a01593
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="f-guide"></a><span data-ttu-id="e8822-104">Průvodce F #</span><span class="sxs-lookup"><span data-stu-id="e8822-104">F# Guide</span></span>

<span data-ttu-id="e8822-105">F # je open source napříč platformami programovací jazyk pro platformu .NET, která poskytuje prvotřídní podporu pro funkční programování, společně s podporou objektově orientované a imperativní programování.</span><span class="sxs-lookup"><span data-stu-id="e8822-105">F# is a cross-platform, open source programming language for .NET which provides first-class support for functional programming, along with support of object-oriented and imperative programming.</span></span>  <span data-ttu-id="e8822-106">Kompilátor Visual F # a nástrojů jsou implementaci společnosti Microsoft a nástrojů pro F # programovací jazyk, díky F # členem první třídy rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="e8822-106">The Visual F# compiler and tooling are Microsoft's implementation and tooling for the F# programming language, making F# a first-class member of .NET.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="e8822-107">Pokud jste ještě F #</span><span class="sxs-lookup"><span data-stu-id="e8822-107">If You're New to F#</span></span> #

<span data-ttu-id="e8822-108">Pokud jste ještě F #, začínat [prohlídka z F #](tour.md) vám získat přehled o jazyce.</span><span class="sxs-lookup"><span data-stu-id="e8822-108">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language.</span></span>

<span data-ttu-id="e8822-109">Doporučujeme projít si [funguje jako hodnoty první třídy](introduction-to-functional-programming/functions-as-first-class-values.md) <!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)--> další funkční programování konceptů, které jsou nezbytné pro práci s F #.</span><span class="sxs-lookup"><span data-stu-id="e8822-109">It's also recommended that you go through the [Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)--> to learn Functional Programming concepts which are essential to working with F#.</span></span>

<span data-ttu-id="e8822-110">[Kurzy](tutorials/getting-started/index.md) také mít podrobné návody pro různé úrovně dovedností a funkce jazyka.</span><span class="sxs-lookup"><span data-stu-id="e8822-110">The [Tutorials](tutorials/getting-started/index.md) also have step-by-step guides for various skill levels and features of the language.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="e8822-111">Pokud máte zkušenosti s F #</span><span class="sxs-lookup"><span data-stu-id="e8822-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="e8822-112">Pokud znáte hodně F #, najdete mnoho použití v [referenční příručka jazyka](language-reference/index.md), který dokumentů. každý aspekt jazyka důkladně, doplňují mnoha ukázek kódu.</span><span class="sxs-lookup"><span data-stu-id="e8822-112">If you know your way around F#, you'll find a lot of use in the [Language Reference](language-reference/index.md), which documents each aspect of the language thoroughly, supplemented by numerous code samples.</span></span>  <span data-ttu-id="e8822-113">Naleznete zde také spoustu použití v [F # referenční dokumentace hlavní knihovny](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference).</span><span class="sxs-lookup"><span data-stu-id="e8822-113">You'll also find a lot of use in the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference).</span></span>  <span data-ttu-id="e8822-114">Reference knihovny základní F # nakonec přesune mimo MSDN a do těchto aktuální dokumenty.</span><span class="sxs-lookup"><span data-stu-id="e8822-114">The F# Core Library Reference will eventually move away from MSDN and into these current docs.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="e8822-115">Foundation softwaru F #</span><span class="sxs-lookup"><span data-stu-id="e8822-115">The F# Software Foundation</span></span>

<span data-ttu-id="e8822-116">I když společnost Microsoft se na vývojáře primární jazyk F # a Visual F # Tooling, F # je také zálohován nezávislé foundation, F # softwaru Foundation (FSSF).</span><span class="sxs-lookup"><span data-stu-id="e8822-116">Although Microsoft is the primary developer of the F# language and Visual F# Tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="e8822-117">Zvláště Foundation softwaru F # je povýšit, ochranu a zálohy programovací jazyk, F # a pro podporu a usnadnění růst různých a mezinárodní komunita programátory v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="e8822-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="e8822-118">Další informace a zahrňte, podívejte se na [fsharp.org](http://fsharp.org).</span><span class="sxs-lookup"><span data-stu-id="e8822-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="e8822-119">Dokumentace</span><span class="sxs-lookup"><span data-stu-id="e8822-119">Documentation</span></span>

* [<span data-ttu-id="e8822-120">Kurzy</span><span class="sxs-lookup"><span data-stu-id="e8822-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="e8822-121">[Funkce jako hodnoty první třídy](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="e8822-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="e8822-122">Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="e8822-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="e8822-123">Referenční dokumentace F # hlavní knihovny</span><span class="sxs-lookup"><span data-stu-id="e8822-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="e8822-124">Online čtení prostředků</span><span class="sxs-lookup"><span data-stu-id="e8822-124">Online Reading Resources</span></span>

* [<span data-ttu-id="e8822-125">F # pro Fun a zisku Gitbook</span><span class="sxs-lookup"><span data-stu-id="e8822-125">F# for Fun and Profit Gitbook</span></span>](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) 
* [<span data-ttu-id="e8822-126">Programování Wikibook F #</span><span class="sxs-lookup"><span data-stu-id="e8822-126">F# Programming Wikibook</span></span>](https://en.wikibooks.org/wiki/F_Sharp_Programming)

## <a name="video-learning-resources"></a><span data-ttu-id="e8822-127">Grafické materiály</span><span class="sxs-lookup"><span data-stu-id="e8822-127">Video Learning Resources</span></span>

* [<span data-ttu-id="e8822-128">Úvod do programování s řady F # na YouTube</span><span class="sxs-lookup"><span data-stu-id="e8822-128">Introduction to Programming with F# series on YouTube</span></span>](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)
* [<span data-ttu-id="e8822-129">Úvod do řady F # na FSharpTV</span><span class="sxs-lookup"><span data-stu-id="e8822-129">Introduction to F# series on FSharpTV</span></span>](https://fsharp.tv/courses/fsharp-programming-intro/)

## <a name="further-resources"></a><span data-ttu-id="e8822-130">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="e8822-130">Further Resources</span></span>

* [<span data-ttu-id="e8822-131">Studijní materiály na fsharp.org F #</span><span class="sxs-lookup"><span data-stu-id="e8822-131">F# Learning Resources on fsharp.org</span></span>](http://fsharp.org/learn.html)
* [<span data-ttu-id="e8822-132">Fragmenty kódu webu F #</span><span class="sxs-lookup"><span data-stu-id="e8822-132">F# Snippets Website</span></span>](http://www.fssnip.net)
* [<span data-ttu-id="e8822-133">F # softwaru Foundation</span><span class="sxs-lookup"><span data-stu-id="e8822-133">F# Software Foundation</span></span>](http://fsharp.org)
