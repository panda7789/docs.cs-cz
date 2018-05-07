---
title: 'Postupy: Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)'
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 800a600f0fa7ca52d0433c8d90039434bf6b7f19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Postupy: Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)

Následující příklad používá ukazatele kopírování bajtů z jednoho pole do jiné.

Tento příklad používá [unsafe](../../language-reference/keywords/unsafe.md) – klíčové slovo, které vám umožní použít ukazatele v `Copy` metoda. [Pevné](../../language-reference/keywords/fixed-statement.md) příkaz se používá k deklaraci ukazatele na zdrojové a cílové pole. `fixed` Příkaz *PIN* umístění zdrojové a cílové maticových v paměti, aby nebude možné přesunout podle uvolňování paměti. Bloky paměti pro pole jsou Odepnout, kdy `fixed` blok dokončení. Protože `Copy` metoda v tomto příkladu používá `unsafe` – klíčové slovo, se musí být zkompilovány s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.

Tento příklad používá elementy obou polí pomocí indexů spíše než druhý nespravovaný ukazatel. Prohlášení o `pSource` a `pTarget` ukazatele PIN kódy pole. Tato funkce je k dispozici počínaje 7.3 C#.

## <a name="example"></a>Příklad

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Viz také
 [Průvodce programováním v jazyce C#](../index.md)  
 [Nebezpečný kód a ukazatele](index.md)  
 [-unsafe (možnosti kompilátoru C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)  
 [Uvolňování paměti](../../../standard/garbage-collection/index.md)  
