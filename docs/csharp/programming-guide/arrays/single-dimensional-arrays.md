---
title: Jednorozměrná pole (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 2f5dcb032c5dea764cdd212bbcd02e1640089d96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313950"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Jednorozměrná pole (Průvodce programováním v C#)
Je možné deklarovat jednorozměrná pole pět celých čísel, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 Toto pole obsahuje elementy ze `array[0]` k `array[4]`. [Nové](../../../csharp/language-reference/keywords/new.md) operátor slouží k vytvoření pole a inicializace elementy pole na výchozí hodnoty. V tomto příkladu jsou inicializovány všechny elementy pole na hodnotu nula.  
  
 Pole, které ukládá prvků řetězce lze deklarovat stejným způsobem. Příklad:  
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Inicializace pole  
 Je možné k chybě při inicializaci pole po deklaraci, v takovém případě není nutné specifikátor rozsahu, protože je již poskytl počet elementů v seznamu inicializace. Příklad:  
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 Pole řetězců jde inicializovat stejným způsobem. Toto je deklaraci pole řetězců kde každý element pole se inicializuje pomocí názvu za den:  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 Při inicializaci pole po deklaraci, můžete použít následující klávesové zkratky:  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 Je možné deklarovat bez inicializace proměnné pole, ale je nutné použít `new` operátor při přiřazení pole na tuto proměnnou. Příklad:  
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 C# 3.0 zavádí implicitně typovaná pole. Další informace najdete v tématu [implicitně typované pole](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Typ hodnoty a odkaz na typ pole  
 Vezměte v úvahu následující deklarace pole:  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 Výsledek tohoto prohlášení, závisí na tom, zda `SomeType` je hodnota typu nebo typu odkazu. Pokud je typ hodnoty, příkaz vytvoří pole 10 elementů, z nichž každá má typ `SomeType`. Pokud `SomeType` je typu odkazu. příkaz vytvoří pole 10 elementů, z nichž každý je inicializováno odkaz s hodnotou null.  
  
 Další informace o typy hodnot a typy odkazu najdete v tématu [typy](../../../csharp/language-reference/keywords/types.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
