---
title: Anonymní funkce – programovací průvodce C#
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: cfb0190ee263e65e8130a8925f76357a382eafa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711997"
---
# <a name="anonymous-functions-c-programming-guide"></a>Anonymní funkce (Průvodce programováním jazyka C#)

Anonymní funkce je "inline" příkaz nebo výraz, který lze použít všude tam, kde je očekáván typ delegáta. Můžete ji použít k inicializaci pojmenovaného delegáta nebo předat jej namísto pojmenovaného typu delegáta jako parametr metody.

K vytvoření anonymní funkce můžete použít [výraz lambda](lambda-expressions.md) nebo [anonymní metodu.](../../language-reference/operators/delegate-operator.md) Doporučujeme používat lambda výrazy, protože poskytují stručnější a expresivní způsob psaní vřádkového kódu. Na rozdíl od anonymních metod mohou být některé typy výrazů lambda převedeny na typy stromů výrazů.

## <a name="the-evolution-of-delegates-in-c"></a>Vývoj delegátů v C\#

 V C# 1.0 jste vytvořili instanci delegáta explicitně inicializovat s metodou, která byla definována jinde v kódu. C# 2.0 představil koncept anonymní metody jako způsob, jak psát nepojmenované bloky vřádlých prohlášení, které mohou být provedeny v vyvolání delegáta. C# 3.0 představil lambda výrazy, které jsou podobné v pojetí anonymní metody, ale výraznější a stručnější. Tyto dvě funkce jsou souhrnně *označovány*jako anonymní funkce . Obecně platí, že aplikace, které cílí na verzi 3.5 a novější rozhraní .NET Framework, by měly používat výrazy lambda.  
  
 Následující příklad ukazuje vývoj vytvoření delegáta z C# 1.0 do C# 3.0:  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Anonymní výrazy funkcí](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Viz také

- [Příkazy, výrazy a operátory](./index.md)
- [Lambda výrazy](./lambda-expressions.md)
- [Delegáty](../delegates/index.md)
- [Stromy výrazů (C#)](../concepts/expression-trees/index.md)
