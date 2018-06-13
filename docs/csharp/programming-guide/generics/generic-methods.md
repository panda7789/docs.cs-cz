---
title: Obecné metody (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 04bc59d41eb7883e08138382b396bc737c7f11bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329865"
---
# <a name="generic-methods-c-programming-guide"></a>Obecné metody (Průvodce programováním v C#)
Obecná metoda je metoda, která je deklarovaný s parametry typu následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 Následující příklad kódu ukazuje jeden ze způsobů k volání metody pomocí `int` pro argument typu:  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 Argument typu můžete vypustit a kompilátor odvodí. Následující volání do `Swap` je ekvivalentem předchozího volání:  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 Stejná pravidla pro odvození typu týkají statických metod a instance metody. Kompilátor můžete infer – parametry typu podle argumenty metoda, kterou předáte v; nemůže infer – parametry typu jenom z omezení nebo vrátit hodnotu. Odvození typu proto nefunguje s metodami, které mají žádné parametry. Odvození typu nastane při kompilaci než kompilátor pokusí přeložit přetížené metody podpisy. Kompilátor logiku odvození typu platí pro všechny obecné metody, které sdílejí stejný název. V kroku rozlišení přetížení kompilátor obsahuje pouze obecné metody ve kterých byla úspěšná odvození typu.  
  
 V rámci obecné třídy neobecnou metody přístup parametry typu na úrovni třídy následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 Pokud definujete obecné metody, která přijímá stejnými parametry typu jako obsahující třídy, kompilátor vygeneruje upozornění CS0693, protože v rámci oboru metody argument zadaný pro vnitřní `T` skryje argument zadaný pro vnější `T`. Pokud budete potřebovat flexibilitu voláním metody – obecná třída s argumenty typu než ty, které jsou zadané, když byla vytvořena instance třídy, zvažte zadat jiný identifikátor pro typ parametru metody, jak je znázorněno v `GenericList2<T>` v následujícím Příklad.  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 Pomocí omezení pro povolení více specializované operací parametrů typů v metodách. Tato verze `Swap<T>`nyní s názvem `SwapIfGreater<T>`, lze použít pouze s argumenty typu, které implementují <xref:System.IComparable%601>.  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 Obecné metody mohou být přetíženy na několik parametrů typu. Například následující metody můžete všechny nacházet ve stejné třídě:  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 Další informace najdete v tématu [Specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
