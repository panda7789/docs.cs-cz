---
title: Stromy výrazů
description: Další informace o stromů výrazů v .NET Core a jakým způsobem je použít k reprezentování kód jako struktury, které můžete prozkoumat, upravit a spustit.
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: db35dd99dadc4e49aaaebd5d3782409a206cafc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214910"
---
# <a name="expression-trees"></a>Stromy výrazů

Pokud jste použili LINQ, máte zkušenosti s bohatou knihovny kde `Func` typy jsou součástí sada rozhraní API. (Pokud nejste obeznámeni s dotazy LINQ, budete ho zřejmě chtít číst [kurzu LINQ](linq/index.md) a kurz týkající se [výrazy lambda](lambda-expressions.md) před tímto.) *Stromy výrazů* poskytovat lepší integrace s argumenty, které jsou funkce.

Psaní argumenty funkce, obvykle pomocí výrazů Lambda, při vytváření dotazů LINQ. V typické dotazu LINQ se tyto argumenty funkce převede na delegáta, který vytvoří kompilátoru. 

Pokud chcete mít lepší integrace, budete muset použít *stromů výrazů*.
Stromy výrazů představují kód jako strukturu, která můžete prozkoumat, upravit nebo provést. Tyto nástroje vám power k manipulaci s kód za běhu. Můžete napsat kód, který hledá spuštěné algoritmy nebo vloží nové funkce. V pokročilejších scénářích můžete upravit, s algoritmy a i převede výrazy jazyka C# do jiného formátu pro spuštění v jiném prostředí.

Pravděpodobně jste již zapsány kód, který používá stromů výrazů. Rozhraní Entity Framework LINQ API přijmout stromů výrazů jako argumenty pro vzor výrazu dotazu LINQ.
Umožňující [Entity Framework](http://docs.efproject.net/en/latest/) přeložit dotaz jste napsali v jazyce C# do SQL, který se spustí v databázovém stroji. Dalším příkladem je [Moq](https://github.com/Moq/moq), což je Oblíbené mocking rozhraní pro rozhraní .NET.

Zbývající části tohoto kurzu bude prozkoumejte, jaké jsou stromů výrazů, zkontrolujte framework třídy, které podporují stromů výrazů a ukazují, jak pracovat s stromů výrazů. Dozvíte se, jak číst stromů výrazů, vytváření stromů výrazů, jak vytvořit stromů výrazů upravené a jak ke spouštění kódu vytvořeného reprezentována stromů výrazů. Po přečtení, bude připravená k použití těchto struktur vytvořit bohaté adaptivní algoritmy.

1. [Vysvětlení stromů výrazů](expression-trees-explained.md)

    Pochopit strukturu a koncepty za *stromů výrazů*.
    
2. [Typy architektur podporující stromy výrazů](expression-classes.md)
    
    Další informace o struktury a třídy, které definují a manipulaci s stromů výrazů.
    
3. [Provádění výrazů](expression-trees-execution.md)

    Zjistěte, jak převést strom výrazu, který je reprezentován jako výraz Lambda do delegáta a provést Výsledný delegát.

4. [Interpretace výrazů](expression-trees-interpreting.md)

    Zjistěte, jak procházet a prozkoumat *stromů výrazů* zjistit, co kód strom výrazu představuje.

5. [Vytváření výrazů](expression-trees-building.md)

    Zjistěte, jak sestavit uzlů pro strom výrazu a sestavení stromů výrazů.

6. [Překlad výrazů](expression-trees-translating.md)

    Naučte se vytvořit kopii strom výrazu upravené nebo přeložit strom výrazu do jiného formátu.

7. [Shrnutí](expression-trees-summary.md)

    Projděte si informace na stromů výrazů.
    
