---
title: stackalloc (Referenční dokumentace jazyka C#)
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 5926550eea1f5a2f8fb74645f22ca54c2bed3136
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508577"
---
# <a name="stackalloc-c-reference"></a>stackalloc (Referenční dokumentace jazyka C#)
`stackalloc` – Klíčové slovo se používá v kontextu unsafe kódu k přidělení bloku paměti na zásobníku.

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a>Poznámky

Klíčové slovo je platný jenom v místní proměnné inicializátory. Následující kód způsobí chyby kompilátoru.

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

Od verze C# 7.3, můžete použít syntaxi inicializátoru pole pro `stackalloc` pole. Následující deklarace deklarovat pole s tři elementy, jejichž hodnoty jsou celá čísla `1`, `2`, a `3`:

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

Protože se jedná o typy ukazatelů, `stackalloc` vyžaduje [nebezpečné](unsafe.md) kontextu. Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md) 

`stackalloc` je třeba [_alloca](/cpp/c-runtime-library/reference/alloca) v knihovně C Runtime.

## <a name="examples"></a>Příklady

Následující příklad vypočítá a zobrazí prvních 20 čísla v pořadí Fibonacciho. Každé číslo je součtu předchozích dvou čísel. V kódu, blok paměti dostatečnou velikost tak, aby obsahovala 20 prvky typu `int` přidělené v zásobníku, není haldy. Adresu bloku je uloženou v ukazateli `fib`. Tuto paměť není předmětem pravidla kolekce paměti a proto nemusí být připnutá (s použitím [oprava](fixed-statement.md)). Životnost blok paměti je omezená na životnost metody, která ho definuje. Nelze uvolnit paměť, než metoda vrátí.

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

Následující příklad inicializuje `stackalloc` pole celých čísel bitová maska s jeden bit nastaven v jednotlivých prvcích. Tento příklad ukazuje novou syntaxi inicializátoru k dispozici od C# 7.3:

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>Zabezpečení

Nezabezpečený kód je méně bezpečné než bezpečné alternativy. Nicméně použití `stackalloc` automaticky povoluje funkce detekce přetečení vyrovnávací paměti v modulu common language runtime (CLR). Pokud se zjistí přetečení vyrovnávací paměti, co nejrychleji, chcete-li minimalizovat pravděpodobnost, že je proveden škodlivý kód ukončení procesu.

## <a name="c-language-specification"></a>Specifikace jazyka C#
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)  
- [Nebezpečný kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
