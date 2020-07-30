---
title: Použití ukazatelů ke kopírování pole bajtů – Průvodce programováním v C#
description: Naučte se používat ukazatele na kopírování pole bajtů. Podívejte se na příklad kódu a další dostupné prostředky.
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 70ab1441d25ea69afb2244bd94bd404a3e32838d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381785"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)

Následující příklad používá ukazatele ke kopírování bajtů z jednoho pole do jiného.

V tomto příkladu se používá klíčové slovo [unsafe](../../language-reference/keywords/unsafe.md) , které umožňuje použití ukazatelů v `Copy` metodě. Příkaz [fixed](../../language-reference/keywords/fixed-statement.md) slouží k deklaraci ukazatelů na zdrojová a cílová pole. Příkaz přiřadí `fixed` umístění zdrojových a cílových polí v paměti tak, aby se nepřesunuly pomocí uvolňování paměti. *pins* Bloky paměti pro pole jsou po `fixed` dokončení bloku odpojeny. Vzhledem k tomu `Copy` , že metoda v tomto příkladu používá `unsafe` klíčové slovo, musí být zkompilována s možností [– nezabezpečený](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilátor.

Tento příklad přistupuje k prvkům obou polí pomocí indexů místo druhého nespravovaného ukazatele. Deklarace `pSource` a `pTarget` odkazuje na pole. Tato funkce je k dispozici od jazyka C# 7,3.

## <a name="example"></a>Příklad

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Nezabezpečený kód a ukazatele](index.md)
- [-unsafe (možnosti kompilátoru C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)
