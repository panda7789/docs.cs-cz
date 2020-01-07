---
title: Použití ukazatelů ke kopírování pole průvodce C# programováním bajtů
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 2673b5a7b87e90618c3a8e579e34e7c7e80efa81
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634999"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Použití ukazatelů ke kopírování pole bajtů (C# Průvodce programováním)

Následující příklad používá ukazatele ke kopírování bajtů z jednoho pole do jiného.

V tomto příkladu se používá klíčové slovo [unsafe](../../language-reference/keywords/unsafe.md) , které umožňuje použití ukazatelů v metodě `Copy`. Příkaz [fixed](../../language-reference/keywords/fixed-statement.md) slouží k deklaraci ukazatelů na zdrojová a cílová pole. *Příkaz `fixed`* přiřadí umístění zdrojových a cílových polí v paměti tak, aby se nepřesunuly pomocí uvolňování paměti. Bloky paměti pro pole jsou po dokončení bloku `fixed` nepřipnutý. Vzhledem k tomu, že metoda `Copy` v tomto příkladu používá klíčové slovo `unsafe`, musí být kompilována s možností kompilátoru [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) .

Tento příklad přistupuje k prvkům obou polí pomocí indexů místo druhého nespravovaného ukazatele. Deklarace `pSource` a ukazatelů `pTarget` přiřadí pole. Tato funkce je k dispozici C# od 7,3.

## <a name="example"></a>Příklad

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Nebezpečný kód a ukazatele](index.md)
- [-UNSAFEC# (možnosti kompilátoru)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)
