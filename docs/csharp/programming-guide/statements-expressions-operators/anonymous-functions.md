---
title: Anonymní funkce – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 4d266584e1867a512e4b61e8839fe948aafb007f
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363925"
---
# <a name="anonymous-functions-c-programming-guide"></a>Anonymní funkce (C# Průvodce programováním)

Anonymní funkce je "vložený" příkaz nebo výraz, který lze použít všude, kde je očekáván typ delegáta. Můžete ji použít k inicializaci pojmenovaného delegáta nebo ho předat místo pojmenovaného typu delegáta jako parametr metody.

Můžete použít [výraz lambda](lambda-expressions.md) nebo [anonymní metodu](../../language-reference/operators/delegate-operator.md) pro vytvoření anonymní funkce. Doporučujeme použít výrazy lambda, protože poskytují výstižnější a výrazný způsob psaní vloženého kódu. Na rozdíl od anonymních metod lze některé typy výrazů lambda převést na typy stromu výrazů.

## <a name="the-evolution-of-delegates-in-c"></a>Vývoj delegátů v jazyce C\#

 V C# 1,0 jste vytvořili instanci delegáta explicitně inicializací s metodou, která byla definována jinde v kódu. C#2,0 představil koncept anonymních metod jako způsob zápisu nepojmenovaných bloků vložených příkazů, které mohou být provedeny při volání delegáta. C#3,0 zavedly lambda výrazy, které jsou podobné v konceptu anonymním metodám, ale častěji a stručnější. Tyto dvě funkce se společně nazývají *anonymní funkce*. Obecně platí, že aplikace, které cílí na verzi 3,5 a novější .NET Framework, by měly používat lambda výrazy.  
  
 Následující příklad ukazuje vývoj vytvoření delegáta z C# 1,0 na C# 3,0:  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Viz také:

- [Příkazy, výrazy a operátory](../../../csharp/programming-guide/statements-expressions-operators/index.md)
- [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)
- [Stromy výrazů (C#)](../concepts/expression-trees/index.md)
