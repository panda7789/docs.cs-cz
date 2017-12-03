---
title: "Průvodce F #"
description: "Další informace o F #, funkční programovací jazyk, který běží na rozhraní .NET."
keywords: "Rozhraní .NET, .NET core"
author: jackfoxy
ms.author: phcart
ms.date: 12/01/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 45f5d2ca794ccea7a35cf6c0bf9d58a3e6500453
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="f-guide"></a><span data-ttu-id="da264-104">Průvodce F #</span><span class="sxs-lookup"><span data-stu-id="da264-104">F# Guide</span></span>

<span data-ttu-id="da264-105">F # je funkční programovací jazyk, který běží na rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="da264-105">F# is a functional programming language which runs on .NET.</span></span>  <span data-ttu-id="da264-106">Kromě podpůrné funkční programovací konstrukce má také programovací možnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="da264-106">In addition to supporting functional programming constructs, it also has object programming capabilities.</span></span>  <span data-ttu-id="da264-107">Díky této hybridní funkční programování s možnostmi objektově orientované F # protokol jazyk k provedení jakékoli úlohy.</span><span class="sxs-lookup"><span data-stu-id="da264-107">This hybrid of functional programming with object-oriented capabilities makes F# a pragmatic language for accomplishing any task.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="da264-108">Pokud jste ještě F #</span><span class="sxs-lookup"><span data-stu-id="da264-108">If You're New to F#</span></span> #

<span data-ttu-id="da264-109">Pokud jste ještě F #, začínat [prohlídka z F #](tour.md) získat přehled o jazyce a některé jeho koncepty programování.</span><span class="sxs-lookup"><span data-stu-id="da264-109">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language and some of its programming concepts.</span></span>  <span data-ttu-id="da264-110">Pokud používáte Visual Studio, šablona projektu kurz obsahuje stejný obsah.</span><span class="sxs-lookup"><span data-stu-id="da264-110">If you're using Visual Studio, the Tutorial project template contains the same content.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="da264-111">Pokud máte zkušenosti s F #</span><span class="sxs-lookup"><span data-stu-id="da264-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="da264-112">Pokud znáte hodně F #, nebo chcete získat další informace o konkrétní jazykové konstrukce, přečtěte si téma [referenční příručka jazyka](language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="da264-112">If you know your way around F#, or want to learn more about a specific language construct, see the [Language Reference](language-reference/index.md).</span></span>  <span data-ttu-id="da264-113">Je důkladné průvodce všechny možnosti jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="da264-113">It's a thorough guide of all F# language capabilities.</span></span>

<span data-ttu-id="da264-114">Kromě toho [F # referenční dokumentace hlavní knihovny](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) je skvělým zdrojem pro získání informací o FSharp.Core, základní knihovna, která je součástí F #.</span><span class="sxs-lookup"><span data-stu-id="da264-114">Additionally, the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) is a great resource for learning about FSharp.Core, the core library which is a part of F#.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="da264-115">Foundation softwaru F #</span><span class="sxs-lookup"><span data-stu-id="da264-115">The F# Software Foundation</span></span>

<span data-ttu-id="da264-116">I když společnost Microsoft se primární vývojáře jazyka F # a jeho nástrojů, F # je také zálohován nezávislé foundation, F # softwaru Foundation (FSSF).</span><span class="sxs-lookup"><span data-stu-id="da264-116">Although Microsoft is the primary developer of the F# language and its tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="da264-117">Zvláště Foundation softwaru F # je povýšit, ochranu a zálohy programovací jazyk, F # a pro podporu a usnadnění růst různých a mezinárodní komunita programátory v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="da264-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="da264-118">Další informace a zahrňte, podívejte se na [fsharp.org](http://fsharp.org).</span><span class="sxs-lookup"><span data-stu-id="da264-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="da264-119">Dokumentace</span><span class="sxs-lookup"><span data-stu-id="da264-119">Documentation</span></span>

* [<span data-ttu-id="da264-120">Kurzy</span><span class="sxs-lookup"><span data-stu-id="da264-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="da264-121">[Funkce jako hodnoty první třídy](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="da264-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="da264-122">Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="da264-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="da264-123">Referenční dokumentace F # hlavní knihovny</span><span class="sxs-lookup"><span data-stu-id="da264-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="da264-124">Online čtení prostředků</span><span class="sxs-lookup"><span data-stu-id="da264-124">Online Reading Resources</span></span>

* [<span data-ttu-id="da264-125">F # pro Fun a zisku Gitbook</span><span class="sxs-lookup"><span data-stu-id="da264-125">F# for Fun and Profit Gitbook</span></span>](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) 
* [<span data-ttu-id="da264-126">Programování Wikibook F #</span><span class="sxs-lookup"><span data-stu-id="da264-126">F# Programming Wikibook</span></span>](https://en.wikibooks.org/wiki/F_Sharp_Programming)

## <a name="video-learning-resources"></a><span data-ttu-id="da264-127">Grafické materiály</span><span class="sxs-lookup"><span data-stu-id="da264-127">Video Learning Resources</span></span>

* [<span data-ttu-id="da264-128">Úvod do programování s řady F # na YouTube</span><span class="sxs-lookup"><span data-stu-id="da264-128">Introduction to Programming with F# series on YouTube</span></span>](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)
* [<span data-ttu-id="da264-129">Úvod do řady F # na FSharpTV</span><span class="sxs-lookup"><span data-stu-id="da264-129">Introduction to F# series on FSharpTV</span></span>](https://fsharp.tv/courses/fsharp-programming-intro/)

## <a name="further-resources"></a><span data-ttu-id="da264-130">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="da264-130">Further Resources</span></span>

* [<span data-ttu-id="da264-131">Studijní materiály na fsharp.org F #</span><span class="sxs-lookup"><span data-stu-id="da264-131">F# Learning Resources on fsharp.org</span></span>](http://fsharp.org/learn.html)
* [<span data-ttu-id="da264-132">Fragmenty kódu webu F #</span><span class="sxs-lookup"><span data-stu-id="da264-132">F# Snippets Website</span></span>](http://www.fssnip.net)
* [<span data-ttu-id="da264-133">F # softwaru Foundation</span><span class="sxs-lookup"><span data-stu-id="da264-133">F# Software Foundation</span></span>](http://fsharp.org)