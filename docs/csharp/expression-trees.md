---
title: Stromy výrazů
description: Další informace o stromů výrazů v .NET Core a jak se dají použít k reprezentaci kód jako struktury, které můžete zkontrolovat, upravit a spustit.
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: db6e23d1ad0014a7dbb58a0cd473e67d6bd9acc0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096612"
---
# <a name="expression-trees"></a>Stromy výrazů

Pokud jste použili LINQ, budete mít prostředí, bohatá knihovna kde `Func` typy jsou součástí sady rozhraní API. (Pokud nejste obeznámeni s jazykem LINQ, pravděpodobně chtít číst [kurzu LINQ](linq/index.md) a v článku o [výrazy lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) před tímto.) *Stromy výrazů* poskytovat lepší interakci s argumenty, které jsou funkce.

Můžete napsat argumenty funkce, obvykle pomocí výrazů Lambda, při vytváření dotazů LINQ. V typické dotaz LINQ jsou tyto argumenty funkce transformuje na delegáta, který kompilátor vytvoří. 

Pokud chcete mít lepší interakci, budete muset použít *stromů výrazů*.
Stromy výrazů reprezentovala strukturu, která můžete zkontrolovat, upravit nebo spuštění kódu. Tyto nástroje vám poskytnou výkon během manipulace s kódem. Můžete napsat kód, který prověří spuštěnými algoritmy nebo vloží nové funkce. V pokročilejších scénářích, můžete upravit, spouštění algoritmů a dokonce i přeložit C# výrazy do jiného formátu pro spuštění v jiném prostředí.

Pravděpodobně jste už napsali kód, který používá stromy výrazů. Rozhraní Entity Framework LINQ API přijmout stromů výrazů jako argumenty pro vzor výrazu dotazu LINQ.
Která umožňuje [Entity Framework](/ef/) přeložit dotazu, který jste napsali v C# do SQL, který se spustí v databázovém stroji. Dalším příkladem je [Moq](https://github.com/Moq/moq), což je oblíbená architektura napodobování .NET.

Zbývající části tohoto kurzu bude prozkoumejte, jaké jsou stromů výrazů, prozkoumejte třídy rozhraní, které podporují stromů výrazů a ukazují, jak pracovat s stromy výrazů. Dozvíte se, jak číst stromů výrazů, k vytvoření stromů výrazu, k vytvoření stromů výrazu upravené a ke spouštění kódu vytvořeného reprezentována stromy výrazů. Po přečtení, bude připravené k použití těchto struktur vytvořit bohaté adaptivní algoritmy.

1. [Vysvětlení stromů výrazů](expression-trees-explained.md)

    Princip struktury a Principy *stromů výrazů*.
    
2. [Typy architektur podporující stromy výrazů](expression-classes.md)
    
    Další informace o struktur a tříd, které definují a manipulaci s stromy výrazů.
    
3. [Provádění výrazů](expression-trees-execution.md)

    Zjistěte, jak převést na strom výrazu, který je reprezentován jako výraz Lambda delegátovi a spusťte Výsledný delegát.

4. [Interpretace výrazů](expression-trees-interpreting.md)

    Další informace o procházení a prozkoumání *stromů výrazů* pochopit, co kód stromu výrazů představuje.

5. [Vytváření výrazů](expression-trees-building.md)

    Zjistěte, jak můžete vytvářet na uzly stromu výrazů a vytváření stromů výrazů.

6. [Překlad výrazů](expression-trees-translating.md)

    Zjistěte, jak sestavovat upravenou kopii strom výrazu, nebo strom výrazů se převedou do jiného formátu.

7. [Shrnutí](expression-trees-summary.md)

    Projděte si informace na stromy výrazů.
