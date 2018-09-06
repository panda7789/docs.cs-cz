---
title: 'Postupy: Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)'
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 061bbbc4557cb25d39edfb1f6235bb065a5de7bd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881392"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Postupy: Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)

Následující příklad používá ukazatelů ke kopírování bajtů z jednoho pole do jiného.

Tento příklad používá [unsafe](../../language-reference/keywords/unsafe.md) – klíčové slovo, které vám umožní použít ukazatele ve `Copy` metody. [Oprava](../../language-reference/keywords/fixed-statement.md) prohlášení se používá k deklaraci ukazatele na zdrojové a cílové pole. `fixed` Příkaz *PIN kódy* indexy pole zdrojové a cílové umístění v paměti, aby nebude možné přesunout uvolňováním paměti. Bloky paměti pro pole nepřipnuté, pokud `fixed` bloku je dokončena. Protože `Copy` metoda v tomto příkladu používá `unsafe` – klíčové slovo, se musí být kompilována s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.

V tomto příkladu přistupuje k prvky obou polí pomocí indexů spíše než druhý nespravovaného ukazatele. Deklarace `pSource` a `pTarget` připíná ukazatele pole. Tato funkce je dostupná, od C# 7.3.

## <a name="example"></a>Příklad

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../index.md)  
- [Nebezpečný kód a ukazatele](index.md)  
- [-unsafe (možnosti kompilátoru C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)  
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)  
