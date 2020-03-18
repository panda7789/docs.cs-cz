---
title: opraven příkaz - C# Reference
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e527e8a54a739391d18b180532372b5b70f34d37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713525"
---
# <a name="fixed-statement-c-reference"></a>fixed – příkaz (Referenční dokumentace jazyka C#)

Příkaz `fixed` zabrání systému uvolňování paměti přemístit pohyblivou proměnnou. Příkaz `fixed` je povolen pouze v [nebezpečném](unsafe.md) kontextu. Klíčové `fixed` slovo můžete také použít k vytvoření [vyrovnávacích pamětí s pevnou velikostí](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

Příkaz `fixed` nastaví ukazatel na spravovanou proměnnou a "kolíky" tuto proměnnou během provádění příkazu. Ukazatele na pohyblivé spravované proměnné `fixed` jsou užitečné pouze v kontextu. Bez `fixed` kontextu uvolňování paměti může přemístit proměnné nepředvídatelně. Kompilátor Jazyka C# umožňuje pouze přiřadit ukazatel spravované `fixed` proměnné v příkazu.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Ukazatel můžete inicializovat pomocí pole, řetězce, vyrovnávací paměti s pevnou velikostí nebo adresy proměnné. Následující příklad ilustruje použití proměnných adres, polí a řetězců:

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

Počínaje C# 7.3, `fixed` příkaz pracuje na další typy mimo pole, řetězce, vyrovnávací paměti s pevnou velikostí nebo nespravované proměnné. Libovolný typ, který implementuje metodu s názvem `GetPinnableReference` lze připnout. Musí `GetPinnableReference` vrátit `ref` proměnnou [nespravovaného typu](../builtin-types/unmanaged-types.md). Typy <xref:System.Span%601?displayProperty=nameWithType> .NET <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> a zavedené v rozhraní .NET Core 2.0 využívají tento vzor a lze je připnout. To je znázorněno v následujícím příkladu:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Pokud vytváříte typy, které by se <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> měly účastnit tohoto vzoru, naleznete příklad implementace vzoru.

Více ukazatelů lze inicializovat v jednom příkazu, pokud jsou všechny stejného typu:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Chcete-li inicializovat ukazatele různých `fixed` typů, jednoduše vnořte příkazy, jak je znázorněno v následujícím příkladu.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Po spuštění kódu v příkazu jsou všechny připnuté proměnné odepnuty a podléhají uvolňování paměti. Proto neodkazují na tyto proměnné `fixed` mimo příkaz. Proměnné deklarované `fixed` v příkazu jsou vymezeny na toto prohlášení, což usnadňuje:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Ukazatele inicializované v `fixed` příkazech jsou proměnné jen pro čtení. Pokud chcete změnit hodnotu ukazatele, musíte deklarovat druhou proměnnou ukazatele a upravit ji. Proměnnou uvedenou `fixed` v výkazu nelze změnit:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Můžete přidělit paměť v zásobníku, kde není předmětem uvolňování paměti a proto není nutné připnout. Chcete-li, že pomocí [ `stackalloc` operátoru](../operators/stackalloc.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete [v části Pevný příkaz](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) specifikace jazyka [C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [unsafe](unsafe.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Vyrovnávací paměti s pevnou velikostí](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
