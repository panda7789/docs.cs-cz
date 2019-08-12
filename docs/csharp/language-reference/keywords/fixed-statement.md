---
title: Příkaz fixed – C# reference
ms.custom: seodec18
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: d3c87f0e71095bbcc7c5a1d64b026e92838a6306
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433757"
---
# <a name="fixed-statement-c-reference"></a>fixed – příkaz (Referenční dokumentace jazyka C#)

`fixed` Příkaz brání systému uvolňování paměti v přemístění pohyblivé proměnné. Příkaz je povolen pouze v nezabezpečeném kontextu. [nebezpečný](unsafe.md) `fixed` Pomocí `fixed` klíčového slova můžete také vytvořit [vyrovnávací paměti pevné velikosti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

`fixed` Příkaz nastaví ukazatel na spravovanou proměnnou a "PIN" tuto proměnnou během provádění příkazu. Ukazatele na pohyblivé spravované proměnné jsou užitečné pouze v `fixed` kontextu. `fixed` Bez kontextu by uvolňování paměti mohlo přemístit proměnné nepředvídatelné. C# Kompilátor umožňuje přiřadit ukazatel na spravovanou proměnnou v `fixed` příkazu.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Můžete inicializovat ukazatel pomocí pole, řetězce, vyrovnávací paměti pevné velikosti nebo adresy proměnné. Následující příklad ilustruje použití proměnných adres, polí a řetězců:

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

Počínaje C# 7,3, `fixed` příkaz funguje na dalších typech nad rámec polí, řetězců, vyrovnávací paměti pevné velikosti nebo nespravovaných proměnných. Libovolný typ, který implementuje metodu s `GetPinnableReference` názvem, lze připnout. Musí vracet proměnnou nespravovaného [typu.](../builtin-types/unmanaged-types.md) `GetPinnableReference` `ref` Typy <xref:System.Span%601?displayProperty=nameWithType> .NET a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> zavedené v .NET Core 2,0 využívají tento model a dají se připnout. To je ukázáno v následujícím příkladu:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Pokud vytváříte typy, které by se měly účastnit tohoto modelu, <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> Přečtěte si příklad implementace vzoru.

V jednom příkazu lze inicializovat více ukazatelů, pokud jsou všechny stejného typu:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Chcete-li inicializovat ukazatele různých typů, jednoduše vnořovat `fixed` příkazy, jak je znázorněno v následujícím příkladu.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

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

Můžete přidělit paměť v zásobníku, kde nepodléhá uvolňování paměti, a proto není nutné ji připnout. K tomu použijte [ `stackalloc` operátor](../operators/stackalloc.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části s [příkazem fixed](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [unsafe](unsafe.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Vyrovnávací paměti pevné velikosti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
