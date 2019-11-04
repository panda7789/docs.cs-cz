---
title: Předávání parametrů – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 22f58bda5aa5b60248902a4130f3ea9b6caa65cf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419128"
---
# <a name="passing-parameters-c-programming-guide"></a>Předávání parametrů (Průvodce programováním v C#)
V C#nástroji mohou být argumenty předány parametrům buď podle hodnoty, nebo podle odkazu. Předání odkazem umožňuje členům funkce, metodám, vlastnostem, indexerům, operátorům a konstruktorům změnit hodnotu parametrů a tuto změnu zachovat v volajícím prostředí. Chcete-li předat parametr odkazem s záměrem změnit hodnotu, použijte klíčové slovo `ref`nebo `out`. Chcete-li předat odkaz s záměrem vyhnout se kopírování, ale nezměnění hodnoty, použijte modifikátor `in`. V případě jednoduchosti se v příkladech v tomto tématu používá pouze klíčové slovo `ref`. Další informace o rozdílu mezi `in`, `ref`a `out`naleznete [v tématech in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)a [out](../../language-reference/keywords/out-parameter-modifier.md).  
  
 Následující příklad znázorňuje rozdíl mezi parametry value a reference.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Další informace naleznete v následujících tématech:  
  
- [Předávání parametrů typu hodnoty](./passing-value-type-parameters.md)  
  
- [Předávání parametrů typu odkazu](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [seznam argumentů](~/_csharplang/spec/expressions.md#argument-lists) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Metody](./methods.md)
