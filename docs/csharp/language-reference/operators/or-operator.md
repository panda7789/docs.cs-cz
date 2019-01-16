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
ms.openlocfilehash: 185ea3aabff4794ec08cca541773dbec3574ab4b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333509"
---
# <a name="-operator-c-reference"></a>| – operátor (C# odkaz)

Binární `|` pro integrální typy jsou předdefinované operátory a `bool`. Pro integrální typy `|` vypočítá bitový OR jeho operandu. Pro `bool` operandy, `|` vypočítá logický operátor OR operandů; to znamená, výsledek je `false` pouze v případě jsou oba operandy jeho `false`.

## <a name="remarks"></a>Poznámky

Binární soubor `|` operátor vyhodnotí oba operandy bez ohledu na to první hodnotu, oproti k [operátor podmíněného OR](conditional-or-operator.md) `||`.

Lze přetěžovat uživatelsky definované typy `|` – operátor (viz [operátor](../keywords/operator.md)).

## <a name="example"></a>Příklad

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C#operátory](index.md)