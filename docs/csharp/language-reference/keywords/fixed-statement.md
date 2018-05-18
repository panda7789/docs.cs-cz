---
title: fixed – příkaz (Referenční dokumentace jazyka C#)
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: decf906efeebf1723b4c5d6f0c75ba57affe9a98
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="fixed-statement-c-reference"></a>fixed – příkaz (Referenční dokumentace jazyka C#)

`fixed` Příkaz zabrání přemístění mobilní proměnné uvolňování paměti. `fixed` Příkazu je povolená jenom v [unsafe](unsafe.md) kontextu. `Fixed` Můžete také použít k vytvoření [pevnou velikost vyrovnávací paměti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

`fixed` Příkaz nastaví ukazatel spravované proměnné a "PIN" tuto proměnnou během provádění příkazu. Ukazatelé na mobilní spravované proměnné jsou užitečné pouze v `fixed` kontextu. Bez `fixed` kontextu, uvolňování paměti by mohly přemístit proměnné nepředvídatelné. Kompilátor jazyka C# pouze umožňuje přiřadit ukazatel spravované proměnné v `fixed` příkaz.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Ukazatel lze inicializovat pomocí pole, řetězec, vyrovnávací paměti pevné velikosti nebo adresy proměnné. Následující příklad ukazuje použití proměnných adresy, pole a řetězce. Další informace o pevné velikosti vyrovnávací paměti najdete v tématu [pevnou velikost vyrovnávací paměti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

Od verze jazyka C# 7.3, `fixed` příkaz funguje na další typy nad rámec pole řetězce, vyrovnávací paměti pevné velikosti nebo nespravované proměnné. Žádný typ, který implementuje metodu s názvem `DangerousGetPinnableReference` lze připojit. `DangerousGetPinnableReference` Musí vrátit `ref` nespravovaný typ proměnné. Podívejte se na téma na [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md) Další informace. Typy .NET <xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadonlySpan%601?displayProperty=nameWithType> byla zavedená v rozhraní .NET 2.0 základní zkontrolujte pomocí tohoto vzoru a může být připnutý. To je ukázáno v následujícím příkladu:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Pokud vytvoříte typy, které by se měly podílet v tomto vzoru, přečtěte si téma <xref:System.Span%601.DangerousGetPinnableReference?displayProperty=nameWithType> příklad implementace vzoru.

Více ukazatele jde inicializovat na jeden příkaz Pokud jsou všechny stejného typu:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

K chybě při inicializaci ukazatele různých typů, jednoduše vnořit `fixed` příkazy, jak je znázorněno v následujícím příkladu.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Po spuštění kódu v příkazu, jsou všechny definovaného proměnné Odepnout a předmět pro uvolňování paměti. Proto neukazují na tyto proměnné mimo `fixed` příkaz. Proměnných deklarovaných v `fixed` příkaz jsou omezená na tento příkaz snadněji toto:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Ukazatele v inicializovat `fixed` příkazy jsou proměnné určené jen pro čtení. Pokud chcete upravit hodnota ukazatele s hodnotou, musí deklarovat druhý proměnné ukazatele a upravit. Proměnná definovaná v `fixed` nemůže být upravena příkaz:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


V režimu unsafe mohou přidělit paměť v zásobníku, kde se nevztahuje uvolňování paměti a proto nemusí být připojena. Další informace najdete v tématu [stackalloc](stackalloc.md).

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a>Specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

 [Referenční dokumentace jazyka C#](../index.md)  
 [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
 [Klíčová slova jazyka C#](index.md)  
 [unsafe](unsafe.md)  
 [Vyrovnávací paměti pevné velikosti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
