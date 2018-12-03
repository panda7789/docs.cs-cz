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
ms.openlocfilehash: 241beb56b0e0f00dae63e12ea775b2b982200efc
ms.sourcegitcommit: 82a3f7882bc03ed733af91fc2a0b113195bf5dc7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2018
ms.locfileid: "44194848"
---
# <a name="passing-parameters-c-programming-guide"></a>Předávání parametrů (Průvodce programováním v C#)
V jazyce C# argumenty lze předat parametry podle hodnoty nebo odkazu. Předávání odkazem umožňuje funkce členy, metody, vlastnosti, indexery, operátory a konstruktory měnit hodnoty parametrů a jste tuto změnu uchování v volajícího prostředí. Chcete-li předat parametr odkazem s cílem změnit hodnotu, použijte `ref`, nebo `out` – klíčové slovo. Předávání pomocí odkazu s cílem vyhnout kopírování, ale nemění hodnoty, použijte `in` modifikátor. Pro jednoduchost, pouze `ref` – klíčové slovo se používá v příkladech v tomto tématu. Další informace o rozdílech mezi `in`, `ref`, a `out`, naleznete v tématu [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), a [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md).  
  
 Následující příklad ukazuje rozdíl mezi hodnotou a odkaz na parametry.  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 Další informace naleznete v následujících tématech:  
  
-   [Předávání parametrů typu hodnoty](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [Předávání parametrů typu odkazu](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [seznamy argumentů](~/_csharplang/spec/expressions.md#argument-lists) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
