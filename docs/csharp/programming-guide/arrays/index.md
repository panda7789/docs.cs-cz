---
title: Pole – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715059"
---
# <a name="arrays-c-programming-guide"></a>Pole (Průvodce programováním v C#)

V datové struktuře pole můžete uložit více proměnných stejného typu. Deklarujete pole zadáním typu jeho prvků. Chcete-li, aby pole ukládalo prvky libovolného typu, můžete jako typ zadat `object`. V rámci sjednoceného typu systému C#jsou všechny typy, předdefinované a uživatelsky definované typy odkazů a typy hodnot děděny přímo nebo nepřímo z <xref:System.Object>.

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
- Vícenásobné pole je pole polí, a proto jeho prvky jsou odkazové typy a jsou inicializovány na `null`.
- Pole jsou indexována nulou: pole s `n` elementy je indexováno z `0` na `n-1`.
- Prvky pole mohou být libovolného typu, včetně typu pole.
- Typy polí jsou [odkazové typy](../../language-reference/keywords/reference-types.md) odvozené od abstraktního základního typu <xref:System.Array>. Vzhledem k tomu, že tento typ implementuje <xref:System.Collections.IEnumerable> a <xref:System.Collections.Generic.IEnumerable%601>[](../../language-reference/keywords/foreach-in.md) , můžete použít iteraci ForEach C#pro všechna pole v.

## <a name="related-sections"></a>Související oddíly

- [Pole jako objekty](arrays-as-objects.md)
- [Použití příkazu foreach s poli](using-foreach-with-arrays.md)
- [Předávání polí jako argumentů](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Kolekce](../concepts/collections.md)
