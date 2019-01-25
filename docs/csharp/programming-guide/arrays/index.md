---
title: Pole - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 1b1a3d2e61507a497349deeb857e4333356f66a5
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857798"
---
# <a name="arrays-c-programming-guide"></a>Pole (Průvodce programováním v C#)

Ve struktuře dat pole lze uložit více proměnných stejného typu. Deklarujete pole zadáním typu jeho elementů.  
  
 `type[] arrayName;`  
  
 Následující příklad vytváří jedno/dvoudimenzionální a vícenásobná pole:  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a>Pole – přehled

 Pole má následující vlastnosti:  
  
-   Pole může být [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [multidimenzionální](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) nebo [vícenásobné](../../../csharp/programming-guide/arrays/jagged-arrays.md).  
  
-   Počet rozměrů a délka každé dimenze jsou vytvořeny při vytvoření instance pole. Tyto hodnoty nelze změnit během životnosti instance.  
  
-   Výchozí hodnoty prvků číselného pole jsou nastaveny na nulu a prvky odkazu jsou nastaveny na hodnotu null.  
  
-   Vícenásobné pole je pole polí, a proto jeho prvky jsou odkazové typy a jsou inicializovány na hodnotu `null`.  
  
-   Pole jsou indexována nula: pole s `n` prvky je indexováno od `0` k `n-1`.  
  
-   Prvky pole mohou být libovolného typu, včetně typu pole.  
  
-   Typy pole jsou [referenční typy](../../../csharp/language-reference/keywords/reference-types.md) odvozené z abstraktního základního typu <xref:System.Array>. Protože tento typ implementuje <xref:System.Collections.IEnumerable> a <xref:System.Collections.Generic.IEnumerable%601>, můžete použít [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iterace pro všechna pole v jazyce C#.  
  
## <a name="related-sections"></a>Související oddíly  
  
-   [Pole jako objekty](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [Použití příkazu foreach s poli](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [Předávání polí jako argumentů](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Kolekce](../../../csharp/programming-guide/concepts/collections.md)
