---
title: Stromy výrazů
description: Další informace o stromech výrazů v .NET Core a jak je použít k reprezentaci kódu jako struktur, které můžete zkoumat, upravovat a spouštět.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: e1026ef70860da519b688a9d67181b88d03f6f0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145836"
---
# <a name="expression-trees"></a>Stromy výrazů

Pokud jste použili LINQ, máte zkušenosti s `Func` bohatou knihovnou, kde jsou typy součástí sady rozhraní API. (Pokud nejste obeznámeni s LINQ, pravděpodobně budete chtít přečíst [linq tutorial](linq/index.md) a článek o [lambda výrazy](./programming-guide/statements-expressions-operators/lambda-expressions.md) před tímto jeden.) *Výraz stromy* poskytují bohatší interakci s argumenty, které jsou funkce.

Při vytváření dotazů LINQ se při zapisují argumenty funkce, obvykle pomocí výrazů Lambda. V typickélinq dotazu jsou tyto argumenty funkce transformovány do delegáta, který vytvoří kompilátor.

Chcete-li mít bohatší interakci, je třeba použít *stromy výrazů*.
Stromy výrazů představují kód jako strukturu, kterou můžete prozkoumat, upravit nebo spustit. Tyto nástroje vám dávají možnost manipulovat s kódem za běhu. Můžete napsat kód, který zkoumá spuštěné algoritmy nebo vloží nové funkce. V pokročilejších scénářích můžete upravit běžící algoritmy a dokonce přeložit výrazy Jazyka C# do jiného formuláře pro spuštění v jiném prostředí.

Pravděpodobně jste již napsali kód, který používá stromy výrazů. Rozhraní LINQ rozhraní LINQ frameworku entity přijímají stromy výrazů jako argumenty pro vzorek výrazu dotazu LINQ.
To umožňuje [entity Framework](/ef/) přeložit dotaz, který jste napsali v C# do SQL, který se spustí v databázovém stroji. Dalším příkladem je [Moq](https://github.com/Moq/moq), což je populární mocking framework pro .NET.

Zbývající části tohoto kurzu se budou zabývat tím, co jsou stromy výrazů, prozkoumáme třídy architektury, které podporují stromy výrazů, a ukáží vám, jak pracovat se stromy výrazů. Dozvíte se, jak číst stromy výrazů, jak vytvářet stromy výrazů, jak vytvářet změněné stromy výrazů a jak spustit kód reprezentovaný stromy výrazů. Po přečtení budete připraveni použít tyto struktury k vytvoření bohatých adaptivních algoritmů.

1. [Vysvětlení stromů výrazů](expression-trees-explained.md)

    Seznamte se s strukturou a koncepty za *stromy výrazů*.

2. [Typy architektur podporující stromy výrazů](expression-classes.md)

    Seznamte se s strukturami a třídami, které definují stromy výrazů a manipulují s nimi.

3. [Provádění výrazů](expression-trees-execution.md)

    Zjistěte, jak převést strom výrazů reprezentovaný jako výraz Lambda na delegáta a provést výsledného delegáta.

4. [Interpretace výrazů](expression-trees-interpreting.md)

    Zjistěte, jak procházet a zkoumat *stromy výrazů,* abyste pochopili, jaký kód strom výrazu představuje.

5. [Vytváření výrazů](expression-trees-building.md)

    Naučte se, jak vytvořit uzly pro strom výrazů a vytvořit stromy výrazů.

6. [Překlad výrazů](expression-trees-translating.md)

    Zjistěte, jak vytvořit upravenou kopii stromu výrazů nebo přeložit strom výrazů do jiného formátu.

7. [Sečtením](expression-trees-summary.md)

    Zkontrolujte informace o stromech výrazů.
