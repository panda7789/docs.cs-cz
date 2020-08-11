---
title: Použití výrazů lambda v dotazu – Průvodce programováním v C#
description: Naučte se používat lambda výrazy v dotazu. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: ef8a7e3b4cd5302d6c928ad7ad81811797777b4a
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063247"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Použití výrazů lambda v dotazu (Průvodce programováním v C#)
Lambda výrazy nepoužíváte přímo v syntaxi dotazu, ale můžete je použít v voláních metody a výrazy dotazů mohou obsahovat volání metody. Některé operace dotazu je ve skutečnosti možné vyjádřit pouze v syntaxi metody. Další informace o rozdílu mezi syntaxí dotazu a syntaxí metody naleznete [v tématu Syntaxe dotazu a syntaxe metody v jazyce LINQ](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít výraz lambda v dotazu založeném na metodě pomocí <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> standardního operátoru dotazu. Všimněte si, že <xref:System.Linq.Enumerable.Where%2A> metoda v tomto příkladu má vstupní parametr typu delegáta <xref:System.Func%602> a že delegát přebírá jako vstup celé číslo a vrátí logickou hodnotu. Výraz lambda lze převést na tento delegát. Pokud se jednalo o [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dotaz, který použil <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> metodu, typ parametru by byl, `Expression<Func<int,bool>>` ale výraz lambda by vypadal přesně stejně. Další informace o typu výrazu naleznete v tématu <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType> .  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít výraz lambda ve volání metody výrazu dotazu. Lambda je nezbytná, protože <xref:System.Linq.Enumerable.Sum%2A> standardní operátor dotazu nelze vyvolat pomocí syntaxe dotazu.  
  
 Dotaz nejprve seskupí studenty podle úrovně jejich úrovně, jak je definováno ve `GradeLevel` výčtu. Pak pro každou skupinu přidá celkové skóre pro každého studenta. To vyžaduje dvě `Sum` operace. Vnitřní `Sum` vypočítá celkové skóre pro každého studenta a u každého studenta `Sum` zůstane spuštěný kombinovaný součet pro všechny studenty ve skupině.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li spustit tento kód, zkopírujte a vložte metodu do objektu `StudentClass` , který je k dispozici v [dotazu na kolekci objektů](../../linq/query-a-collection-of-objects.md) a zavolejte ji z `Main` metody.
  
## <a name="see-also"></a>Viz také

- [Výrazy lambda](../../language-reference/operators/lambda-expressions.md)
- [Stromy výrazů (C#)](../concepts/expression-trees/index.md)
