---
title: Operátory převodu - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: 927640b63773d24be93cc90427668f9568a39652
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362727"
---
# <a name="conversion-operators-c-programming-guide"></a>Operátory převodu (C# Programming Guide)

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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Convert>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Zřetězit uživatelem definované explicitní převody v jazyce C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
