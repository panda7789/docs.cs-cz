---
title: klíčové slovo params - C# Reference
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: f462ccc2421fef3ea111d263ec035a701cf04775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173546"
---
# <a name="params-c-reference"></a>params (Referenční dokumentace jazyka C#)

Pomocí klíčového `params` slova můžete zadat [parametr metody,](method-parameters.md) který přebírá proměnný počet argumentů.

Můžete odeslat seznam argumentů oddělených čárkami typu zadaného v deklaraci parametru nebo pole argumentů zadaného typu. Můžete také odeslat žádné argumenty. Pokud neodešlete žádné argumenty, bude délka `params` seznamu nulová.

Žádné další parametry jsou `params` povoleny po klíčové slovo `params` v deklaraci metody a pouze jedno klíčové slovo je povoleno v deklaraci metody.

Deklarovaný `params` typ parametru musí být jednorozměrné pole, jak ukazuje následující příklad. V opačném případě dojde k chybě kompilátoru [CS0225.](../../misc/cs0225.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje různé způsoby, ve kterém `params` mohou být argumenty odeslány do parametru.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Parametry metody](method-parameters.md)
