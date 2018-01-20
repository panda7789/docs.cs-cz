---
title: "Pole (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d395bcb179650fe29ab0918e7f91f3c8b6197b5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="arrays-c-programming-guide"></a>Pole (Průvodce programováním v C#)
V strukturu dat pole můžete uložit více proměnných stejného typu. Pole je deklarovat s typem jejích elementů.  
  
 `type[] arrayName;`  
  
 Následující příklady vytvořit jednorozměrná, multidimenzionální a vícenásobná pole:  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a>Pole – přehled  
 Pole má následující vlastnosti:  
  
-   Pole může být [jednorozměrná](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [multidimenzionálního](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) nebo [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).  
  
-   Počet dimenzí a délka Každá dimenze se vytvářejí, když je vytvořena instance pole. Tyto hodnoty nelze změnit po dobu životnosti instance.  
  
-   Výchozí hodnoty prvků číselná pole je nastaven na hodnotu nula a referenční dokumentace elementů jsou nastaveny na hodnotu null.  
  
-   Vícenásobná pole je pole polí, a proto jeho prvky jsou odkazové typy a jsou inicializována tak, aby `null`.  
  
-   Pole jsou nula indexované: pole s `n` elementy je indexovaný z `0` k `n-1`.  
  
-   Elementy pole může být jakéhokoli typu, včetně typu pole.  
  
-   Typy polí jsou [odkazové typy](../../../csharp/language-reference/keywords/reference-types.md) odvozené od abstraktní základní typ <xref:System.Array>. Vzhledem k tomu, že tento typ implementuje <xref:System.Collections.IEnumerable> a <xref:System.Collections.Generic.IEnumerable%601>, můžete použít [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iterace v rámci všech polí v jazyce C#.  
  
## <a name="related-sections"></a>Související oddíly  
  
-   [Pole jako objekty](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [Použití příkazu foreach s poli](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [Předávání polí jako argumentů](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [Předávání polí pomocí parametrů ref a out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Kolekce](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [Pole – Typ kolekce](http://msdn.microsoft.com/library/8a9964de-8941-47b1-a3cf-a01bc88db9e8)
