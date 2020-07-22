---
title: Předávání parametrů – Průvodce programováním v C#
description: Argument můžete předat parametru v jazyce C# podle hodnoty nebo odkazu. Změny argumentu předaného odkazem jsou trvalé. Použijte ref nebo out pro předání odkazem.
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 875a42aacf3d7aa4124684aefafdcb07ff4c87d6
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864732"
---
# <a name="passing-parameters-c-programming-guide"></a>Předávání parametrů (Průvodce programováním v C#)
V jazyce C# mohou být argumenty předány parametrům buď podle hodnoty, nebo podle odkazu. Předání odkazem umožňuje členům funkce, metodám, vlastnostem, indexerům, operátorům a konstruktorům změnit hodnotu parametrů a tuto změnu zachovat v volajícím prostředí. Chcete-li předat parametr odkazem s záměrem změnit hodnotu, použijte `ref` `out` klíčové slovo or. Chcete-li předat odkaz s záměrem vyhnout se kopírování, ale nikoli změně hodnoty, použijte `in` modifikátor. Pro jednoduchost se `ref` v příkladech v tomto tématu používá jenom klíčové slovo. Další informace o rozdílu mezi `in` , `ref` a naleznete `out` v části [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)a [out](../../language-reference/keywords/out-parameter-modifier.md).  
  
 Následující příklad znázorňuje rozdíl mezi parametry value a reference.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Další informace najdete v následujících tématech:  
  
- [Předávání parametrů typu hodnoty](./passing-value-type-parameters.md)  
  
- [Předávání parametrů typu odkazu](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [seznam argumentů](~/_csharplang/spec/expressions.md#argument-lists) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Metody](./methods.md)
