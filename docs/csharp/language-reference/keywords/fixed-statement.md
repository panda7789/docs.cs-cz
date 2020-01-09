---
title: Příkaz fixed – C# reference
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e527e8a54a739391d18b180532372b5b70f34d37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713525"
---
# <a name="fixed-statement-c-reference"></a>fixed – příkaz (Referenční dokumentace jazyka C#)

Příkaz `fixed` zabraňuje systému uvolňování paměti v přemístění pohyblivé proměnné. Příkaz je povolen pouze v nezabezpečeném kontextu. [nebezpečný](unsafe.md) `fixed` Pomocí klíčového slova `fixed` lze také vytvořit [vyrovnávací paměti pevné velikosti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

Příkaz `fixed` nastaví ukazatel na spravovanou proměnnou a "PIN" tuto proměnnou během provádění příkazu. Ukazatele na pohyblivé spravované proměnné jsou užitečné pouze v kontextu `fixed`. Bez kontextu `fixed`, uvolňování paměti může přemístit proměnné nepředvídatelné. C# Kompilátor umožňuje přiřadit ukazatel na spravovanou proměnnou v příkazu `fixed`.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Můžete inicializovat ukazatel pomocí pole, řetězce, vyrovnávací paměti pevné velikosti nebo adresy proměnné. Následující příklad ilustruje použití proměnných adres, polí a řetězců:

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

Počínaje C# 7,3 se příkaz `fixed` pracuje na dalších typech nad rámec polí, řetězců, vyrovnávací paměti pevné velikosti nebo nespravovaných proměnných. Libovolný typ, který implementuje metodu s názvem `GetPinnableReference` lze připnout. Musí vracet proměnnou nespravovaného [typu.](../builtin-types/unmanaged-types.md) `GetPinnableReference` `ref` Typy .NET <xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> představené v .NET Core 2,0 využívají tento model a dají se připnout. To je ukázáno v následujícím příkladu:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Pokud vytváříte typy, které by se měly účastnit tohoto modelu, přečtěte si téma <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> pro příklad implementace vzoru.

V jednom příkazu lze inicializovat více ukazatelů, pokud jsou všechny stejného typu:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Chcete-li inicializovat ukazatele různých typů, jednoduše vnořovat `fixed` příkazy, jak je znázorněno v následujícím příkladu.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Po spuštění kódu v příkazu nejsou připnuté žádné připnuté proměnné a podléhají uvolňování paměti. Proto neodkazujte na tyto proměnné mimo příkaz `fixed`. Proměnné deklarované v příkazu `fixed` jsou vymezeny na tento příkaz, což usnadňuje tyto akce:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Ukazatele inicializované v příkazech `fixed` jsou proměnné jen pro čtení. Chcete-li změnit hodnotu ukazatele, je nutné deklarovat druhý ukazatel na proměnnou a upravit ji. Proměnnou deklarovanou v příkazu `fixed` nelze změnit:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Můžete přidělit paměť v zásobníku, kde nepodléhá uvolňování paměti, a proto není nutné ji připnout. K tomu použijte [operátor`stackalloc`](../operators/stackalloc.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části s [příkazem fixed](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [unsafe](unsafe.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Vyrovnávací paměti pevné velikosti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
