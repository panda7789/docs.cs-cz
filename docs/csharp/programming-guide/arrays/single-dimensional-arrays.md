---
title: Jednorozměrná pole – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 07c6061bfc66b1640d0eacca217302feff1a390a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715032"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Jednorozměrná pole (Průvodce programováním v C#)

Můžete deklarovat jednorozměrné pole pěti celých čísel, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 Toto pole obsahuje prvky z `array[0]` k `array[4]`. Operátor [New](../../language-reference/operators/new-operator.md) slouží k vytvoření pole a inicializaci prvků pole na jejich výchozí hodnoty. V tomto příkladu jsou všechny prvky pole inicializovány na nulu.  
  
 Pole, které ukládá prvky řetězce, lze deklarovat stejným způsobem. Příklad:  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>Inicializace pole

 Je možné inicializovat pole po deklaraci, v takovém případě není specifikátor délky nutný, protože je již poskytnutý počtem prvků v seznamu inicializace. Příklad:  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 Pole řetězců lze inicializovat stejným způsobem. Následuje deklarace pole řetězců, kde je každý element pole inicializován pomocí názvu dne:  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 Když inicializujete pole při deklaraci, můžete použít následující klávesové zkratky:  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 Je možné deklarovat proměnnou pole bez inicializace, ale je nutné použít operátor `new`, když přiřadíte pole k této proměnné. Příklad:  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 C#3,0 zavádí implicitně typované pole. Další informace naleznete v tématu [implicitně typované pole](./implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Pole Typ hodnoty a odkazové typy

 Zvažte následující deklaraci pole:  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 Výsledek tohoto příkazu závisí na tom, zda `SomeType` typ hodnoty nebo typ odkazu. Pokud se jedná o typ hodnoty, příkaz vytvoří pole 10 prvků, z nichž každý má typ `SomeType`. Pokud je `SomeType` odkazový typ, příkaz vytvoří pole 10 prvků, z nichž každá je inicializována na odkaz s hodnotou null.  
  
Další informace o typech hodnot a odkazových typech naleznete v tématu [typy hodnot](../../language-reference/keywords/value-types.md) a [odkazové typy](../../language-reference/keywords/reference-types.md).
  
## <a name="see-also"></a>Viz také:

- <xref:System.Array>
- [Průvodce programováním v jazyce C#](../index.md)
- [Pole](./index.md)
- [Vícerozměrná pole](./multidimensional-arrays.md)
- [Vícenásobná pole](./jagged-arrays.md)
