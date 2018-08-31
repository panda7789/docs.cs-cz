---
title: 'Postupy: Použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: fa76236cc4144cd591a5bfd7cb9cb85f26f7f82c
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43253336"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Postupy: Použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu (Průvodce programováním v C#)
Implicitně typované lokální proměnné lze použít, když chcete, aby kompilátor určit typ místní proměnné. Implicitně typované lokální proměnné musíte použít k ukládání anonymní typy, které se často používají ve výrazech dotazů. Následující příklady ilustrují použití povinných a volitelných implicitně typované lokální proměnné v dotazech.  
  
 Implicitně typované lokální proměnné jsou deklarovány pomocí [var](../../../csharp/language-reference/keywords/var.md) kontextové klíčové slovo. Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [implicitně typované pole](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje běžný scénář, ve kterém `var` je požadováno klíčové slovo: výraz dotazu, který generuje sekvenci anonymních typů. V tomto scénáři, proměnná dotazu a iterační proměnné v `foreach` příkazu musí být implicitně typována pomocí `var` vzhledem k tomu, že nemáte přístup k názvu typu pro anonymního typu. Další informace o anonymních typech najdete v tématu [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `var` – klíčové slovo v situaci, která se podobá, ale ve kterém použití `var` je volitelný. Protože `student.LastName` je řetězec, spuštění vrátí dotazu sekvencí řetězců. Proto typ `queryID` by mohla být deklarována jako `System.Collections.Generic.IEnumerable<string>` místo `var`. Klíčové slovo `var` slouží ke zvýšení pohodlí. V příkladu, iterační proměnná ve `foreach` příkazu je explicitně zadán jako řetězec, ale místo toho ji může deklarovaná příkazem using `var`. Protože typ proměnné iterace není anonymního typu použití `var` je možnost, která nevyžaduje. Mějte na paměti, `var` samotný není typu, ale instrukce kompilátoru odvodit a přiřadit typu.  
  
 [!code-csharp[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [LINQ (Language-Integrated Query)](../../../csharp/linq/index.md) [var](../../../csharp/language-reference/keywords/var.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)
