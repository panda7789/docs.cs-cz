---
title: Delegáti s pojmenovanými vs. anonymními metodami – Průvodce programováním v C#
description: Přečtěte si o delegátech pomocí pojmenovaných vs. anonymních metod. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 940363b87e17b34feeffaff38ed498d6fcf6850a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302747"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Delegáti s pojmenovanými vs. anonymními metodami (Průvodce programováním v C#)
[Delegát](../../language-reference/builtin-types/reference-types.md) může být spojen s pojmenovanou metodou. Při vytváření instance delegáta pomocí pojmenované metody je metoda předána jako parametr, například:  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 Tato metoda je volána pomocí pojmenované metody. Delegáty vytvořené pomocí pojmenované metody mohou zapouzdřit buď [statickou](../../language-reference/keywords/static.md) metodu, nebo metodu instance. Pojmenované metody jsou jediným způsobem, jak vytvořit instanci delegáta v dřívějších verzích jazyka C#. Nicméně v situaci, kdy je vytvoření nové metody nežádoucí režie, vám jazyk C# umožňuje vytvořit instanci delegáta a okamžitě zadat blok kódu, který bude při volání zpracován delegátem. Blok může obsahovat buď výraz lambda, nebo anonymní metodu. Další informace najdete v tématu [anonymní funkce](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="remarks"></a>Poznámky  
 Metoda, kterou předáte jako parametr delegáta, musí mít stejnou signaturu jako deklarace delegáta.  
  
 Instance delegáta může zapouzdřit buď statickou, nebo metodu instance.  
  
 I když delegát může použít [výstupní](../../language-reference/keywords/out-parameter-modifier.md) parametr, nedoporučujeme ho používat s delegáty událostí vícesměrového vysílání, protože nemůžete zjistit, který delegát se bude volat.  
  
## <a name="example-1"></a>Příklad 1  
 Následuje jednoduchý příklad deklarace a použití delegáta. Všimněte si, že delegát, i `Del` přidružená metoda `MultiplyNumbers` mají stejnou signaturu.  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a>Příklad 2  
 V následujícím příkladu je jeden delegát mapován na statické a instanční metody a vrátí konkrétní informace z každého z nich.  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Delegáti](./index.md)
- [Postup kombinování delegátů (Delegáti vícesměrového vysílání)](./how-to-combine-delegates-multicast-delegates.md)
- [Události](../events/index.md)
