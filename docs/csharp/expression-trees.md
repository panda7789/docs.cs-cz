---
title: Stromy výrazů
description: Přečtěte si o stromech výrazů v .NET Core a jejich použití k reprezentaci kódu jako struktur, které můžete prozkoumávat, upravovat a spouštět.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: 62f5b93097ee8ad2177fc0bb484c656408f91f30
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062506"
---
# <a name="expression-trees"></a>Stromy výrazů

Pokud jste použili LINQ, máte zkušenosti s bohatou knihovnou, kde `Func` jsou typy součástí sady rozhraní API. (Pokud nejste obeznámeni s LINQ, pravděpodobně budete chtít přečíst [kurz LINQ](linq/index.md) a článek o [výrazech lambda](language-reference/operators/lambda-expressions.md) před tímto.) *Stromy výrazů* poskytují bohatou interakci s argumenty, které jsou funkcemi.

Při vytváření dotazů LINQ píšete argumenty funkce, obvykle pomocí výrazů lambda. V typických dotazech LINQ jsou tyto argumenty funkce transformovány na delegáta, který kompilátor vytvoří.

Pokud chcete mít rozsáhlejší interakci, je nutné použít *stromy výrazů*.
Stromy výrazů reprezentují kód jako strukturu, kterou můžete prostudovat, upravit nebo spustit. Tyto nástroje umožňují pracovat s kódem během běhu. Můžete napsat kód, který prověřuje spuštěné algoritmy nebo vloží nové funkce. V pokročilejších scénářích můžete upravit běžící algoritmy a dokonce přeložit výrazy jazyka C# do jiného formuláře pro provádění v jiném prostředí.

Pravděpodobně jste již napsali kód, který používá stromy výrazů. Rozhraní API LINQ Entity Framework akceptují stromy výrazů jako argumenty pro vzor výrazu dotazu LINQ.
To umožňuje [Entity Framework](/ef/) přeložit dotaz, který jste napsali v jazyce C#, do jazyka SQL, který se spouští v databázovém stroji. Dalším příkladem je [MOQ](https://github.com/Moq/moq), což je oblíbená rozhraní pro návrhy rozhraní .NET.

Zbývající části tohoto kurzu budou zkoumat, jaké stromy výrazů jsou, prozkoumat třídy architektury, které podporují stromy výrazů, a Ukázat, jak pracovat se stromy výrazů. Naučíte se, jak číst stromy výrazů, jak vytvářet stromy výrazů, jak vytvářet stromy upravených výrazů a jak spustit kód reprezentovaný stromy výrazů. Po přečtení budete připraveni tyto struktury použít k vytváření bohatých adaptivních algoritmů.

1. [Vysvětlení stromů výrazů](expression-trees-explained.md)

    Pochopení struktury a konceptů za *stromy výrazů*.

2. [Typy architektur podporující stromy výrazů](expression-classes.md)

    Přečtěte si o strukturách a třídách, které definují a manipulují s stromy výrazů.

3. [Provádění výrazů](expression-trees-execution.md)

    Přečtěte si, jak převést strom výrazu reprezentovaný jako výraz lambda do delegáta a provést výsledný delegát.

4. [Interpretace výrazů](expression-trees-interpreting.md)

    Naučte se procházet a prozkoumávat *stromy výrazů* , abyste pochopili, jaký kód strom výrazu představuje.

5. [Vytváření výrazů](expression-trees-building.md)

    Naučte se vytvářet uzly pro strom výrazů a stromy výrazů sestavení.

6. [Překlad výrazů](expression-trees-translating.md)

    Naučte se, jak vytvořit upravenou kopii stromu výrazů nebo jak přeložit strom výrazu do jiného formátu.

7. [Sčítání](expression-trees-summary.md)

    Projděte si informace o stromech výrazů.
