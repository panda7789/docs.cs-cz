---
title: '| Operator - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 38f8e21dbd07868441e0c4fbb6074f9897905222
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312875"
---
# <a name="-operator-c-reference"></a>| – operátor (C# odkaz)

Binární `|` pro integrální typy jsou předdefinované operátory a `bool`. Pro integrální typy `|` vypočítá bitový OR jeho operandu. Pro `bool` operandy, `|` vypočítá logický operátor OR operandů; to znamená, výsledek je `false` pouze v případě jsou oba operandy jeho `false`.

## <a name="remarks"></a>Poznámky

Binární soubor `|` operátor vyhodnotí oba operandy bez ohledu na to první hodnotu, oproti k [operátor podmíněného OR](boolean-logical-operators.md#conditional-logical-or-operator-) `||`.

Lze přetěžovat uživatelsky definované typy `|` – operátor (viz [operátor](../keywords/operator.md)).

## <a name="example"></a>Příklad

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)