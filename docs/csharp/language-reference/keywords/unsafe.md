---
title: nebezpečné klíčové slovo - C# Reference
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: ef98809eae0329c028dfb318c4a437aae4736db1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712985"
---
# <a name="unsafe-c-reference"></a>unsafe (Referenční dokumentace jazyka C#)

Klíčové `unsafe` slovo označuje nebezpečný kontext, který je vyžadován pro všechny operace zahrnující ukazatele. Další informace naleznete [v tématu Nebezpečný kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).

`unsafe` Modifikátor můžete použít v deklaraci typu nebo člena. Celý textový rozsah typu nebo člena je proto považován za nebezpečný kontext. Například následující je metoda deklarovaná modifikátorem: `unsafe`

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

Rozsah nebezpečného kontextu sahá od seznamu parametrů až po konec metody, takže ukazatele lze také použít v seznamu parametrů:

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

Můžete také použít nebezpečný blok k povolení použití nebezpečného kódu uvnitř tohoto bloku. Například:

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Chcete-li zkompilovat [`-unsafe`](../compiler-options/unsafe-compiler-option.md) nebezpečný kód, musíte zadat možnost kompilátoru. Nebezpečný kód není ověřitelný běžným jazykem runtime.

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>specifikace jazyka C#

For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [fixed – příkaz](fixed-statement.md)
- [Nebezpečný kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md)
- [Vyrovnávací paměti s pevnou velikostí](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
