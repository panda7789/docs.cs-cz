---
title: Obecné metody - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 28ce14eca4398a359061a54b7c6cc74ed69b87b1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244814"
---
# <a name="generic-methods-c-programming-guide"></a>Obecné metody (Průvodce programováním v C#)
Obecná metoda je metoda, která je deklarována s parametry typu, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 Následující příklad kódu ukazuje jeden způsob, jak volat metodu pomocí `int` pro argument typu:  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 Také můžete vynechat argument typu a kompilátor odvodí. Následující volání `Swap` je ekvivalentem předchozího volání:  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 Stejná pravidla pro odvození typu platí pro statické metody a metody instance. Kompilátor může odvodit typ parametrů na základě argumentů metody, které můžete předat nelze jej odvodit jenom z omezení parametry typu nebo návratovou hodnotu. Odvození typu proměnné proto nefunguje s metodami, které mají žádné parametry. Odvození typu vyvolá v době kompilace předtím, než kompilátor pokusí přeložit podpisy přetížené metody. Kompilátor použije logiku odvození typu na všechny obecné metody, které mají stejný název. V kroku rozlišení přetížení kompilátor obsahuje pouze tyto obecné metody, na které bylo úspěšné odvození typu proměnné.  
  
 V rámci obecné třídy neobecné metody mají přístup k úrovni třídy typové parametry, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 Při definování obecné metody, která má stejné parametry typu jako obsahující třídu, kompilátor vygeneruje upozornění CS0693, protože v rámci oboru metody argument zadaný pro vnitřní `T` skryje argument zadaný pro vnější `T`. Pokud požadujete flexibilitu volání metody obecnou třídu s argumenty typů než ty, pokud byla vytvořena instance třídy, zvažte poskytnutí jiný identifikátor pro typ parametru metody, jak je znázorněno v `GenericList2<T>` následující Příklad.  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 Umožňuje povolit více specializované operace u parametrů typu v metodách omezení. Tato verze `Swap<T>`teď s názvem `SwapIfGreater<T>`, lze použít pouze s argumenty typů, které implementují <xref:System.IComparable%601>.  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 Obecné metody lze přetížit na několik parametrů typu. Například následující metody můžete všechny nacházet ve stejné třídě:  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/classes.md#methods).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
