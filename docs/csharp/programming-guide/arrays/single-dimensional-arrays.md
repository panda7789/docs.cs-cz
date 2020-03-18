---
title: Jednorozměrná pole – programovací průvodce C#
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: bd4ab53a9cb53e5cf636601bff5ac64a10a310a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170348"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Jednorozměrná pole (Průvodce programováním v C#)

Můžete deklarovat jednorozměrné pole pěti celočísel, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 Toto pole obsahuje `array[0]` `array[4]`prvky z do . [Nový](../../language-reference/operators/new-operator.md) operátor se používá k vytvoření pole a inicializaci prvků pole na jejich výchozí hodnoty. V tomto příkladu jsou všechny prvky pole inicializovány na nulu.  
  
 Pole, které ukládá řetězcové prvky, může být deklarováno stejným způsobem. Například:  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>Inicializace pole

 Je možné inicializovat pole při deklaraci, v takovém případě není specifikátor délky nutný, protože je již zadán počtem prvků v inicializačním seznamu. Například:  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 Pole řetězce lze inicializovat stejným způsobem. Následuje deklarace pole řetězců, kde je každý prvek pole inicializován názvem dne:  

 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 Při inicializaci pole při deklaraci můžete použít následující zkratky:  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 Je možné deklarovat proměnnou pole bez inicializace, ale je nutné použít `new` operátor při přiřazení pole k této proměnné. Například:  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 C# 3.0 zavádí implicitně zadaných polí. Další informace naleznete [v tématu Implicitně zadali pole](./implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Pole typu a referenčního typu

 Zvažte následující deklaraci pole:  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 Výsledek tohoto příkazu závisí `SomeType` na tom, zda je typ hodnoty nebo typ odkazu. Pokud se jedná o typ hodnoty, příkaz vytvoří pole 10 prvků, z nichž každý má typ `SomeType`. Pokud `SomeType` je typ odkazu, příkaz vytvoří pole 10 prvků, z nichž každý je inicializován na odkaz null.  
  
Další informace o typech hodnot a typech odkazů naleznete v [tématu Typy hodnot](../../language-reference/builtin-types/value-types.md) a [Reference .](../../language-reference/keywords/reference-types.md)
  
## <a name="see-also"></a>Viz také

- <xref:System.Array>
- [Programovací příručka jazyka C#](../index.md)
- [Pole](./index.md)
- [Vícerozměrná pole](./multidimensional-arrays.md)
- [Vícenásobná pole](./jagged-arrays.md)
