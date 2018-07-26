---
title: Seskupení výsledků dotazu (LINQ v JAZYKU C#)
description: Zjistěte, jak seskupit výsledky pomocí jazyka LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 4da0aac6b406f588ea4f241c72d5700e8a63838c
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403862"
---
# <a name="group-query-results"></a>Seskupení výsledků dotazu

Seskupení je jedním z nejúčinnějších funkcí LINQ. Následující příklady ukazují, jak k seskupení dat různými způsoby:

- Podle jedné vlastnosti.

- Podle první písmeno vlastnosti typu string.

- Pomocí počítaného číselného rozsahu.

- Podle typu Boolean predikát nebo jiný výraz.

- Pomocí složeného klíče.

Kromě toho poslední dva dotazy projektu jejich výsledky do nové anonymní typ, který obsahuje pouze studenta je první a poslední název. Další informace najdete v tématu [group – klauzule](../language-reference/keywords/group-clause.md).

## <a name="example"></a>Příklad

Všechny příklady v tomto tématu použijte následující pomocné rutiny třídy a data zdrojů.

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak seskupit podle jedné vlastnosti elementu klíč skupiny zdrojové elementy. V tomto případě je klíč `string`, student získal příjmení. Je také možné použít dílčí řetězec klíče. Operaci seskupení pomocí výchozí procedury rovnosti pro typ.

Vložte následující metodu do `StudentClass` třídy. Změňte volání příkazu v `Main` metodu `sc.GroupBySingleProperty()`.

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak seskupit zdrojové prvky pomocí jinou hodnotu než vlastnost v objektu pro klíč skupiny. V tomto příkladu je klíč první písmeno student získal příjmení.

Vložte následující metodu do `StudentClass` třídy. Změňte volání příkazu v `Main` metodu `sc.GroupBySubstring()`.

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak seskupit zdroje prvky pomocí číselného rozsahu jako klíč skupiny. Výsledky dotazu pak projekty do anonymního typu, který obsahuje pouze první a poslední název a percentil rozsahu, do které patří studenta. Anonymní typ se používá, protože to není nutné použít úplnou `Student` zobrazíte výsledky. `GetPercentile` pomocná funkce, který vypočítá percentil podle skóre průměrné známky studenta. Metoda vrátí celé číslo mezi 0 a 10.

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

Vložte následující metodu do `StudentClass` třídy. Změňte volání příkazu v `Main` metodu `sc.GroupByRange()`.

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak pomocí výrazu porovnání logická seskupení zdrojové elementy. V tomto příkladu logický výraz testuje, jestli student získal zkoušku průměrné skóre je větší než 75. Stejně jako v předchozích příkladech výsledky se promítnou do anonymního typu vzhledem k tomu, že úplný zdrojový element není potřeba. Všimněte si, že vlastnosti v anonymním typu stanou vlastnosti na `Key` člena a je přístupný podle názvu, při spuštění dotazu.

Vložte následující metodu do `StudentClass` třídy. Změňte volání příkazu v `Main` metodu `sc.GroupByBoolean()`.

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít anonymní typ k zapouzdření klíč, který obsahuje více hodnot. V tomto příkladu první hodnota klíče je první písmeno student získal příjmení. Druhá hodnota klíče je logická hodnota, která určuje, jestli student zohlednit více než 85 na první zkoušku. Seřazení skupin podle libovolné vlastnosti v klíči.

Vložte následující metodu do `StudentClass` třídy. Změňte volání příkazu v `Main` metodu `sc.GroupByCompositeKey()`.

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a>Viz také:

<xref:System.Linq.Enumerable.GroupBy%2A>  
<xref:System.Linq.IGrouping%602>  
[LINQ (Language Integrated Query)](index.md)  
[group – klauzule](../language-reference/keywords/group-clause.md)  
[Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)  
[Provádění poddotazů na operace seskupení](perform-a-subquery-on-a-grouping-operation.md)  
[Vytvoření vnořené skupiny](create-a-nested-group.md)  
[Seskupování dat](../programming-guide/concepts/linq/grouping-data.md)  