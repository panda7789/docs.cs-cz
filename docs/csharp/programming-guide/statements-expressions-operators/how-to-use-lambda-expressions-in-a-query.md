---
title: Použití výrazů lambda v dotazu – Programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 92bdbf842c5c30b2f32e06f622f3e08f3c7a878f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711958"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Použití výrazů lambda v dotazu (Průvodce programováním jazyka C#)
Nepoužívejte výrazy lambda přímo v syntaxi dotazu, ale používáte je v volání metod a výrazy dotazu mohou obsahovat volání metod. Ve skutečnosti některé operace dotazu lze vyjádřit pouze v syntaxi metody. Další informace o rozdílu mezi syntaxí dotazu a syntaxí metody naleznete [v tématu Syntaxe dotazu a syntaxe metody v LINQ](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat výraz lambda v dotazu <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> založeném na metodách pomocí standardního operátoru dotazu. Všimněte <xref:System.Linq.Enumerable.Where%2A> si, že metoda v tomto příkladu má vstupní parametr typu <xref:System.Func%602> delegáta a delegát bere celé číslo jako vstup a vrátí boolean. Výraz lambda lze převést na tohoto delegáta. Pokud by [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] se jednalo <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> o dotaz, který `Expression<Func<int,bool>>` používá metodu, typ parametru by byl, ale výraz lambda by vypadal přesně stejně. Další informace o typu Výraz <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>naleznete v tématu .  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat výraz lambda ve volání metody výrazu dotazu. Lambda je nezbytné, <xref:System.Linq.Enumerable.Sum%2A> protože standardní operátor dotazu nelze vyvolat pomocí syntaxe dotazu.  
  
 Dotaz nejprve seskupí studenty podle `GradeLevel` úrovně jejich hodnocení, jak je definováno ve výčtu. Pak pro každou skupinu přidá celkové skóre pro každého studenta. To vyžaduje `Sum` dvě operace. Vnitřní `Sum` vypočítá celkové skóre pro každého studenta `Sum` a vnější udržuje běh, kombinovaný součet pro všechny studenty ve skupině.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li spustit tento kód, zkopírujte a vložte metodu `StudentClass` do, která je k dispozici v [dotazu kolekce objektů](../../linq/query-a-collection-of-objects.md) a volat z `Main` metody.
  
## <a name="see-also"></a>Viz také

- [Lambda výrazy](./lambda-expressions.md)
- [Stromy výrazů (C#)](../concepts/expression-trees/index.md)
