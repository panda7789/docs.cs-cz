---
title: Předávání polí pomocí parametrů ref a out (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
ms.openlocfilehash: a186399125e01bb2535f3a8b488c6fbd85932246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a>Předávání polí pomocí parametrů ref a out (Průvodce programováním v C#)
Všechny jako [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry, `out` parametr typu pole musí mít přiřazenou před jeho použitím; to znamená, musí být přiřazen volaného. Příklad:  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 Všechny jako [ref](../../../csharp/language-reference/keywords/ref.md) parametrů, `ref` parametr pole typu musí být výborný přiřadila volající. Z tohoto důvodu není nutné je jednoznačně přiřazovat volaným. A `ref` parametr pole typu mohou být změněny v důsledku volání. Například můžete přiřadit pole [null](../../../csharp/language-reference/keywords/null.md) hodnotu nebo může být inicializována na jiné pole. Příklad:  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 Následující dva příklady ukazují rozdíl mezi `out` a `ref` při použití v předávání do metod pole.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu pole `theArray` deklarovaného v volající ( `Main` metoda) a inicializované v `FillArray` metoda. Prvky pole jsou poté vráceny volajícímu a zobrazeny.  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu pole `theArray` je inicializován v volající ( `Main` metoda) a předaný `FillArray` metoda pomocí `ref` parametr. Některé elementy pole jsou aktualizovány v `FillArray` metoda. Prvky pole jsou poté vráceny volajícímu a zobrazeny.  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a>Viz také  
 [ref](../../../csharp/language-reference/keywords/ref.md)  
 [out – modifikátor parametrů](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
