---
title: orderby – klauzule (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 1fd0036e8bd3c838fe92ca27635cd7638d59ef1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="orderby-clause-c-reference"></a>orderby – klauzule (Referenční dokumentace jazyka C#)
Ve výrazu dotazu `orderby` klauzule způsobí, že vrácený pořadí nebo dalším (skupiny), který se má seřadit ve vzestupném nebo sestupném pořadí. Aby bylo možné provést jednu nebo více operací sekundární řazení lze zadat více klíčů. Toto řazení je prováděno pomocí porovnávače výchozí pro typ elementu. Výchozí pořadí řazení je vzestupně. Můžete také zadat vlastní porovnávací funkci. Je však pouze k dispozici pomocí syntaxe na základě metod. Další informace najdete v tématu [řazení dat](../../programming-guide/concepts/linq/sorting-data.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu první dotaz seřadí slova v abecedním pořadí spouštění z A a druhý dotaz seřadí stejná slova v sestupném pořadí. ( `ascending` – Klíčové slovo je výchozí hodnota řazení a lze vynechat.)  
  
 [!code-csharp[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad primární řazení na na studentů příjmení a sekundární řazení provádí jejich názvy první.  
  
 [!code-csharp[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]  
  
## <a name="remarks"></a>Poznámky  
 Při kompilaci `orderby` přeložen volání <xref:System.Linq.Enumerable.OrderBy%2A> metoda. Více klíčů v `orderby` klauzule nepřeloží na <xref:System.Linq.Enumerable.ThenBy%2A> volání metody.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Klíčová slova dotazu (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [group – klauzule](../../../csharp/language-reference/keywords/group-clause.md)  
 [Začínáme s dotazy LINQ v jazyce C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
