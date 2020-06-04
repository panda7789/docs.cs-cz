---
title: Použití ukazatelů ke kopírování pole bajtů – Průvodce programováním v C#
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 8c1afc06fb567a923d604ad53dc26f94178a8d60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397412"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)

Následující příklad používá ukazatele ke kopírování bajtů z jednoho pole do jiného.

V tomto příkladu se používá klíčové slovo [unsafe](../../language-reference/keywords/unsafe.md) , které umožňuje použití ukazatelů v `Copy` metodě. Příkaz [fixed](../../language-reference/keywords/fixed-statement.md) slouží k deklaraci ukazatelů na zdrojová a cílová pole. Příkaz přiřadí `fixed` umístění zdrojových a cílových polí v paměti tak, aby se nepřesunuly pomocí uvolňování paměti. *pins* Bloky paměti pro pole jsou po `fixed` dokončení bloku odpojeny. Vzhledem k tomu `Copy` , že metoda v tomto příkladu používá `unsafe` klíčové slovo, musí být zkompilována s možností [– nezabezpečený](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilátor.

Tento příklad přistupuje k prvkům obou polí pomocí indexů místo druhého nespravovaného ukazatele. Deklarace `pSource` a `pTarget` odkazuje na pole. Tato funkce je k dispozici od jazyka C# 7,3.

## <a name="example"></a>Příklad

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Nezabezpečený kód a ukazatele](index.md)
- [-unsafe (možnosti kompilátoru C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)
