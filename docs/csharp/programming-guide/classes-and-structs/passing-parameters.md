---
title: Předávání parametrů – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 60ac7a8d982e7788f07debce114896859385c8e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705467"
---
# <a name="passing-parameters-c-programming-guide"></a>Předávání parametrů (Průvodce programováním v C#)
V c#, argumenty mohou být předány parametry buď hodnotou nebo odkazem. Předávání odkazem umožňuje členům funkce, metodám, vlastnostem, indexerům, operátorům a konstruktorům změnit hodnotu parametrů a mít tuto změnu v prostředí volání zachovat. Chcete-li předat parametr odkazem s úmyslem `ref`změnit `out` hodnotu, použijte klíčové slovo nebo klíčové slovo. Chcete-li předat odkaz s úmyslem vyhnout se kopírování, `in` ale nemění hodnotu, použijte modifikátor. Pro jednoduchost se v `ref` příkladech v tomto tématu používá pouze klíčové slovo. Další informace `in`o rozdílu `ref`mezi `out`, , a , viz [v](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)a [out](../../language-reference/keywords/out-parameter-modifier.md).  
  
 Následující příklad ilustruje rozdíl mezi parametry hodnoty a referenční parametry.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Další informace najdete v následujících tématech:  
  
- [Předávání parametrů typu hodnoty](./passing-value-type-parameters.md)  
  
- [Předávání parametrů typu odkazu](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v [tématu Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Metody](./methods.md)
