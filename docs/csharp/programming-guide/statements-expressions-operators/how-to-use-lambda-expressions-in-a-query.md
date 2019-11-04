---
title: 'Postupy: použití výrazů lambda v průvodci C# programováním dotazů'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: e7e7da211599b5ce0263377ecaf25b404399ce9c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423170"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Postupy: Použití výrazů lambda v dotazu (Průvodce programováním v C#)
Lambda výrazy nepoužíváte přímo v syntaxi dotazu, ale můžete je použít v voláních metody a výrazy dotazů mohou obsahovat volání metody. Některé operace dotazu je ve skutečnosti možné vyjádřit pouze v syntaxi metody. Další informace o rozdílu mezi syntaxí dotazu a syntaxí metody naleznete [v tématu Syntaxe dotazu a syntaxe metody v jazyce LINQ](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít výraz lambda v dotazu založeném na metodě pomocí operátoru dotazu <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> Standard. Všimněte si, že metoda <xref:System.Linq.Enumerable.Where%2A> v tomto příkladu má vstupní parametr typu delegáta <xref:System.Func%602> a tento delegát přebírá jako vstup celé číslo a vrací logickou hodnotu. Výraz lambda lze převést na tento delegát. Pokud se jednalo o [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dotaz, který použil metodu <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>, typ parametru by byl `Expression<Func<int,bool>>`, ale výraz lambda by vypadal přesně stejně. Další informace o typu výrazu naleznete v tématu <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít výraz lambda ve volání metody výrazu dotazu. Lambda je nezbytná, protože operátor dotazu <xref:System.Linq.Enumerable.Sum%2A> Standard nelze vyvolat pomocí syntaxe dotazu.  
  
 Dotaz nejprve seskupí studenty podle úrovně jejich úrovně, jak je definováno ve výčtu `GradeLevel`. Pak pro každou skupinu přidá celkové skóre pro každého studenta. To vyžaduje dvě operace `Sum`. Vnitřní `Sum` vypočítá celkové skóre pro každého studenta a vnější `Sum` udržuje běžící a kombinované součty pro všechny studenty ve skupině.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li spustit tento kód, zkopírujte a vložte metodu do `StudentClass`, který je k dispozici v tématu [Postupy: vytvoření dotazu na kolekci objektů](../../linq/query-a-collection-of-objects.md) a jejich volání z metody `Main`.  
  
## <a name="see-also"></a>Viz také:

- [Výrazy lambda](./lambda-expressions.md)
- [Stromy výrazů (C#)](../concepts/expression-trees/index.md)
