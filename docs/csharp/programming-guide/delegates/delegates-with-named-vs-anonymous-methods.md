---
title: Delegáti s pojmenovanými vs. Anonymní metody - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 586ad5a59eebb03ed9ed6bea68d232a6b249c3c9
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241483"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Delegáti s pojmenovanými vs. Anonymní metody (Průvodce programováním v C#)
A [delegovat](../../../csharp/language-reference/keywords/delegate.md) lze přidružit metodu s názvem. Když vytvoříte instanci delegátu pomocí metodu s názvem, je metoda předaného jako parametr, například:  
  
 [!code-csharp[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 Tomu se říká pomocí pojmenovanou metodu. Delegáti zkonstruován pomocí metodu s názvem může zapouzdřit buď [statické](../../../csharp/language-reference/keywords/static.md) metodu nebo metodu instance. Jediný způsob, jak vytvořit instanci delegáta v dřívějších verzích jazyka C# jsou pojmenované metody. Ale v situaci, kde vytvoření nové metody nežádoucí režie, C# umožňuje instanci delegátu a okamžitě určit blok kódu, který bude zpracovávat delegáta, když je volána. Blok může obsahovat výraz lambda nebo anonymní metodu. Další informace najdete v tématu [anonymní funkce](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="remarks"></a>Poznámky  
 Metoda, která je předat jako parametr delegáta musí mít stejný podpis jako delegát deklarace.  
  
 Instanci delegáta může zapouzdřit statických nebo metodu instance.  
  
 I když můžete použít delegáta [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr, nedoporučujeme její použití s delegáty vícesměrového vysílání událostí protože nelze zjistit, které delegát, zavolá se.  
  
## <a name="example-1"></a>Příklad 1  
 Toto je jednoduchý příklad deklarování a použití delegáta. Všimněte si, že oba delegáta, `Del`a přidruženou metodu `MultiplyNumbers`, mají stejnou signaturu  
  
 [!code-csharp[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## <a name="example-2"></a>Příklad 2  
 V následujícím příkladu, jeden delegáta se mapuje na statické a instanci metody a vrátí konkrétní informace z každého.  
  
 [!code-csharp[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
- [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [Postupy: Kombinování delegátů (vícesměroví delegáti)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
- [Události](../../../csharp/programming-guide/events/index.md)
