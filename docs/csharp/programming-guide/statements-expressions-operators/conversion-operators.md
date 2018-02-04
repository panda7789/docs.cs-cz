---
title: "Operátory převodu (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 056971dcd648208d77573c180df28ffdd46788c5
ms.sourcegitcommit: 22a48b64a0150a60b00b4fc4d8c62cde7f1670c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2018
---
# <a name="conversion-operators-c-programming-guide"></a>Operátory převodu (Průvodce programováním v C#)
C# umožňuje programátorům deklarovat převody na třídy nebo struktury tak, aby třídy nebo struktury lze převést na nebo z jiných třídy nebo struktury nebo základní typy. Převody jsou definovány jako operátory a jsou název pro typ, do které převést. Obsahující typ musí být buď typ argumentu má být převeden, nebo typ výsledek převodu, ale ne obojí.  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a>Přehled operátorů převodů  
 Operátory převodu mít následující vlastnosti:  
  
-   Převody deklarován jako `implicit` automaticky provedou, když je požadováno.  
  
-   Převody deklarován jako `explicit` vyžadují přetypování, která se má volat.  
  
-   Všechny převody musí být deklarována jako `static`.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
-   [Použití operátorů převodu](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [Přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Postupy: Implementace uživatelem definovaných převodů mezi strukturami](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [static](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Convert>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Zřetězené uživatelem definované explicitní převody v jazyce C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
