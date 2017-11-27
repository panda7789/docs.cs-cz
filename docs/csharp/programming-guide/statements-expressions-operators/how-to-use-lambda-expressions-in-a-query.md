---
title: "Postupy: Použití výrazů lambda v dotazu (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ccc94b1932336ff4a6b1787304846114869400e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Postupy: Použití výrazů lambda v dotazu (Průvodce programováním v C#)
Nepoužívejte výrazy lambda přímo v syntaxi dotazu, ale je použijete v volání metod a výrazy dotazů může obsahovat volání metody. Ve skutečnosti některé operace dotazů lze vyjádřit pouze v syntaxe využívající metody. Další informace o rozdílu mezi syntaxe dotazů a syntaxe využívající metody najdete v tématu [syntaxe dotazů a syntaxe využívající metody v technologii LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí výrazu lambda v dotazu na základě metod pomocí <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operátor standardní dotazu. Všimněte si, že <xref:System.Linq.Enumerable.Where%2A> metoda v tomto příkladu má vstupní parametr typu delegáta <xref:System.Func%601> a přidělíte trvá celé jako vstup a vrátí logickou hodnotu. Výrazu lambda může být převeden na tohoto delegáta. Pokud to bylo [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dotaz, který používá <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> metoda, typ parametru by `Expression<Func\<int,bool>>` ale výrazu lambda vypadat přesně stejný. Další informace o typ výrazu najdete v tématu <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí výrazu lambda ve volání metody výrazu dotazu. Argument lambda je nutné vzhledem k tomu <xref:System.Linq.Enumerable.Sum%2A> operátor standardní dotazu nelze vyvolat pomocí syntaxe dotazu.  
  
 Dotaz nejprve skupiny studenty podle jejich úrovni úrovni, jak jsou definovány v `GradeLevel` výčtu. Potom pro každou skupinu přidá celkové skóre pro každý student. To vyžaduje dvě `Sum` operace. Vnitřní `Sum` vypočítá celkové skóre pro každý student a vnější `Sum` udržuje spuštěný, celkem pro všechny studenty ve skupině.  
  
 [!code-csharp[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pokud chcete spustit tento kód, zkopírujte a vložte metodu do `StudentClass` poskytované v [postupy: dotazování kolekci objektů](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) a volat z `Main` metoda.  
  
## <a name="see-also"></a>Viz také  
 [Lambda – výrazy](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Stromy výrazů](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
