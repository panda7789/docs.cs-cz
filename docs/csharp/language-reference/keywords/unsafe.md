---
title: unsafe – klíčové slovo (C# odkaz)
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 79cb246c4094f02d1319d28fcc94d0d3d5bd9cb5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128424"
---
# <a name="unsafe-c-reference"></a>unsafe (Referenční dokumentace jazyka C#)

`unsafe` – Klíčové slovo označuje nezabezpečený kontext, který se vyžaduje pro libovolnou operaci s ukazateli. Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).

Můžete použít `unsafe` modifikátor v deklaraci typu nebo člena. Textové celý rozsah tento typ nebo člen je proto považován za nezabezpečený kontext. Například tady je metody deklarované s `unsafe` modifikátor:

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

Obor nezabezpečeném kontextu rozšiřuje ze seznamu parametrů na konec metody, takže ukazatele lze také v seznamu parametrů:

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

Můžete také použít blok unsafe umožní použít nezabezpečený kód v tomto bloku. Příklad:

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Chcete-li zkompilovat nebezpečný kód, je nutné zadat [/ unsafe](../compiler-options/unsafe-compiler-option.md) – možnost kompilátoru. Nezabezpečený kód není možné ověřit modulem common language runtime.

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [nezabezpečený kód](~/_csharplang/spec/unsafe-code.md) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [fixed – příkaz](fixed-statement.md)
- [Nebezpečný kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md)
- [Vyrovnávací paměti pevné velikosti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)