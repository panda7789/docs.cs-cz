---
title: nezabezpečené – C# odkaz na klíčové slovo
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: ef98809eae0329c028dfb318c4a437aae4736db1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712985"
---
# <a name="unsafe-c-reference"></a>unsafe (Referenční dokumentace jazyka C#)

Klíčové slovo `unsafe` označuje nezabezpečený kontext, který je vyžadován pro všechny operace zahrnující ukazatele. Další informace naleznete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).

Můžete použít modifikátor `unsafe` v deklaraci typu nebo člena. Celý textový rozsah typu nebo členu je proto považován za nezabezpečený kontext. Například následující je metoda deklarovaná s modifikátorem `unsafe`:

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

Rozsah nebezpečného kontextu se rozšiřuje ze seznamu parametrů na konec metody, takže ukazatele lze použít také v seznamu parametrů:

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

Pomocí nebezpečného blokování můžete také povolit používání nebezpečného kódu uvnitř tohoto bloku. Příklad:

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Chcete-li zkompilovat nezabezpečený kód, je nutné zadat možnost kompilátoru [`-unsafe`](../compiler-options/unsafe-compiler-option.md) . Modul CLR (Common Language Runtime) neumožňuje ověřit nezabezpečený kód.

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v tématu [nezabezpečený kód](~/_csharplang/spec/unsafe-code.md) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [fixed – příkaz](fixed-statement.md)
- [Nebezpečný kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md)
- [Vyrovnávací paměti pevné velikosti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
