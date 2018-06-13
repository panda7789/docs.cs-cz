---
title: 'Postupy: Použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: c2bc990f9dda4b91928c176cf7f10bfb349ba343
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319322"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Postupy: Použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu (Průvodce programováním v C#)
Implicitně typované lokální proměnné můžete použít vždy, když chcete kompilátoru k určení typu místní proměnné. Implicitně typované lokální proměnné je nutné použít k uložení anonymní typy, které se často používají ve výrazech dotazů. Následující příklady znázorňují volitelné a vyžaduje použití implicitně typované lokální proměnné v dotazech.  
  
 Implicitně typované lokální proměnné jsou deklarovány s použitím [var](../../../csharp/language-reference/keywords/var.md) kontextové klíčové slovo. Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [implicitně typované pole](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje běžný scénář, ve kterém `var` je požadováno klíčové slovo: výrazu dotazu, který produkuje posloupnost anonymní typy. V tomto scénáři proměnnou dotazu a proměnné iterace ve `foreach` příkazu musí být implicitně typované pomocí `var` vzhledem k tomu, že nemáte přístup k typu název anonymního typu. Další informace o anonymních typech najdete v tématu [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `var` – klíčové slovo v situaci, který je podobný, ale ve kterém použití `var` je volitelný. Protože `student.LastName` je řetězec, provádění dotaz vrací posloupnost řetězce. Proto typ `queryID` může být deklarována jako `System.Collections.Generic.IEnumerable<string>` místo `var`. – Klíčové slovo `var` slouží ke zvýšení pohodlí. V příkladu proměnné iterace ve `foreach` příkaz je explicitně zadán jako řetězec, ale místo toho se může deklarovat pomocí `var`. Protože typ proměnné iterace není anonymní typ použití `var` je možnost, která nevyžaduje. Pamatujte si, že `var` samotné není typu, ale instrukce pro kompilátor odvození a typ přiřazení.  
  
 [!code-csharp[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)
