---
title: 'Postupy: Použití výrazů Lambda v dotazu - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: bdcf93679664f8761e8ed32550027a2337374ffa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643582"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Postupy: Použití výrazů Lambda v dotazu (C# Průvodce programováním v)
Nepoužívat výrazy lambda přímo v syntaxi dotazů, ale je použít ve volání metody a výrazy dotazů můžou obsahovat volání metody. Ve skutečnosti nějakých operací dotazů lze vyjádřit pouze v syntaxe metody. Další informace o rozdílech mezi syntaxi dotazů a syntaxe využívající metody, naleznete v tématu [syntaxi dotazů a syntaxe využívající metody v jazyce LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí výrazu lambda v dotazu založených na volání metody <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> standardní operátor dotazu. Všimněte si, že <xref:System.Linq.Enumerable.Where%2A> metoda v tomto příkladu má vstupní parametr typu delegáta <xref:System.Func%601> a tohoto delegáta celého čísla jako vstup převezme a vrátí logickou hodnotu. Výraz lambda lze převést na tento delegát. To šlo [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dotaz, který se používá <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> typ parametru metody, bude `Expression<Func<int,bool>>` však lambda výraz by vypadat stejně. Další informace o typu výrazu naleznete v tématu <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít výraz lambda ve volání metody, výrazu dotazu. Výraz lambda je nezbytné vzhledem k tomu <xref:System.Linq.Enumerable.Sum%2A> standardní operátor dotazu nelze vyvolat pomocí syntaxe dotazu.  
  
 Dotaz nejprve skupiny studentů podle jejich úrovně na podnikové úrovni, jak jsou definovány v `GradeLevel` výčtu. Potom pro každou skupinu přidá celkové hodnocení pro každého studenta. To vyžaduje dvě `Sum` operace. Vnitřní `Sum` vypočítá celkové skóre pro každého studenta a vnější `Sum` udržuje spuštěné, celkový součet všech studentů ve skupině.  
  
 [!code-csharp[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li spustit tento kód, zkopírujte a vložte metodu do `StudentClass` , který je součástí [jak: Dotazování kolekci objektů](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) a volejte jej z `Main` metody.  
  
## <a name="see-also"></a>Viz také:

- [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Stromy výrazů (C#)](../concepts/expression-trees/index.md)
