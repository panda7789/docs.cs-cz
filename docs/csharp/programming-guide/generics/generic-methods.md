---
title: Obecné metody – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 5f066ca39c97b70554886e423c37c4ee47d49158
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712192"
---
# <a name="generic-methods-c-programming-guide"></a>Obecné metody (Průvodce programováním v C#)
Obecná metoda je metoda, která je deklarována s parametry typu, a to následovně:  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 Následující příklad kódu ukazuje jeden způsob volání `int` metody pomocí argumentu typu:  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 Můžete také vynechat argument typu a kompilátor jej odvodí. Následující volání `Swap` je ekvivalentní předchozímu volání:  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 Stejná pravidla pro odvození typu platí pro statické metody a metody instancí. Kompilátor může odvodit parametry typu na základě argumentů metody, které předáte; nelze odvodit parametry typu pouze z omezení nebo vrácené hodnoty. Proto odvození typu nefunguje s metodami, které nemají žádné parametry. Odvození typu dochází v době kompilace před kompilátor pokusí vyřešit přetížené podpisy metody. Kompilátor použije logiku odvození typu na všechny obecné metody, které sdílejí stejný název. V kroku řešení přetížení kompilátor zahrnuje pouze ty obecné metody, na kterých byl úspěšný odvození typu.  
  
 V rámci obecné třídy mohou neobecné metody přistupovat k parametrům typu na úrovni třídy následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 Pokud definujete obecnou metodu, která přebírá stejné parametry typu jako obsahující třída, kompilátor generuje upozornění [CS0693,](../../misc/cs0693.md) protože v rámci oboru metody argument zadaný pro vnitřní `T` skryje argument zadaný pro vnější `T`. Pokud požadujete flexibilitu volání metody obecné třídy s argumenty typu jiné než ty, které byly poskytnuty při vytvoření instance třídy, `GenericList2<T>` zvažte poskytnutí jiného identifikátoru pro parametr typu metody, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 Pomocí omezení povolte specializovanější operace parametrů typu v metodách. Tuto verzi `Swap<T>`aplikace `SwapIfGreater<T>`, nyní pojmenovanou , lze <xref:System.IComparable%601>použít pouze s argumenty typu , které implementují .  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 Obecné metody mohou být přetíženy na několik parametrů typu. Například všechny následující metody mohou být umístěny ve stejné třídě:  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/classes.md#methods).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- [Programovací příručka jazyka C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Metody](../classes-and-structs/methods.md)
