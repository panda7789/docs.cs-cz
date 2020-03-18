---
title: Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715059"
---
# <a name="arrays-c-programming-guide"></a>Pole (Průvodce programováním v C#)

Do datové struktury pole můžete uložit více proměnných stejného typu. Deklarujete pole zadáním typu jeho prvků. Pokud chcete, aby pole uklánělo prvky libovolného typu, můžete zadat `object` jako jeho typ. V systému sjednoceného typu jazyka C# všechny typy, předdefinované a uživatelem definované, <xref:System.Object>typy odkazů a typy hodnot, dědí přímo nebo nepřímo z .

```csharp
type[] arrayName;
```

## <a name="example"></a>Příklad

Následující příklad vytvoří jednorozměrná, vícerozměrná a zubatá pole:

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>Přehled pole

Pole má následující vlastnosti:

- Pole může být [jednorozměrné](single-dimensional-arrays.md), [vícerozměrné](multidimensional-arrays.md) nebo [zubaté](jagged-arrays.md).
- Počet dimenzí a délka každé dimenze jsou stanoveny při vytvoření instance pole. Tyto hodnoty nelze změnit během životnosti instance.
- Výchozí hodnoty číselných prvků pole jsou nastaveny na nulu a referenční prvky jsou nastaveny na hodnotu null.
- Zubaté pole je pole polí, a proto jeho prvky jsou `null`typy odkazů a jsou inicializovány na .
- Pole jsou indexována bez `n` indexu: pole `0` s `n-1`prvky je indexováno z do .
- Prvky pole mohou být libovolného typu, včetně typu pole.
- Typy polí jsou [typy odkazů](../../language-reference/keywords/reference-types.md) odvozené <xref:System.Array>z abstraktního základního typu . Vzhledem k <xref:System.Collections.IEnumerable> tomu, že tento typ implementuje a <xref:System.Collections.Generic.IEnumerable%601>, můžete použít [foreach](../../language-reference/keywords/foreach-in.md) iteraci na všech polích v C#.

## <a name="related-sections"></a>Související oddíly

- [Pole jako objekty](arrays-as-objects.md)
- [Použití příkazu foreach s poli](using-foreach-with-arrays.md)
- [Předávání polí jako argumentů](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Kolekce](../concepts/collections.md)
