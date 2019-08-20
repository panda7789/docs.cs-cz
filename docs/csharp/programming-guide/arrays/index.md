---
title: Pole – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 24c6d54c3fe92ada661e732adec582e87ab62417
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597528"
---
# <a name="arrays-c-programming-guide"></a>Pole (Průvodce programováním v C#)

V datové struktuře pole můžete uložit více proměnných stejného typu. Deklarujete pole zadáním typu jeho prvků.  
  
 `type[] arrayName;`  
  
 Následující příklad vytvoří jednorozměrná, multidimenzionální a vícenásobná pole:  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a>Přehled pole

 Pole má následující vlastnosti:  
  
- Pole může být jednorozměrné [](./single-dimensional-arrays.md), [multidimenzionální](./multidimensional-arrays.md) nebo vícenásobné. [](./jagged-arrays.md)  
  
- Počet rozměrů a délka každé dimenze jsou vytvořeny při vytvoření instance pole. Tyto hodnoty nejde během životnosti instance změnit.  
  
- Výchozí hodnoty prvků číselného pole jsou nastaveny na nulu a referenční prvky jsou nastaveny na hodnotu null.  
  
- Vícenásobné pole je pole pole, a proto jeho prvky jsou odkazové typy a jsou inicializovány na `null`.  
  
- Pole jsou indexována nulou: pole s `n` elementy je indexováno `0` z `n-1`do.  
  
- Prvky pole mohou být libovolného typu, včetně typu pole.  
  
- Typy polí jsou [odkazové typy](../../language-reference/keywords/reference-types.md) odvozené od abstraktního základního <xref:System.Array>typu. Vzhledem k tomu, <xref:System.Collections.IEnumerable> že <xref:System.Collections.Generic.IEnumerable%601>tento typ implementuje a [](../../language-reference/keywords/foreach-in.md) , můžete použít iteraci ForEach C#pro všechna pole v.  
  
## <a name="related-sections"></a>Související oddíly  
  
- [Pole jako objekty](./arrays-as-objects.md)  
  
- [Použití příkazu foreach s poli](./using-foreach-with-arrays.md)  
  
- [Předávání polí jako argumentů](./passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Kolekce](../concepts/collections.md)
