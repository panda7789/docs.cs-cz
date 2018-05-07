---
title: public (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: abf7219359c108108b1ce3a3fde3dc10f9a8732d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="public-c-reference"></a>public (Referenční dokumentace jazyka C#)
`public` – Klíčové slovo je – modifikátor přístupu pro různé typy a členy typu. Veřejný přístup je nejvíce projektovou úroveň přístupu. Neexistují žádná omezení na přístup k veřejné členy, jako v následujícím příkladu:  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 V tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) a [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md) Další informace.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou dvě třídy deklarované, `PointTest` a `MainClass`. Veřejné členy `x` a `y` z `PointTest` se k nim přistupuje přímo z `MainClass`.  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 Pokud změníte `public` úroveň přístupu k [privátní](../../../csharp/language-reference/keywords/private.md) nebo [chráněné](../../../csharp/language-reference/keywords/protected.md), zobrazí se chybová zpráva:  
  
 'PointTest.y' je nedostupná v důsledku úrovně ochrany.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
