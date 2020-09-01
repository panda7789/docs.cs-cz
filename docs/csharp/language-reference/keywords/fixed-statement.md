---
description: fixed – příkaz – reference jazyka C#
title: fixed – příkaz – reference jazyka C#
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 05505916ab3837d2c433ec420d7928a8ee883fa8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139720"
---
# <a name="fixed-statement-c-reference"></a>fixed – příkaz (Referenční dokumentace jazyka C#)

`fixed`Příkaz brání systému uvolňování paměti v přemístění pohyblivé proměnné. `fixed`Příkaz je povolen pouze v [nezabezpečeném](unsafe.md) kontextu. Pomocí `fixed` klíčového slova můžete také vytvořit [vyrovnávací paměti pevné velikosti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

`fixed`Příkaz nastaví ukazatel na spravovanou proměnnou a "PIN" tuto proměnnou během provádění příkazu. Ukazatele na pohyblivé spravované proměnné jsou užitečné pouze v `fixed` kontextu. Bez `fixed` kontextu by uvolňování paměti mohlo přemístit proměnné nepředvídatelné. Kompilátor jazyka C# umožňuje pouze přiřadit ukazatel na spravovanou proměnnou v `fixed` příkazu.

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#1)]

Můžete inicializovat ukazatel pomocí pole, řetězce, vyrovnávací paměti pevné velikosti nebo adresy proměnné. Následující příklad ilustruje použití proměnných adres, polí a řetězců:

[!code-csharp[Initializing fixed size buffers](snippets/FixedKeywordExamples.cs#2)]

Počínaje jazykem C# 7,3 `fixed` příkaz funguje na dalších typech nad rámec polí, řetězců, vyrovnávací paměti pevné velikosti nebo nespravovaných proměnných. Libovolný typ, který implementuje metodu s názvem, `GetPinnableReference` lze připnout. `GetPinnableReference`Musí vracet `ref` proměnnou [nespravovaného typu](../builtin-types/unmanaged-types.md). Typy .NET <xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> zavedené v .net Core 2,0 využívají tento model a dají se připnout. To je znázorněno v následujícím příkladu:

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#FixedSpan)]

Pokud vytváříte typy, které by se měly účastnit tohoto modelu, přečtěte si <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> Příklad implementace vzoru.

V jednom příkazu lze inicializovat více ukazatelů, pokud jsou všechny stejného typu:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Chcete-li inicializovat ukazatele různých typů, jednoduše vnořovat `fixed` příkazy, jak je znázorněno v následujícím příkladu.

[!code-csharp[Initializing multiple pointers](snippets/FixedKeywordExamples.cs#3)]

Po spuštění kódu v příkazu nejsou připnuté žádné připnuté proměnné a podléhají uvolňování paměti. Proto neodkazujte na tyto proměnné mimo `fixed` příkaz. Proměnné deklarované v `fixed` příkazu jsou vymezeny na tento příkaz, což usnadňuje tyto akce:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Ukazatelé inicializovaný v `fixed` příkazech jsou proměnné jen pro čtení. Chcete-li změnit hodnotu ukazatele, je nutné deklarovat druhý ukazatel na proměnnou a upravit ji. Proměnná deklarovaná v `fixed` příkazu se nedá změnit:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Můžete přidělit paměť v zásobníku, kde nepodléhá uvolňování paměti, a proto není nutné ji připnout. K tomu použijte [ `stackalloc` výraz](../operators/stackalloc.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [fixed Statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [UNSAFE](unsafe.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Vyrovnávací paměti pevné velikosti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
