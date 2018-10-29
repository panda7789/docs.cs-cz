---
title: Co je nového v C# - C# Průvodce
description: Jak je C# vyvíjejí jazyka
ms.date: 11/13/2017
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: b079c21ee90a797b038b96ae68123a538464c382
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201436"
---
# <a name="whats-new-in-c"></a>Co je nového v jazyce C# #

Tato stránka poskytuje přehled nových funkcí v jednotlivých hlavní verze produktu C# jazyka. Informace o hlavní funkce přidané v jednotlivých verzích jsou podrobně popsané odkazovaných článcích. Informace o nových funkcích, které byly vydány, najdete v obecné verzi nebo ve verzi public preview. Podrobný stav funkce jazyka, včetně funkcí pro nadcházejících vydáních najdete [v úložišti dotnet/roslyn](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) na Githubu.

> [!IMPORTANT]
> C# Jazyk spoléhá na typy a metody v *standardní knihovny* pro některé funkce. Jedním z příkladů je zpracování výjimek. Každý `throw` příkaz nebo výraz je zaškrtnuto, aby objekt vyvolané je odvozen z <xref:System.Exception>. Podobně každý `catch` proběhne kontrola, že typ je zachycena je odvozen od <xref:System.Exception>. Každá verze může přidat nové požadavky. Chcete-li používat nejnovější funkce jazyků v starší prostředí, budete muset nainstalovat konkrétní knihovny. Tyto závislosti jsou popsané na stránce u každé konkrétní verze. Další informace o [vztahy mezi jazykem a knihovny](relationships-between-language-and-library.md) Další informace o této závislosti. 

Chcete-li používat nejnovější funkce ve verzi bod, je potřeba [konfigurace verze jazyka kompilátoru](../language-reference/configure-language-version.md) a vyberte verzi.

* [C#7.3](csharp-7-3.md):
  - Tato stránka popisuje nejnovější funkce v produktech C# jazyka. C#7.3 je aktuálně dostupné v [Visual Studio 2017 verze 15.7](https://visualstudio.microsoft.com/vs/whatsnew/)a [.NET Core 2.1 SDK 2.1.300 RC1](../../core/whats-new/index.md).
* [C#7.2](csharp-7-2.md):
  - Tato stránka popisuje funkce přidané ve C# jazyka. C#7.2 je aktuálně dostupné v [Visual Studio 2017 verze 15.5](https://visualstudio.microsoft.com/vs/whatsnew/)a [.NET Core 2.0 SDK](../../core/whats-new/index.md).
* [C#7.1](csharp-7-1.md):
  - Tato stránka popisuje funkce přidané ve C# 7.1. Tyto funkce byly přidány v [Visual Studio 2017 verze 15.3](https://visualstudio.microsoft.com/vs/whatsnew/)a [.NET Core 2.0 SDK](../../core/whats-new/index.md).
* [C#7.0](csharp-7.md):
  - Tato stránka popisuje funkce přidané ve C# 7.0. Tyto funkce byly přidány v [Visual Studio 2017](https://visualstudio.microsoft.com/vs/whatsnew/) a [.NET Core 1.0](../../core/whats-new/index.md) a novější
* [C#6](csharp-6.md):
  - Tato stránka popisuje funkce přidané ve C# 6. Tyto funkce jsou k dispozici v sadě Visual Studio 2015 pro vývojáře Windows a na .NET Core 1.0 pro vývojáře zkoumání C# v systémech macOS a Linux.
* [Podpora různých platforem](../../core/index.md):
  - C#, díky podpoře .NET Core běží na různých platformách. Pokud máte zájem o vyzkoušení C# v systému macOS nebo v některém z mnoha podporované distribuce Linuxu, další informace o .NET Core.
* [.NET compiler Platform SDK](../roslyn-sdk/index.md):
  - Sada SDK platformy kompilátoru .NET umožňuje napsat kód, který provádí statickou analýzu na C# kódu. Najít potenciální chyby, nebo špatné postupy, navrhnout opravy a dokonce i implementovat tyto opravy můžete pomocí těchto rozhraní API.

## <a name="previous-versions"></a>Předchozí verze

Následující seznam obsahuje klíčové funkce, které byly zavedeny v předchozích verzích C# jazyka a sady Visual Studio .NET.

* Visual Studio .NET 2013:
  - Tato verze sady Visual Studio zahrnuty, opravy chyb, vylepšení výkonu a náhledy technologie .NET Compiler Platform ("Roslyn"), kde byl program [sada SDK platformy kompilátoru .NET](../roslyn-sdk/index.md).
* C#5, visual Studio .NET 2012:
  - `Async` / `await`, a [informace o subjektu volajícím](../programming-guide/concepts/caller-information.md) atributy.
* C#4, visual Studio .NET 2010:
  - `Dynamic`, [pojmenované argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md), volitelné parametry a Obecné [odchylku kovariance a opravné položky k](../programming-guide/concepts/covariance-contravariance/index.md).
* C#3, visual Studio .NET 2008:
  - Inicializátory objektu a kolekce, výrazů lambda, rozšiřující metody, anonymní typy, automatické vlastnosti, místní `var` odvození, typu a [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).
* C#2, visual Studio .NET 2005:
  - Anonymní metody, obecné typy, typy připouštějící hodnotu Null, iterátory/yield `static` třídy a kovariance a opravné položky k odchylku pro delegáty.
* C#1.1, visual Studio .NET 2003:
  - `#line` direktivy pragma a xml komentáře.
* C#1. visual Studio .NET 2002:
  - První verzi [ C# ](../csharp.md).
