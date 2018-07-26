---
title: Provádění vlastních operací spojování (LINQ v JAZYKU C#)
description: Zjistěte, jak k provádění vlastních operací spojování LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: 09ed0a202627a07ac8958de6ac46d7dc6c2837d0
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403967"
---
# <a name="perform-custom-join-operations"></a>Provádění vlastních operací spojování

Tento příklad ukazuje, jak provádět operace spojení, které nejsou možné s `join` klauzuli. Ve výrazu dotazu `join` klauzule je omezená na a optimalizovaná pro equijoins, které jsou jednoznačně nejpopulárnější nejběžnější typ operace spojení. Při provádění porovnávání, bude pravděpodobně vždy získat nejlepší výkon pomocí `join` klauzuli.

Ale `join` klauzuli nelze použít v následujících případech:

- Když se spojení záleží na výraz nerovnosti (jiných porovnávání).

- Když se spojení záleží na více než jeden výraz rovnosti nebo nerovnosti.

- Pokud máte zavést proměnnou rozsahu dočasný pro pořadí (vnitřní) na pravé straně před provedením operace spojení.

 K provedení spojení, které nejsou equijoins, lze použít více `from` klauzule zavést každý zdroj dat nezávisle na sobě. Pak použijete v predikátu výraz `where` klauzule pro proměnnou rozsahu pro každý zdroj. Výraz také můžou mít podobu volání metody.

> [!NOTE]
> Nepleťte si tento druh operace vlastní připojení s použitím více `from` klauzule pro přístup k vnitřních kolekcí. Další informace najdete v tématu [klauzule join](../language-reference/keywords/join-clause.md).

## <a name="example"></a>Příklad

První metoda v následujícím příkladu ukazuje, jednoduché křížové spojení. Křížové spojení musí používat opatrně, protože může vést k velmi velké množství výsledků. Ale že může být užitečné v některých scénářích pro vytvoření zdrojových posloupností, u kterých jsou spuštěny další dotazy.

Druhá metoda vytvoří posloupnost všech produktů, jejichž ID kategorie je uveden v seznamu kategorií na levé straně. Všimněte si použití `let` klauzule a `Contains` metodu pro vytvoření dočasné pole. Také je možné vytvořit pole před dotaz a předchází první `from` klauzuli.

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a>Příklad

V následujícím příkladu musí dotaz spojení dvou sekvencí založené na přiřazování shodných klíčů, které v případě pořadí vnitřní (pravá strana), nelze získat před klauzuli spojení sama. Pokud toto připojení se prováděly s `join` klauzule, pak bude `Split` metoda musel být volána pro každý prvek. Použití více `from` umožňuje klauzule dotazu, aby režii volání opakované metody. Nicméně od `join` optimalizuje, v tomto konkrétním případě může být rychlejší než při použití více `from` klauzule. Výsledky se budou lišit v závislosti primárně na to, jak nákladné volání metody, které je.

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a>Viz také:

[LINQ (Language Integrated Query)](index.md)  
[join – klauzule](../language-reference/keywords/join-clause.md)  
[Řazení výsledků klauzule join](order-the-results-of-a-join-clause.md)  