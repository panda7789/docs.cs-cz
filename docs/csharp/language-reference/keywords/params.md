---
title: klíčové slovo params – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: dd9699eb50f7dffc7c2f4976a79afbf689ba2470
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235839"
---
# <a name="params-c-reference"></a>params (Referenční dokumentace jazyka C#)

S použitím `params` – klíčové slovo, můžete zadat [parametr metody](method-parameters.md) , která přijímá proměnný počet argumentů.

Můžete odeslat čárkami oddělený seznam argumentů typ zadaný v deklaraci parametru nebo pole argumentů zadaného typu. Můžete také odeslat žádné argumenty. Pokud odešlete bez argumentů, délka `params` seznamu je nula.

Žádné další parametry nejsou povoleny po `params` – klíčové slovo v deklaraci metody a pouze jeden `params` – klíčové slovo je povolený v deklaraci metody.

Deklarovaný typ `params` parametr musí být jednorozměrné pole, jak ukazuje následující příklad. V opačném případě chybu kompilátoru [CS0225](../../misc/cs0225.md) vyvolá.

## <a name="example"></a>Příklad

Následující příklad ukazuje různé způsoby, jimiž lze argumenty odesílat do `params` parametru.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Parametry metody](method-parameters.md)