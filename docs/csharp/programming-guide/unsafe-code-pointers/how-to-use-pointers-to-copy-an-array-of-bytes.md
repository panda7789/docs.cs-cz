---
title: 'Postupy: Použití ukazatelů ke kopírování pole bajtů - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: d174f51fa1709a70b98473a4dbbad89b9c62c22a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61708909"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Postupy: Použití ukazatelů ke kopírování pole bajtů (C# Průvodce programováním v)

Následující příklad používá ukazatelů ke kopírování bajtů z jednoho pole do jiného.

Tento příklad používá [unsafe](../../language-reference/keywords/unsafe.md) – klíčové slovo, které vám umožní použít ukazatele ve `Copy` metody. [Oprava](../../language-reference/keywords/fixed-statement.md) prohlášení se používá k deklaraci ukazatele na zdrojové a cílové pole. `fixed` Příkaz *PIN kódy* indexy pole zdrojové a cílové umístění v paměti, aby nebude možné přesunout uvolňováním paměti. Bloky paměti pro pole nepřipnuté, pokud `fixed` bloku je dokončena. Protože `Copy` metoda v tomto příkladu používá `unsafe` – klíčové slovo, se musí být kompilována s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.

V tomto příkladu přistupuje k prvky obou polí pomocí indexů spíše než druhý nespravovaného ukazatele. Deklarace `pSource` a `pTarget` připíná ukazatele pole. Tato funkce je dostupná, od C# 7.3.

## <a name="example"></a>Příklad

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Nebezpečný kód a ukazatele](index.md)
- [-unsafe (možnosti kompilátoru C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)
