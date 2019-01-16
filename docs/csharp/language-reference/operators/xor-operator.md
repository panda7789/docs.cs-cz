---
title: ^ – operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 152be2d81d1bf340b839d74f169d63d7260f7ca5
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333704"
---
# <a name="-operator-c-reference"></a>^ – operátor (C# odkaz)

Binární `^` pro integrální typy jsou předdefinované operátory a `bool`. Pro integrální typy `^` vypočítá bitový exkluzivní operátor OR z operandů. Pro `bool` operandy, `^` vypočítá exkluzivní logické- nebo z operandů; to znamená, výsledek je `true` pouze v případě právě jeden z operandů je `true`.

## <a name="remarks"></a>Poznámky

Lze přetěžovat uživatelsky definované typy `^` – operátor (viz [operátor](../keywords/operator.md)). Operace interních typů jsou obecně povoleny na výčet.

## <a name="example"></a>Příklad

[!code-csharp[csRefOperators#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#30)]

Výpočet `0xf8 ^ 0x3f` v předchozím příkladu provádí logické bitové exkluzivní disjunkce OR následující dvě binárních hodnot, které odpovídají šestnáctkových hodnot F8 a 3F:

`1111 1000`

`0011 1111`

Výsledek exkluzivní disjunkce OR je `1100 0111`, který je kompatibilní s C7 v šestnáctkové soustavě.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C#operátory](index.md)
