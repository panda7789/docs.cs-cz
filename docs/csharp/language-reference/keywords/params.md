---
title: klíčové slovo params – C# referenční informace
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 90d224080f607cbac96514aaf5ac6d67affef9e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713232"
---
# <a name="params-c-reference"></a>params (Referenční dokumentace jazyka C#)

Pomocí klíčového slova `params` můžete zadat [parametr metody](method-parameters.md) , který přebírá proměnný počet argumentů.

Můžete odeslat čárkami oddělený seznam argumentů typu určeného v deklaraci parametru nebo pole argumentů zadaného typu. Nemůžete také odesílat žádné argumenty. Pokud neodešlete žádné argumenty, délka seznamu `params` je nula.

V deklaraci metody nejsou povoleny žádné další parametry za klíčovým slovem `params` a v deklaraci metody je povoleno pouze jedno klíčové slovo `params`.

Deklarovaný typ parametru `params` musí být jednorozměrné pole, jak ukazuje následující příklad. V opačném případě dojde k chybě kompilátoru [CS0225](../../misc/cs0225.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje různé způsoby, jak lze do parametru `params` odeslat argumenty.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Parametry metody](method-parameters.md)
