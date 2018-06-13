---
title: Úvod do delegáti
description: Další informace o Delegáti v tomto tématu Přehled, který uvádí základní koncepty a popisuje cíle návrhu jazyk pro delegáti.
ms.date: 06/20/2016
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: d42d9d10aeaa153f12933fa3a59e58719f7741e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212184"
---
# <a name="introduction-to-delegates"></a>Úvod do delegáti

[Předchozí](delegates-events.md)

Zadejte delegáti *pozdní vazby* mechanismus v rozhraní .NET. Pozdní vazba znamená, že můžete vytvořit algoritmus kde volající také poskytuje alespoň jednu metodu, který implementuje část algoritmu.

Představte si třeba řazení seznamu hvězdiček v aplikaci astronomii.
Můžete řadit podle jejich vzdálenost od zemském povrchu, nebo odhad hvězdičkou nebo jejich dosahovaný také průraznost těchto hvězdiček.

V těchto případech metody Sort() provede v podstatě totéž: Uspořádá položky v seznamu na základě některé porovnání. Kód, který porovná dvě hvězdiček se liší pro jednotlivé pořadí řazení.

Tyto druhy řešení byly použity v softwaru pro poloviční století.
Koncept delegáta jazyka C# nabízí prvotřídní podporu a bezpečnost typů kolem koncept.

Jak uvidíte dál v této série, napsaný pro algoritmy, jako je to kód C# je typově bezpečný a využívá jazyk a kompilátoru zajistit, že typy odpovídat argumenty a návratové typy.

## <a name="language-design-goals-for-delegates"></a>Cíle návrhu jazyk pro delegáti

Návrháři jazyk uvedené několik cíle pro funkci, nakonec se aktivovala delegáti.

Tým chtěli běžné konstrukce jazyk, které by mohly být použity žádné pozdní vazba algoritmy. Která umožňuje vývojářům další jeden koncept a použít tento stejný koncept napříč mnoha různých softwaru problémy.

Druhý chtěli týmem pro podporu obou volání metody jednoho a vícesměrového vysílání. (Vícesměroví Delegáti jsou delegáti kde několik metod zřetězenými společně. Uvidíte příklady [dál v této série](delegate-class.md). 

Tým chtěli delegáty pro podporu stejné bezpečnost typů, které vývojáři očekávat od všech konstrukce jazyka C#. 

Nakonec týmem rozpoznat, že vzor událostí je jeden specifického vzoru kde delegáti nebo libovolný algoritmus pozdní vazba) je velmi užitečné. Tým chtěli Ujistěte se, že kód pro delegáti může být základem pro vzor událostí rozhraní .NET.

Výsledek všechno, co pracovní byla podpora delegáta a události v C# a rozhraní .NET. Zbývající články v této části se věnují funkce jazyka, podpora knihovny a běžné idioms, které se používají při práci s delegáti.

Získáte informace o `delegate` – klíčové slovo a co ho kódu generuje. Získáte informace o funkcích v `System.Delegate` třídy a jak se používají tyto funkce. Dozvíte se, jak vytvořit typ bezpečné Delegáti a postup vytvoření metody, které můžete vyvolat prostřednictvím delegáti. Budete také zjistěte, jak pracovat s Delegáti a události pomocí výrazů Lambda. Uvidíte, kde delegáti stane jeden ze stavebních bloků pro výrazy LINQ. Dozvíte se, jak delegáti slouží jako základ pro vzor událostí rozhraní .NET a jak se liší.

Celkově platí uvidíte, jak Delegáti jsou nedílnou součástí programování v rozhraní .NET a práci s rozhraní API.

Můžeme začít.

[Next](delegate-class.md)
