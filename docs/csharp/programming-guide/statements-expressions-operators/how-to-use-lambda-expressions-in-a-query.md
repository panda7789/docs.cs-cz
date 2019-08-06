---
title: 'Postupy: Použití výrazů lambda v průvodci C# programováním dotazů'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: ad9feed7ea3d96267d632f4ca4bc992f2c8d335f
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796655"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Postupy: Použití výrazů lambda v dotazu (C# Průvodce programováním)
Lambda výrazy nepoužíváte přímo v syntaxi dotazu, ale můžete je použít v voláních metody a výrazy dotazů mohou obsahovat volání metody. Některé operace dotazu je ve skutečnosti možné vyjádřit pouze v syntaxi metody. Další informace o rozdílu mezi syntaxí dotazu a syntaxí metody naleznete [v tématu Syntaxe dotazu a syntaxe metody v jazyce LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít výraz lambda v dotazu založeném na metodě pomocí <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> standardního operátoru dotazu. Všimněte si, <xref:System.Linq.Enumerable.Where%2A> že metoda v tomto příkladu má vstupní parametr typu <xref:System.Func%602> delegáta a že delegát přebírá jako vstup celé číslo a vrátí logickou hodnotu. Výraz lambda lze převést na tento delegát. Pokud se jednalo [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] o dotaz, který <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> použil metodu, typ `Expression<Func<int,bool>>` parametru by byl, ale výraz lambda by vypadal přesně stejně. Další informace o typu výrazu naleznete v tématu <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít výraz lambda ve volání metody výrazu dotazu. Lambda je nezbytná, protože <xref:System.Linq.Enumerable.Sum%2A> standardní operátor dotazu nelze vyvolat pomocí syntaxe dotazu.  
  
 Dotaz nejprve seskupí studenty podle úrovně jejich úrovně, jak je definováno ve `GradeLevel` výčtu. Pak pro každou skupinu přidá celkové skóre pro každého studenta. To vyžaduje dvě `Sum` operace. Vnitřní `Sum` vypočítá celkové skóre pro každého studenta a `Sum` u každého studenta zůstane spuštěný kombinovaný součet pro všechny studenty ve skupině.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li spustit tento kód, zkopírujte a vložte metodu do `StudentClass` , který je k [dispozici v tématu How to: Dotaz na kolekci objektů](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) a jejich volání `Main` z metody.  
  
## <a name="see-also"></a>Viz také:

- [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Stromy výrazů (C#)](../concepts/expression-trees/index.md)
