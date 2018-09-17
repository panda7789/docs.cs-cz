---
title: Jednorozměrná pole (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: c2f26fd74a596ada21eef578e58c9cd8e0305d6c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746176"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Jednorozměrná pole (Průvodce programováním v C#)

Je možné deklarovat jednorozměrné pole pět celých čísel, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 Toto pole obsahuje prvky z `array[0]` k `array[4]`. [Nové](../../../csharp/language-reference/keywords/new.md) operátor se používá k vytvoření pole a inicializaci prvků pole na výchozí hodnoty. V tomto příkladu jsou všechny prvky pole inicializovány na nulu.  
  
 Pole, která ukládá prvků řetězce mohou být deklarovány stejným způsobem. Příklad:  
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Inicializace pole

 Je možné k inicializaci pole při deklaraci, v takovém případě není potřeba specifikátor pozice, protože je už zadaný počet prvků v inicializačního seznamu. Příklad:  
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 Pole řetězců mohou být inicializovány stejným způsobem. Následuje deklaraci pole řetězců kde každý prvek pole je inicializována pomocí názvu dne:  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 Když inicializujete pole při deklaraci, můžete použít následující klávesové zkratky:  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 Je možné deklarovat proměnné pole bez inicializace, ale je nutné použít `new` operátor při přiřazení k této proměnné pole. Příklad:  
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 C# 3.0 zavádí implicitně typovaná pole. Další informace najdete v tématu [implicitně typované pole](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Typ hodnoty a odkaz na typ pole

 Vezměte v úvahu následující deklarace pole:  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 Výsledkem tohoto příkazu závisí na tom, zda `SomeType` je hodnotový typ nebo typ odkazu. Pokud je typ hodnoty, příkaz vytvoří pole 10 prvků, z nichž každá má typ `SomeType`. Pokud `SomeType` je typem odkazu, příkaz vytvoří pole 10 prvků, z nichž každý je inicializován na hodnotu Null.  
  
 Další informace o typy hodnot a typy odkazů, najdete v části [typy](../../../csharp/language-reference/keywords/types.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Array>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Pole](../../../csharp/programming-guide/arrays/index.md)  
- [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
