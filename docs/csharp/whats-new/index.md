---
title: Co je nového v jazyce C# – průvodce v C#
description: Jak se vyvíjí jazyka C#
ms.date: 11/13/2017
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 399550178a12ff520dff033f0f1dc4a7cdfb9591
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314669"
---
# <a name="whats-new-in-c"></a>Co je nového v jazyce C# #

Tato stránka obsahuje přehled nových funkcí v každé hlavní verzi jazyka C#. Následující odkazy obsahují podrobné informace na hlavní funkce přidané do jednotlivých verzí.

> [!IMPORTANT]
> Jazyk C# spoléhá na typy a metody v *standardní knihovna* pro některé funkce. Jedním z příkladů je zpracování výjimky. Každý `throw` příkaz nebo výraz je zaškrtnuto, aby objekt hlášeny je odvozený od <xref:System.Exception>. Podobně každých `catch` je zaškrtnuta možnost zajistit, aby se zjistilo je odvozen od <xref:System.Exception>. Každá verze může přidat nové požadavky. Pokud chcete použít nejnovější funkce jazyka v starší prostředí, musíte nainstalovat specifické knihovny. Tyto závislosti jsou popsané na stránce pro každou konkrétní verzi. Další informace o [vztahy mezi jazyk a knihovna](relationships-between-language-and-library.md) pozadí na tuto závislost. 

Chcete-li použít nejnovější funkce ve verzi bod, je potřeba [konfigurace jazyková verze kompilátoru](../language-reference/configure-language-version.md) a vyberte verzi.

* [C# 7.3](csharp-7-3.md):
  - Tato stránka popisuje nejnovější funkce v jazyce C#. Je nyní k dispozici v C# 7.3 [Visual Studio 2017 verze 15.7](https://visualstudio.microsoft.com/vs/whatsnew/)a v [.NET Core 2.1 SDK 2.1.300 RC1](../../core/whats-new/index.md).
* [C# 7.2](csharp-7-2.md):
  - Tato stránka popisuje funkce přidané do jazyka C#. Je nyní k dispozici v C# 7.2 [Visual Studio 2017 verze 15,5](https://visualstudio.microsoft.com/vs/whatsnew/)a v [.NET Core 2.0 SDK](../../core/whats-new/index.md).
* [C# 7.1](csharp-7-1.md):
  - Tato stránka popisuje funkce přidané v C# 7.1. Tyto funkce byly přidány v [Visual Studio 2017 verze 15.3](https://visualstudio.microsoft.com/vs/whatsnew/)a v [.NET Core 2.0 SDK](../../core/whats-new/index.md).
* [C# 7.0](csharp-7.md):
  - Tato stránka popisuje funkce přidané v C# 7.0. Tyto funkce byly přidány v [Visual Studio 2017](https://visualstudio.microsoft.com/vs/whatsnew/) a [.NET Core 1.0](../../core/whats-new/index.md) a novější
* [C# 6](csharp-6.md):
  - Tato stránka popisuje funkce přidané v C# 6. Tyto funkce jsou k dispozici v sadě Visual Studio 2015 pro vývojáře v systému Windows a na .NET Core 1.0 pro vývojáře zkoumat C# v systému macOS a Linux.
* [Podpora různých platforem](../../core/index.md):
  - C#, prostřednictvím podpory .NET Core, běží ve více platformách. Pokud vás zajímá pokusí C# v systému macOS nebo na jednu z dalších podporované distribuce systému Linux, přečtěte si další informace o .NET Core.
* [Kompilátoru platformy .NET SDK](../roslyn-sdk/index.md):
  - .NET SDK platformy kompilátoru umožňuje psát kód, který provádí statické analýzy kódu C#. Tato rozhraní API můžete najít potenciální chyby, nebo špatnými, navrhnout opravy a i implementaci těchto opravy.

## <a name="previous-versions"></a>Předchozí verze

Následující seznamy klíčové funkce, které byly zavedeny v předchozích verzích jazyka C# a Visual Studio .NET.

* Visual Studio .NET 2013:
  - Tato verze sady Visual Studio obsahovala opravy chyb, vylepšení výkonu a verze Preview technologie .NET kompilátoru platformy ("Roslyn"), která se aktivovala [SDK pro platformu .NET kompilátoru](../roslyn-sdk/index.md).
* C# 5, Visual Studio .NET 2012:
  - `Async` / `await`, a [informace o subjektu volajícím](../programming-guide/concepts/caller-information.md) atributy.
* C# 4, Visual Studio .NET 2010:
  - `Dynamic`, [s názvem argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md), volitelnými parametry a obecného [kovarianci a opravné položky k odchylku](../programming-guide/concepts/covariance-contravariance/index.md).
* C# 3, Visual Studio .NET 2008:
  - Inicializátory objektu a kolekce, výrazů lambda, rozšiřující metody, anonymní typy, automatické vlastnosti, místní `var` odvození, typu a [jazyk integrovaného dotazu (LINQ)](../programming-guide/concepts/linq/index.md).
* C# 2, Visual Studio .NET 2005:
  - Anonymní metody, obecné typy, typy s možnou hodnotou Null, iterátory/yield `static` třídy a kovariance a opravné položky k odchylky pro delegáti.
* C# 1.1, Visual Studio .NET 2003:
  - `#line` komentáře doc – Direktiva pragma a xml.
* C# 1, Visual Studio .NET 2002:
  - První verze součásti [C#](../csharp.md).
