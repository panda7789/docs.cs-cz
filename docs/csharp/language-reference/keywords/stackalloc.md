---
title: stackalloc – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 61a27e777a1919a2a6fc5140a311835a8f3daba9
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480804"
---
# <a name="stackalloc-c-reference"></a>stackalloc (Referenční dokumentace jazyka C#)

`stackalloc` – Klíčové slovo se používá k přidělení bloku paměti na zásobníku.

```csharp
Span<int> block = stackalloc int[100];
```

Přiřazení přiděleného bloku k <xref:System.Span%601?displayName=nameWithType> místo `int*` umožňuje přidělení zásobníku v nouzovém bloku. `unsafe` Kontextu se nevyžaduje.

## <a name="remarks"></a>Poznámky

Klíčové slovo je platný jenom v místní proměnné inicializátory. Následující kód způsobí chyby kompilátoru.

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
Span<int> span;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
span = stackalloc int[100];
```

Od verze C# 7.3, můžete použít syntaxi inicializátoru pole pro `stackalloc` pole. Následující deklarace deklarovat pole s tři elementy, jejichž hodnoty jsou celá čísla `1`, `2`, a `3`. Druhý inicializace přiřadí paměti pro <xref:System.ReadOnlySpan%601>, označující, že je paměť nelze upravit.

```csharp
// Valid starting with C# 7.3
Span<int> first = stackalloc int[3] { 1, 2, 3 };
ReadOnlySpan<int> second = stackalloc int[] { 1, 2, 3 };
Span<int> third = stackalloc[] { 1, 2, 3 };
```

Pokud se jedná o typy ukazatelů, `stackalloc` vyžaduje [nebezpečné](unsafe.md) kontextu. Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).

`stackalloc` je třeba [_alloca](/cpp/c-runtime-library/reference/alloca) v knihovně C Runtime.

## <a name="examples"></a>Příklady

Následující příklad vypočítá a zobrazí prvních 20 čísla v pořadí Fibonacciho. Každé číslo je součtu předchozích dvou čísel. V kódu, blok paměti dostatečnou velikost tak, aby obsahovala 20 prvky typu `int` přidělené v zásobníku, není haldy. Adresu bloku je uložen v `Span` `fib`. Tuto paměť není předmětem pravidla kolekce paměti a proto nemusí být připnutá (s použitím [oprava](fixed-statement.md)). Životnost blok paměti je omezená na životnost metody, která ho definuje. Nelze uvolnit paměť, než metoda vrátí.

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

Následující příklad inicializuje `stackalloc` pole celých čísel bitová maska s jeden bit nastaven v jednotlivých prvcích. Tento příklad ukazuje novou syntaxi inicializátoru k dispozici od C# 7.3:

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>Zabezpečení

Měli byste použít <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601> Pokud je to možné, protože je méně bezpečné než bezpečné alternativy nezabezpečený kód. I v případě, že se používá s ukazateli, použití `stackalloc` automaticky povoluje funkce detekce přetečení vyrovnávací paměti v modulu common language runtime (CLR). Pokud se zjistí přetečení vyrovnávací paměti, co nejrychleji, chcete-li minimalizovat pravděpodobnost, že je proveden škodlivý kód ukončení procesu.

## <a name="c-language-specification"></a>specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Klíčová slova operátorů](operator-keywords.md)
- [Nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md)
