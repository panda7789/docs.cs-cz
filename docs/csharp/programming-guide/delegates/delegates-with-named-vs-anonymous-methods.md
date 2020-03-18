---
title: Delegáti s pojmenovanými vs. anonymními metodami – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 1ec366999ca6457471b705fa83f06fcde4293f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712374"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Delegáti s pojmenovanými vs. anonymními metodami (Průvodce programováním v C#)
[Delegát](../../language-reference/builtin-types/reference-types.md) může být přidružen k pojmenované metodě. Při vytváření instanci delegáta pomocí pojmenované metody je metoda předána jako parametr, například:  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 To se nazývá pomocí pojmenované metody. Delegáti vytvořená s pojmenovanou metodou mohou zapouzdřit [statickou](../../language-reference/keywords/static.md) metodu nebo metodu instance. Pojmenované metody jsou jediným způsobem, jak vytvořit konkretizovat delegáta v dřívějších verzích jazyka C#. Však v situaci, kdy vytváření nové metody je nežádoucí režie, C# umožňuje vytvořit instanci delegáta a okamžitě zadat blok kódu, který delegát zpracuje, když je volána. Blok může obsahovat výraz lambda nebo anonymní metodu. Další informace naleznete [v tématu Anonymní funkce](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="remarks"></a>Poznámky  
 Metoda, kterou předáte jako parametr delegáta, musí mít stejný podpis jako deklarace delegáta.  
  
 Instance delegáta může zapouzdřit statickou metodu nebo metodu instance.  
  
 Přestože delegát může použít [out](../../language-reference/keywords/out-parameter-modifier.md) parametr, nedoporučujeme jeho použití s delegáty událostí vícesměrového vysílání, protože nemůžete vědět, který delegát bude volán.  
  
## <a name="example-1"></a>Příklad 1  
 Následuje jednoduchý příklad deklarování a používání delegáta. Všimněte si, `Del`že delegát , `MultiplyNumbers`a přidružená metoda , mají stejný podpis  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a>Příklad 2  
 V následujícím příkladu je jeden delegát mapován na statické metody a metody instance a vrací konkrétní informace z každého z nich.  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Delegáty](./index.md)
- [Jak kombinovat delegáty (delegáti vícesměrového vysílání)](./how-to-combine-delegates-multicast-delegates.md)
- [Akce](../events/index.md)
