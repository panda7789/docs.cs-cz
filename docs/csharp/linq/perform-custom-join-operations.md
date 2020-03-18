---
title: Provedení operací vlastního spojení (LINQ v C#)
description: Zjistěte, jak provádět vlastní operace připojení LINQ v c#.
ms.date: 12/01/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: 7051007c67bd64cd11ede2f4d5352ce3d497255f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659849"
---
# <a name="perform-custom-join-operations"></a>Provádění vlastních operací spojování

Tento příklad ukazuje, jak provádět operace spojení, `join` které nejsou možné s klauzulí. Ve výrazu dotazu `join` je klauzule omezena na a optimalizovaná pro equijoins, které jsou zdaleka nejběžnějším typem operace spojení. Při provádění equijoin, budete pravděpodobně vždy získat nejlepší `join` výkon pomocí klauzule.

Doložka `join` však nemůže být použita v následujících případech:

- Když je spojení založeno na výrazu nerovnosti (neequijoin).

- Když je spojení založeno na více než jednom výrazu rovnosti nebo nerovnosti.

- Pokud máte zavést dočasnou proměnnou rozsahu pro pravé straně (vnitřní) sekvence před operací spojení.

 Chcete-li provést spojení, která nejsou equijoins, můžete použít více `from` klauzulí zavést každý zdroj dat nezávisle. Potom použít predikát výraz `where` v klauzuli na proměnnou rozsahu pro každý zdroj. Výraz může mít také podobu volání metody.

> [!NOTE]
> Nezaměňujte tento druh operace vlastního spojení `from` s použitím více klauzulí pro přístup k vnitřní kolekce. Další informace naleznete v tématu [join clause](../language-reference/keywords/join-clause.md).

## <a name="example"></a>Příklad

První metoda v následujícím příkladu ukazuje jednoduché křížové spojení. Křížová spojení musí být používána s opatrností, protože mohou vytvářet velmi velké sady výsledků. Však mohou být užitečné v některých scénářích pro vytváření zdrojových sekvencí, proti kterému jsou spuštěny další dotazy.

Druhá metoda vytváří posloupnost všech produktů, jejichž ID kategorie je uveden v seznamu kategorií na levé straně. Všimněte si `let` použití klauzule a `Contains` metody k vytvoření dočasného pole. Je také možné vytvořit pole před dotazem `from` a odstranit první klauzuli.

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a>Příklad

V následujícím příkladu dotaz musí spojit dvě sekvence založené na odpovídající klíče, které v případě vnitřní (pravé straně) sekvence, nelze získat před join klauzule sám. Pokud toto spojení `join` byly provedeny `Split` s klauzulí, pak metoda by musela být volána pro každý prvek. Použití více `from` klauzulí umožňuje dotazu, aby se zabránilo režii volání opakované metody. Nicméně vzhledem k tomu, `join` je optimalizován, v tomto `from` konkrétním případě může být stále rychlejší než použití více klauzulí. Výsledky se budou lišit především v závislosti na tom, jak nákladné je volání metody.

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a>Viz také

- [LINQ (Language Integrated Query)](index.md)
- [spojit klauzuli](../language-reference/keywords/join-clause.md)
- [Řazení výsledků klauzule join](order-the-results-of-a-join-clause.md)
