---
title: Pole – Průvodce programováním v C#
description: Uložení více proměnných stejného typu v datové struktuře pole v jazyce C#. Deklarujte pole zadáním typu nebo zadáním objektu pro uložení libovolného typu.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e302ff2e4c2488c4899c4eb99a666d2d322119ce
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474732"
---
# <a name="arrays-c-programming-guide"></a>Pole (Průvodce programováním v C#)

V datové struktuře pole můžete uložit více proměnných stejného typu. Deklarujete pole zadáním typu jeho prvků. Chcete-li, aby pole ukládalo prvky libovolného typu, můžete zadat `object` jako jeho typ. V rámci sjednoceného typu systému C# všechny typy, předdefinované a uživatelsky definované typy odkazů a typy hodnot dědí přímo nebo nepřímo z <xref:System.Object> .

```csharp
type[] arrayName;
```

## <a name="example"></a>Příklad

Následující příklad vytvoří jednorozměrná, multidimenzionální a vícenásobná pole:

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>Přehled pole

Pole má následující vlastnosti:

- Pole [může být jednorozměrné](single-dimensional-arrays.md), [multidimenzionální](multidimensional-arrays.md) nebo [vícenásobné](jagged-arrays.md).
- Počet rozměrů a délka každé dimenze jsou vytvořeny při vytvoření instance pole. Tyto hodnoty nejde během životnosti instance změnit.
- Výchozí hodnoty prvků číselného pole jsou nastaveny na nulu a referenční prvky jsou nastaveny na hodnotu null.
- Vícenásobné pole je pole pole, a proto jeho prvky jsou odkazové typy a jsou inicializovány na `null` .
- Pole jsou indexována nulou: pole s `n` elementy je indexováno z `0` do `n-1` .
- Prvky pole mohou být libovolného typu, včetně typu pole.
- Typy polí jsou [odkazové typy](../../language-reference/keywords/reference-types.md) odvozené od abstraktního základního typu <xref:System.Array> . Vzhledem k tomu, že tento typ implementuje <xref:System.Collections.IEnumerable> a <xref:System.Collections.Generic.IEnumerable%601> , můžete použít iteraci [foreach](../../language-reference/keywords/foreach-in.md) pro všechna pole v jazyce C#.

## <a name="related-sections"></a>Související oddíly

- [Pole jako objekty](arrays-as-objects.md)
- [Použití příkazu foreach s poli](using-foreach-with-arrays.md)
- [Předávání polí jako argumentů](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Kolekce](../concepts/collections.md)
