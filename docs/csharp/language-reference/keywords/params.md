---
title: klíčové slovo params (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 089e31f3aad12c2303619e2a1998d0d6a5a0ad86
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028358"
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