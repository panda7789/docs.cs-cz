---
title: "Delegáti s pojmenované vs. Anonymní metody (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 59317ad3cd9a5d360d0375bf46ff0c9f752a5944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Delegáti s pojmenované vs. Anonymní metody (Průvodce programováním v C#)
A [delegovat](../../../csharp/language-reference/keywords/delegate.md) může být přidružen metodu s názvem. Pokud instanci delegáta můžete vytvořit pomocí metodu s názvem, metodu předávána jako parametr, například:  
  
 [!code-csharp[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 Tomu se říká pomocí metodu s názvem. Delegáti zkonstruovat s metodu s názvem může zapouzdřit buď [statické](../../../csharp/language-reference/keywords/static.md) metodu nebo metody instance. Pojmenované metody jsou jediný způsob, jak vytvořit instanci delegáta v dřívějších verzích systému C#. Ale v situaci, kdy vytvoření nové metody nežádoucí režie, C# umožňuje vytvořit instanci delegáta a okamžitě zadejte blok kódu, která zpracuje delegáta, když je volána. Blok může obsahovat výraz lambda nebo anonymní metody. Další informace najdete v tématu [anonymní funkce](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="remarks"></a>Poznámky  
 Metoda, kterou předáte jako parametr delegáta musí mít stejný podpis jako deklaraci delegáta.  
  
 Instanci delegáta může zapouzdřit buď statickou nebo metodu instance.  
  
 I když delegát můžete použít [out](../../../csharp/language-reference/keywords/out.md) parametr, nedoporučujeme jeho použití s delegáty vícesměrového vysílání událostí protože nelze zjistit, které delegáta bude volána.  
  
## <a name="example-1"></a>Příklad 1  
 Toto je jednoduchý příklad deklarování a použití delegáta. Všimněte si, že oba delegáta, `Del`a metodu přidružené `MultiplyNumbers`, mají stejným podpisem  
  
 [!code-csharp[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## <a name="example-2"></a>Příklad 2  
 V následujícím příkladu je namapovaný jeden delegáta statických a instanci metody a vrátí konkrétní informace z každého.  
  
 [!code-csharp[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
 [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [Postupy: kombinování delegátů (vícesměroví delegáti)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
 [Události](../../../csharp/programming-guide/events/index.md)
