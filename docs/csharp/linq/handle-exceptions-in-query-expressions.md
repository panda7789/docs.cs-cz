---
title: "Zpracování výjimek ve výrazech dotazů"
description: "Postupy: zpracování výjimek ve výrazech dotazů."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 376bd461bfeb51653471fd374a2215aa15872976
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="handle-exceptions-in-query-expressions"></a>Zpracování výjimek ve výrazech dotazů

Je možné volat jakékoli metody v kontextu výrazu dotazu. Doporučujeme však vyhnout voláním jakékoli metody ve výrazu dotazu, který může vytvářet vedlejším účinkem například změně obsahu zdroj dat nebo došlo k výjimce. Tento příklad ukazuje, jak se vyhnout vyvolání výjimky při volání metody ve výrazu dotazu bez narušení obecné pokyny rozhraní .NET Framework na zpracování výjimek. Tyto pokyny stavu, který se dá zachycení určité výjimky, když je pochopit, proč bude vyvolána v daném kontextu. Další informace najdete v tématu [osvědčené postupy pro výjimky](../../standard/exceptions/best-practices-for-exceptions.md).  
  
 Poslední příklad ukazuje, jak zpracování těchto případech, pokud musíte vyvolat výjimku během provádění dotazu.  
  
## <a name="example"></a>Příklad  

 Následující příklad ukazuje, jak přesunout kódu mimo výraz dotazu pro zpracování výjimek. To je možné pouze, pokud metoda nezávisí na žádné proměnné, které jsou místní pro dotaz.  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a>Příklad 

 V některých případech může být okamžitě zabránit spuštění dotazu nejlepší odpověď na výjimku, která je vyvolána od v dotazu. Následující příklad ukazuje, jak zpracování výjimek, které mohou být vyvolány z uvnitř text dotazu. Předpokládáme, že `SomeMethodThatMightThrow` může potenciálně způsobit výjimku, která vyžaduje spuštění dotazu zastavit.  
  
 Všimněte si, že `try` uzavře bloku `foreach` smyčky a není dotaz. Důvodem je, že `foreach` smyčka je bod, ve kterém je ve skutečnosti spustit dotaz. Další informace najdete v tématu [Úvod do dotazů LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)
