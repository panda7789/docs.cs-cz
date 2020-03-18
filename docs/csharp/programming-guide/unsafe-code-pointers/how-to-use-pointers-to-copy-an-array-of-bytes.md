---
title: Použití ukazatelů ke zkopírování pole bajtů – Programovací příručka jazyka C#
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698453"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Použití ukazatelů ke zkopírování pole bajtů (Průvodce programováním jazyka C#)

Následující příklad používá ukazatele ke kopírování bajtů z jednoho pole do druhého.

Tento příklad používá klíčové slovo [nebezpečné,](../../language-reference/keywords/unsafe.md) které umožňuje `Copy` použít ukazatele v metodě. Příkaz [fixed](../../language-reference/keywords/fixed-statement.md) se používá k deklarování ukazatelů na zdrojová a cílová pole. Příkaz `fixed` *připne* umístění zdrojového a cílového pole v paměti, aby nebyla přesunuta systémem uvolňování paměti. Bloky paměti pro pole jsou po dokončení `fixed` bloku odepnuty. Vzhledem `Copy` k tomu, `unsafe` že metoda v tomto příkladu používá klíčové slovo, musí být zkompilován s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilátoru možnost.

Tento příklad přistupuje k prvkům obou polí pomocí indexů, nikoli druhého nespravovaného ukazatele. Deklarace `pSource` a `pTarget` ukazatele připne pole. Tato funkce je k dispozici počínaje C# 7.3.

## <a name="example"></a>Příklad

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Nebezpečný kód a ukazatele](index.md)
- [-unsafe (Možnosti kompilátoru Jazyka C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Kolekce paměti](../../../standard/garbage-collection/index.md)
