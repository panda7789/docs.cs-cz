---
title: Operátory převodu (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: cbf6a83d43a1b3a69e82a35d5d0875f62422cd3f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787820"
---
# <a name="conversion-operators-c-programming-guide"></a>Operátory převodu (Průvodce programováním v C#)
C# umožňuje programátorům deklarovat převody na třídy nebo struktury tak, aby třídy nebo struktury lze převést na nebo z jiné třídy nebo struktury nebo základní typy. Převody jsou definovány jako operátory a jsou pojmenovány pro typ, ke kterému převodu. Typ argumentu, který má být převeden nebo typ výsledku převodu, ale ne obojí, musí být nadřazeného typu.  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a>Přehled operátorů převodů  
 Operátory převodu mají následující vlastnosti:  
  
-   Převody deklarovány jako `implicit` automaticky provedou, když je povinný.  
  
-   Převody deklarovány jako `explicit` vyžaduje přetypování, která se má volat.  
  
-   Musí být všechny převody deklarovány jako `static`.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
-   [Použití operátorů převodu](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [Přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Postupy: Implementace uživatelem definovaných převodů mezi strukturami](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [static](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>Viz také

- <xref:System.Convert>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Zřetězit uživatelem definované explicitní převody v jazyce C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
