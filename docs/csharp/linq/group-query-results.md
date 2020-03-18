---
title: Výsledky dotazu skupiny (LINQ v C#)
description: Přečtěte si, jak seskupit výsledky pomocí LINQ v C#.
ms.date: 12/01/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 577a358c31fcf5346e7aab7a2e2b6be10fd1beff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688459"
---
# <a name="group-query-results"></a>Seskupení výsledků dotazu

Seskupení je jednou z nejvýkonnějších funkcí LINQ. Následující příklady ukazují, jak seskupit data různými způsoby:

- Jedinou vlastností.

- Prvním písmenem vlastnosti string.

- Podle vypočítaného číselného rozsahu.

- Podle logického predikátu nebo jiného výrazu.

- Složeným klíčem.

Kromě toho poslední dva dotazy promítnou své výsledky do nového anonymního typu, který obsahuje pouze křestní jméno a příjmení studenta. Další informace naleznete v [klauzuli group .](../language-reference/keywords/group-clause.md)

## <a name="example"></a>Příklad

Všechny příklady v tomto tématu používají následující pomocné třídy a zdroje dat.

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak seskupit zdrojové prvky pomocí jedné vlastnosti prvku jako klíče skupiny. V tomto případě je `string`klíčem , příjmení studenta. Je také možné použít podřetězec pro klíč. Operace seskupení používá výchozí porovnávání rovnosti pro typ.

Do třídy vložte následující metodu. `StudentClass` Změňte příkaz volání `Main` v `sc.GroupBySingleProperty()`metodě na .

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak seskupit zdrojové prvky pomocí něčeho jiného než vlastnost objektu pro klíč skupiny. V tomto příkladu je klíčem první písmeno příjmení studenta.

Do třídy vložte následující metodu. `StudentClass` Změňte příkaz volání `Main` v `sc.GroupBySubstring()`metodě na .

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak seskupit zdrojové prvky pomocí číselné oblasti jako klíče skupiny. Dotaz pak promítne výsledky do anonymního typu, který obsahuje pouze křestní jméno a příjmení a rozsah percentilu, do kterého student patří. Anonymní typ se používá, protože není nutné `Student` použít celý objekt k zobrazení výsledků. `GetPercentile`je pomocná funkce, která vypočítá percentil na základě průměrného skóre studenta. Metoda vrátí celé číslo mezi 0 a 10.

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

Do třídy vložte následující metodu. `StudentClass` Změňte příkaz volání `Main` v `sc.GroupByRange()`metodě na .

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak seskupit zdrojové prvky pomocí logického porovnání výrazu. V tomto příkladu logický výraz testuje, zda je průměrné skóre zkoušky studenta větší než 75. Stejně jako v předchozích příkladech jsou výsledky promítány do anonymního typu, protože není potřeba celý zdrojový prvek. Všimněte si, že vlastnosti v `Key` anonymní typ stanou vlastnosti na člena a lze přistupovat podle názvu při spuštění dotazu.

Do třídy vložte následující metodu. `StudentClass` Změňte příkaz volání `Main` v `sc.GroupByBoolean()`metodě na .

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít anonymní typ zapouzdřit klíč, který obsahuje více hodnot. V tomto příkladu je první hodnota klíče první písmeno příjmení studenta. Druhá hodnota klíče je logická hodnota, která určuje, zda student skóroval nad 85 při první zkoušce. Skupiny můžete objednat podle libovolné vlastnosti v klíči.

Do třídy vložte následující metodu. `StudentClass` Změňte příkaz volání `Main` v `sc.GroupByCompositeKey()`metodě na .

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.IGrouping%602>
- [LINQ (Language Integrated Query)](index.md)
- [group – klauzule](../language-reference/keywords/group-clause.md)
- [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)
- [Provedení poddotazu na operaci seskupení](perform-a-subquery-on-a-grouping-operation.md)
- [Vytvoření vnořené skupiny](create-a-nested-group.md)
- [Seskupování dat](../programming-guide/concepts/linq/grouping-data.md)
