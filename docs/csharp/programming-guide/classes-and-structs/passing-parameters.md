---
title: Předávání parametrů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: a1ccfff8081d101eee46360009653b0591dfb3ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="passing-parameters-c-programming-guide"></a>Předávání parametrů (Průvodce programováním v C#)
V jazyce C# argumenty můžete předat parametry hodnotou nebo odkazem. Předání odkazem umožňuje funkce členy, metody, vlastnosti, indexery, operátory a konstruktory změna hodnoty parametrů a tato změna uchování v volání prostředí. Chcete-li předat parametr odkazem se záměrem změna hodnoty, použijte `ref`, nebo `out` – klíčové slovo. Chcete-li předat odkazem se záměrem vyhnout kopírování, ale není změna hodnoty, použijte `in` modifikátor. Pro jednoduchost, jenom `ref` – klíčové slovo se používá v příkladech v tomto tématu. Další informace o rozdílu mezi `in`, `ref`, a `out`, najdete v části [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), a [ Předávání polí pomocí parametrů ref a out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Následující příklad ukazuje rozdíl mezi parametry hodnoty a odkazu.  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 Další informace naleznete v následujících tématech:  
  
-   [Předávání parametrů typu hodnoty](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [Předávání parametrů typu odkazu](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
