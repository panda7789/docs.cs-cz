---
description: klíčové slovo params pro pole parametrů – reference jazyka C#
title: klíčové slovo params pro pole parametrů – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: a2726c725508cd297001aaabddeff414704d1115
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134468"
---
# <a name="params-c-reference"></a>params (Referenční dokumentace jazyka C#)

Pomocí `params` klíčového slova můžete zadat [parametr metody](method-parameters.md) , který přebírá proměnný počet argumentů. Typ parametru musí být jednorozměrné pole.

V deklaraci metody nejsou povoleny žádné další parametry za `params` klíčovým slovem a `params` v deklaraci metody je povoleno pouze jedno klíčové slovo.

Není-li deklarovaný typ `params` parametru jednorozměrné pole, dojde k chybě kompilátoru [CS0225](../../misc/cs0225.md) .

Při volání metody s `params` parametrem můžete předat:

- Čárkami oddělený seznam argumentů typu prvků pole.
- Pole argumentů zadaného typu.
- Žádné argumenty. Pokud neodešlete žádné argumenty, délka `params` seznamu je nula.

## <a name="example"></a>Příklad

Následující příklad ukazuje různé způsoby, jak lze argumenty odeslat do `params` parametru.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Parametry metody](method-parameters.md)
