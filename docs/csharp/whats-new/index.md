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
# <a name="whats-new-in-c"></a>Co je nového v jazyce C# #

Tato stránka obsahuje přehled nových funkcí v každé hlavní verzi jazyka C#. Následující odkazy obsahují podrobné informace na hlavní funkce přidané do jednotlivých verzí.

> [!IMPORTANT]
> Jazyk C# spoléhá na typy a metody v *standardní knihovna* pro některé funkce. Jedním z příkladů je zpracování výjimky. Každý `throw` příkaz nebo výraz je zaškrtnuto, aby objekt hlášeny je odvozený od <xref:System.Exception>. Podobně každých `catch` je zaškrtnuta možnost zajistit, aby se zjistilo je odvozen od <xref:System.Exception>. Každá verze může přidat nové požadavky. Pokud chcete použít nejnovější funkce jazyka v starší prostředí, musíte nainstalovat specifické knihovny. Tyto závislosti jsou popsané na stránce pro každou konkrétní verzi. Další informace o [vztahy mezi jazyk a knihovna](relationships-between-language-and-library.md) pozadí na tuto závislost. 


* [C# 7.2](csharp-7-2.md):
    - Tato stránka popisuje nejnovější funkce v jazyce C#. Je nyní k dispozici v C# 7.2 [Visual Studio 2017 verze 15,5](https://www.visualstudio.com/vs/whatsnew/)a v [.NET Core 2.0 SDK](../../core/whats-new/index.md).

* [C# 7.1](csharp-7-1.md):
    - Tato stránka popisuje funkce v C# 7.1. Tyto funkce byly přidány v [Visual Studio 2017 verze 15.3](https://www.visualstudio.com/vs/whatsnew/)a v [.NET Core 2.0 SDK](../../core/whats-new/index.md).

* [C# 7](csharp-7.md):
    - Tato stránka popisuje funkce přidané v C# 7. Tyto funkce byly přidány v [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) a [.NET Core 1.0](../../core/whats-new/index.md) a novější
     
* [C# 6](csharp-6.md):
    - Tato stránka popisuje funkce přidané v C# 6. Tyto funkce jsou k dispozici v sadě Visual Studio 2015 pro vývojáře v systému Windows a na .NET Core 1.0 pro vývojáře zkoumat C# v systému macOS a Linux.

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* [Podpora různých platforem](../../core/index.md):
    - C#, prostřednictvím podpory .NET Core, běží ve více platformách. Pokud vás zajímá pokusí C# v systému macOS nebo na jednu z dalších podporované distribuce systému Linux, přečtěte si další informace o .NET Core.

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a>Předchozí verze
Následující seznamy klíčové funkce, které byly zavedeny v předchozích verzích jazyka C# a Visual Studio .NET.  
  
 * Visual Studio .NET 2013: 
     - Tato verze sady Visual Studio obsahovala opravy chyb, vylepšení výkonu a verze Preview technologie .NET kompilátoru platformy ("Roslyn"), který se stal .NET SDK platformy kompilátoru<!--Link to ../roslyn/index.md-->.

 * C# 5, Visual Studio .NET 2012: 
     - `Async` / `await`, a [informace o subjektu volajícím](../programming-guide/concepts/caller-information.md) atributy.

 * C# 4, Visual Studio .NET 2010: 
     - `Dynamic`, [s názvem argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md), volitelnými parametry a obecného [kovarianci a opravné položky k odchylku](../programming-guide/concepts/covariance-contravariance/index.md).

 * C# 3, Visual Studio .NET 2008: 
     - Inicializátory objektu a kolekce, výrazů lambda, rozšiřující metody, anonymní typy, automatické vlastnosti, místní `var` odvození, typu a [jazyk integrovaného dotazu (LINQ)](../programming-guide/concepts/linq/index.md).

 * C# 2, Visual Studio .NET 2005: 
     - Anonymní metody, obecné typy, typy s možnou hodnotou Null, iterátory/yield `static` třídy a kovariance a opravné položky k odchylky pro delegáti.

 * C# 1.1, Visual Studio .NET 2003: 
     - `#line`komentáře doc – Direktiva pragma a xml.

 * C# 1, Visual Studio .NET 2002: 
     - První verze součásti [C#](../csharp.md).   
