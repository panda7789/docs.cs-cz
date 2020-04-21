---
title: klíčové slovo params pro pole parametrů - odkaz C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 77d7fd19ff57f80f401191027e2fae95026e1966
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738843"
---
# <a name="params-c-reference"></a>params (Referenční dokumentace jazyka C#)

Pomocí klíčového `params` slova můžete zadat [parametr metody,](method-parameters.md) který přebírá proměnný počet argumentů. Typ parametru musí být jednorozměrné pole.

Žádné další parametry jsou `params` povoleny po klíčové slovo `params` v deklaraci metody a pouze jedno klíčové slovo je povoleno v deklaraci metody.

Pokud deklarovaný `params` typ parametru není jednorozměrné pole, dojde k chybě kompilátoru [CS0225.](../../misc/cs0225.md)

Při volání metody s `params` parametrem můžete předat:

- Seznam argumentů oddělených čárkami typu prvků pole.
- Pole argumentů zadaného typu.
- Žádné argumenty. Pokud neodešlete žádné argumenty, bude délka `params` seznamu nulová.

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
