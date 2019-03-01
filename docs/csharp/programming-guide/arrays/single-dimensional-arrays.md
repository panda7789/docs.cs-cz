---
title: Jednorozměrná pole - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: d2ee0c2a38ffeef3d2d0b339b98e48c25227d96c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973259"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Jednorozměrná pole (Průvodce programováním v C#)

Je možné deklarovat jednorozměrné pole pět celých čísel, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 Toto pole obsahuje prvky z `array[0]` k `array[4]`. [Nové](../../../csharp/language-reference/keywords/new.md) operátor se používá k vytvoření pole a inicializaci prvků pole na výchozí hodnoty. V tomto příkladu jsou všechny prvky pole inicializovány na nulu.  
  
 Pole, která ukládá prvků řetězce mohou být deklarovány stejným způsobem. Příklad:  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>Inicializace pole

 Je možné k inicializaci pole při deklaraci, v takovém případě není potřeba specifikátor délku, protože je už zadaný počet prvků v seznamu inicializace. Příklad:  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 Pole řetězců mohou být inicializovány stejným způsobem. Následuje deklaraci pole řetězců kde každý prvek pole je inicializována pomocí názvu dne:  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 Když inicializujete pole při deklaraci, můžete použít následující klávesové zkratky:  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 Je možné deklarovat proměnné pole bez inicializace, ale je nutné použít `new` operátor při přiřazení k této proměnné pole. Příklad:  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 C# 3.0 zavádí implicitně typovaná pole. Další informace najdete v tématu [implicitně typované pole](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Typ hodnoty a odkaz na typ pole

 Vezměte v úvahu následující deklarace pole:  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 Výsledkem tohoto příkazu závisí na tom, zda `SomeType` je hodnotový typ nebo typ odkazu. Pokud je typ hodnoty, příkaz vytvoří pole 10 prvků, z nichž každá má typ `SomeType`. Pokud `SomeType` je typem odkazu, příkaz vytvoří pole 10 prvků, z nichž každý je inicializován na hodnotu Null.  
  
 Další informace o typy hodnot a typy odkazů, najdete v části [typy](../../../csharp/language-reference/keywords/types.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Array>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Pole](../../../csharp/programming-guide/arrays/index.md)
- [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
