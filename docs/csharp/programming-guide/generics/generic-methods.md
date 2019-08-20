---
title: Obecné metody – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 600bb249d1bc1e9f68026caf6596e0a35bb97c43
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589707"
---
# <a name="generic-methods-c-programming-guide"></a>Obecné metody (Průvodce programováním v C#)
Obecná metoda je metoda, která je deklarována s parametry typu, následovně:  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 Následující příklad kódu ukazuje jeden ze způsobů, jak volat metodu pomocí `int` argumentu typu:  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 Můžete také vynechat argument typu a kompilátor ho odvodí. Následující volání `Swap` je ekvivalentní předchozímu volání:  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 Stejná pravidla pro odvození typu se vztahují na statické metody a metody instance. Kompilátor může odvodit parametry typu na základě argumentů metody, které předáte; nemůže odvodit parametry typu jenom z omezení nebo návratové hodnoty. Proto odvození typu nefunguje s metodami, které nemají žádné parametry. K odvození typu dojde v době kompilace předtím, než se kompilátor pokusí přeložit signatury přetížené metody. Kompilátor aplikuje logiku odvození typu na všechny obecné metody, které mají stejný název. V kroku řešení přetížení obsahuje kompilátor pouze ty obecné metody, na které bylo odvození typu úspěšné.  
  
 V rámci obecné třídy mohou neobecné metody získat přístup k parametrům typu na úrovni třídy, a to následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 Definujete-li obecnou metodu, která přebírá stejné parametry typu jako obsahující třídu, kompilátor vygeneruje upozornění [CS0693](../../misc/cs0693.md) , protože v rámci oboru metody vygeneruje argument pro vnitřní `T` hodnotu argumentu, který je zadán pro vnější `T`. Pokud požadujete flexibilitu při volání obecné metody třídy s argumenty typu jiné než ty, které jsou zadány při vytváření instance třídy, zvažte zadání jiného identifikátoru pro parametr typu metody, jak je znázorněno `GenericList2<T>` v následujícím příkladu. případě.  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 Použijte omezení pro povolení více specializovaných operací u parametrů typu v metodách. Tato verze `Swap<T>`, která je nyní `SwapIfGreater<T>`pojmenována, může být použita pouze s argumenty <xref:System.IComparable%601>typu, které implementují.  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 Obecné metody mohou být přetíženy u několika parametrů typu. Například následující metody mohou být umístěny ve stejné třídě:  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/classes.md#methods).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Metody](../classes-and-structs/methods.md)
