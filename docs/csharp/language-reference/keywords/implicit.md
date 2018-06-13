---
title: implicit (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 160d9f7c0d58abd685bf1d799b53cc96a26aebe8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215014"
---
# <a name="implicit-c-reference"></a>implicit (referenční dokumentace jazyka C#)
`implicit` – Klíčové slovo se používá k deklaraci operátor implicitní uživatelsky definovaný typ. převod. Můžete povolit implicitní převody mezi uživatelem definovaný typ a jiného typu, pokud převod záruku, že nechcete mít za následek ztrátu dat.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 Odstraněním nepotřebných přetypování implicitní převody zlepšit čitelnost zdrojového kódu. Ale protože implicitní převody nevyžadují programátorům explicitně přetypování z jednoho typu na druhý, musí dát pozor na zabránit neočekávané výsledky. Operátory implicitního převodu obecně by nikdy generování výjimek a nikdy dojít ke ztrátě informací, tak, aby bylo možné bezpečně bez vědomí pro programátory. Pokud operátor převodu nelze splňují tato kritéria, by měl být označen `explicit`. Další informace najdete v tématu [použití operátorů převodu](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)  
 [Operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md)  
 [Postupy: Implementace uživatelem definovaných převodů mezi strukturami](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
