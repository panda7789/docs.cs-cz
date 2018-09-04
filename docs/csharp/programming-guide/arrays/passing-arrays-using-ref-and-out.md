---
title: Předávání polí pomocí parametrů ref a out (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
ms.openlocfilehash: 8da3bf9f8eede72a7bc3cf8380eab66ca2b56e86
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526762"
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a>Předávání polí pomocí parametrů ref a out (Průvodce programováním v C#)

Stejně jako všechny [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry, `out` před se používá, musí být přiřazeno parametr typu pole; to znamená, musíte být přiřazeni volaným. Příklad:  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 Stejně jako všechny [ref](../../../csharp/language-reference/keywords/ref.md) parametry, `ref` parametr typu pole musí být přiřazen volajícím. Z tohoto důvodu není nutné je jednoznačně přiřazovat volaným. A `ref` parametr typu pole může být změněn v důsledku volání. Například je možné přiřadit pole [null](../../../csharp/language-reference/keywords/null.md) hodnotu, nebo může být inicializována jinému poli. Příklad:  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 Následující dva příklady znázorňují rozdíl mezi `out` a `ref` při použití předání polí metodám.  
  
## <a name="example"></a>Příklad

 V tomto příkladu je pole `theArray` je deklarováno pro volajícího ( `Main` metoda) a inicializováno v `FillArray` metody. Prvky pole jsou poté vráceny volajícímu a zobrazeny.  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]

## <a name="example"></a>Příklad

 V tomto příkladu je pole `theArray` je inicializováno pro volajícího ( `Main` metoda) a předat `FillArray` metoda pomocí `ref` parametr. Některé prvky pole jsou aktualizovány v `FillArray` metody. Prvky pole jsou poté vráceny volajícímu a zobrazeny.  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a>Viz také

- [ref](../../../csharp/language-reference/keywords/ref.md)  
- [out – modifikátor parametrů](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Pole](../../../csharp/programming-guide/arrays/index.md)  
- [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
