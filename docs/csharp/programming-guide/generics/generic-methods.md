---
title: Obecné metody – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 5f066ca39c97b70554886e423c37c4ee47d49158
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712192"
---
# <a name="generic-methods-c-programming-guide"></a>Obecné metody (Průvodce programováním v C#)
Obecná metoda je metoda, která je deklarována s parametry typu, následovně:  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 Následující příklad kódu ukazuje jeden ze způsobů, jak volat metodu pomocí `int` pro argument typu:  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 Můžete také vynechat argument typu a kompilátor ho odvodí. Následující volání `Swap` je ekvivalentní předchozímu volání:  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 Stejná pravidla pro odvození typu se vztahují na statické metody a metody instance. Kompilátor může odvodit parametry typu na základě argumentů metody, které předáte; nemůže odvodit parametry typu jenom z omezení nebo návratové hodnoty. Proto odvození typu nefunguje s metodami, které nemají žádné parametry. K odvození typu dojde v době kompilace předtím, než se kompilátor pokusí přeložit signatury přetížené metody. Kompilátor aplikuje logiku odvození typu na všechny obecné metody, které mají stejný název. V kroku řešení přetížení obsahuje kompilátor pouze ty obecné metody, na které bylo odvození typu úspěšné.  
  
 V rámci obecné třídy mohou neobecné metody získat přístup k parametrům typu na úrovni třídy, a to následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 Definujete-li obecnou metodu, která přebírá stejné parametry typu jako obsahující třídu, kompilátor vygeneruje upozornění [CS0693](../../misc/cs0693.md) , protože v rámci rozsahu metod, argument zadaný pro vnitřní `T` skryje argument dodaný pro vnější `T`. Pokud požadujete flexibilitu při volání obecné metody třídy s argumenty typu jiné než ty, které jsou zadány při vytváření instance třídy, zvažte zadání jiného identifikátoru pro parametr typu metody, jak je znázorněno v následujícím příkladu v `GenericList2<T>`.  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 Použijte omezení pro povolení více specializovaných operací u parametrů typu v metodách. Tuto verzi `Swap<T>`, která je nyní pojmenována `SwapIfGreater<T>`, lze použít pouze s argumenty typu, které implementují <xref:System.IComparable%601>.  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 Obecné metody mohou být přetíženy u několika parametrů typu. Například následující metody mohou být umístěny ve stejné třídě:  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a>C# – jazyková specifikace  
 Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/classes.md#methods).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Metody](../classes-and-structs/methods.md)
