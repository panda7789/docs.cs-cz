---
title: Operátory související s ukazateli – C# reference
description: Přečtěte C# si o operátorech, které můžete použít při práci s ukazateli.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 51e6aeda7699d9e2fe3c46ced93e1783a52e6743
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238959"
---
# <a name="pointer-related-operators-c-reference"></a>Operátory související s ukazateli (C# referenční)

Pro práci s ukazateli můžete použít následující operátory:

- Unární [`&` operátor (Address-of)](#address-of-operator-) : pro získání adresy proměnné
- Unární [`*` operátor (dereference ukazatele)](#pointer-indirection-operator-) : pro získání proměnné, na kterou odkazuje ukazatel
- Operátory [`->` (přístup do členů)](#pointer-member-access-operator--) a [`[]` (přístup k prvkům)](#pointer-element-access-operator-)
- Aritmetické operátory [`+`, `-`, `++`a `--`](#pointer-arithmetic-operators)
- Operátory porovnání [`==`, `!=`, `<`, `>`, `<=`a `>=`](#pointer-comparison-operators)

Informace o typech ukazatelů naleznete v tématu [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> Jakákoli operace s ukazateli vyžaduje [nezabezpečený](../keywords/unsafe.md) kontext. Kód, který obsahuje nebezpečné bloky, musí být kompilován s možností kompilátoru [`-unsafe`](../compiler-options/unsafe-compiler-option.md) .

## <a name="address-of-operator-"></a>&amp; operátoru adresy

Unární operátor `&` vrátí adresu svého operandu:

[!code-csharp[address of local](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

Operandem operátoru `&` musí být pevná proměnná. *Pevné* proměnné jsou proměnné, které jsou umístěny v umístěních úložiště, která nejsou ovlivněna operací [uvolňování paměti](../../../standard/garbage-collection/index.md). V předchozím příkladu je místní proměnná `number` pevnou proměnnou, protože se nachází v zásobníku. Proměnné, které jsou umístěné v umístění úložiště, které může být ovlivněno systémem uvolňování paměti (například přemístěné), se nazývají *pohyblivé* proměnné. V příkladech pohyblivých proměnných jsou pole objektů a prvky pole. Adresu pohyblivé proměnné můžete získat, pokud "opravíte" nebo "PIN" a pomocí [příkazu`fixed`](../keywords/fixed-statement.md). Získaná adresa je platná pouze uvnitř bloku příkazu `fixed`. Následující příklad ukazuje, jak použít příkaz `fixed` a operátor `&`:

[!code-csharp[address of fixed](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

Nemůžete získat adresu konstanty nebo hodnoty.

Další informace o pevných a pohyblivých proměnných naleznete v části [pevné a mobilní](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) proměnné [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

Operátor binárního `&` vypočítá [logický a](boolean-logical-operators.md#logical-and-operator-) jeho logický operandy nebo [bitovou logickou hodnotu a](bitwise-and-shift-operators.md#logical-and-operator-) její celočíselné operandy.

## <a name="pointer-indirection-operator-"></a>Operátor dereference ukazatele *

Operátor dereference unárního ukazatele `*` získá proměnnou, ke které má svůj operand ukazatel. Označuje se také jako operátor odkázání. Operand operátoru `*` musí být typu ukazatele.

[!code-csharp[pointer indirection](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

Operátor `*` nelze použít na výraz typu `void*`.

Operátor binárního `*` vypočítá [součin](arithmetic-operators.md#multiplication-operator-) svých číselných operandů.

## <a name="pointer-member-access-operator--"></a>Operátor přístupu členů ukazatele->

Operátor `->` kombinuje [nepřímý odkaz na ukazatel](#pointer-indirection-operator-) a [přístup ke členu](member-access-operators.md#member-access-operator-). To znamená, že pokud je `x` ukazatelem typu `T*` a `y` je přístupný člen typu `T`, výraz formuláře

```csharp
x->y
```

je ekvivalentem

```csharp
(*x).y
```

Následující příklad ukazuje použití operátoru `->`:

[!code-csharp[pointer member access](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

Operátor `->` nelze použít na výraz typu `void*`.

## <a name="pointer-element-access-operator-"></a>Operátor přístupu k elementu ukazatele []

Pro výraz `p` typu ukazatele je přístup k prvku `p[n]` formuláře vyhodnocen jako `*(p + n)`, kde `n` musí být typu implicitně převoditelná na `int`, `uint`, `long`nebo `ulong`. Informace o chování operátoru `+` s ukazateli naleznete v části [sčítání nebo odčítání celočíselné hodnoty nebo z ukazatele na ukazatel](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) .

Následující příklad ukazuje, jak přistupovat k prvkům pole s ukazatelem a operátorem `[]`:

[!code-csharp[pointer element access](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

V příkladu se pomocí [operátoru`stackalloc`](stackalloc.md) přidělí blok paměti v zásobníku.

> [!NOTE]
> Operátor přístupu elementu ukazatele nekontroluje chyby mimo hranice.

`[]` nelze použít pro přístup k prvku ukazatele s výrazem typu `void*`.

Můžete také použít operátor `[]` pro [prvek pole nebo přístup indexeru](member-access-operators.md#indexer-operator-).

## <a name="pointer-arithmetic-operators"></a>Aritmetické operátory ukazatele

S ukazateli můžete provádět následující aritmetické operace:

- Přidat nebo odečíst celočíselnou hodnotu do nebo z ukazatele
- Odečíst dva ukazatele
- Zvýšení nebo snížení ukazatele

Tyto operace nelze provést s ukazateli typu `void*`.

Informace o podporovaných aritmetických operacích s číselnými typy naleznete v tématu [aritmetické operátory](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Sčítání nebo odečítání celočíselné hodnoty do nebo z ukazatele

Pro ukazatel `p` typu `T*` a výraz `n` pro typ implicitně převoditelný na `int`, `uint`, `long`nebo `ulong`, sčítání a odčítání jsou definovány takto:

- `p + n` i `n + p` výrazy vytvoří ukazatel typu `T*`, který je výsledkem přidání `n * sizeof(T)` na adresu danou `p`.
- Výraz `p - n` vytvoří ukazatel typu `T*`, který je výsledkem odečtení `n * sizeof(T)` od adresy zadané `p`.

[Operátor`sizeof`](sizeof.md) získá velikost typu v bajtech.

Následující příklad ukazuje použití operátoru `+` s ukazatelem:

[!code-csharp[pointer addition](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>Odečtení ukazatele

Pro dva ukazatele `p1` a `p2` typu `T*``p1 - p2` výraz vygeneruje rozdíl mezi adresami daným `p1` a `p2` dělenou `sizeof(T)`. Typ výsledku je `long`. To znamená, že `p1 - p2` je vypočítávána jako `((long)(p1) - (long)(p2)) / sizeof(T)`.

Následující příklad ukazuje odčítání ukazatele:

[!code-csharp[pointer subtraction](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>Zvýšení a snížení ukazatele

Operátor přírůstku `++` [přidá](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 k operandu ukazatele. Operátor snížení `--` [odečte](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 od jeho operandu ukazatele.

Oba operátory jsou podporovány ve dvou formulářích: přípona (`p++` a `p--`) a předpona (`++p` a `--p`). Výsledek `p++` a `p--` je hodnota `p` *před* operací. Výsledkem `++p` a `--p` je hodnota `p` *po* operaci.

Následující příklad demonstruje chování obou operátorů přípony i prefixu:

[!code-csharp[pointer increment](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>Operátory porovnání ukazatelů

Operátory `==`, `!=`, `<`, `>`, `<=`a `>=` lze použít k porovnání operandů libovolného typu ukazatele, včetně `void*`. Tyto operátory porovnávají adresy zadané dvěma operandy, jako by šlo o celá čísla bez znaménka.

Informace o chování těchto operátorů pro operandy jiných typů naleznete v článcích [operátory rovnosti](equality-operators.md) a [operátory porovnání](comparison-operators.md) .

## <a name="operator-precedence"></a>Priorita operátorů

Následující seznam uvádí operátory související s ukazateli počínaje od nejvyšší priority k nejnižší:

- Přírůstek přípony `x++` a snížení `x--`ch operátorů a operátorů `->` a `[]`
- Zvýšení prefixu `++x` a snížení `--x` operátorů a operátorů `&` a `*`
- Aditivní `+` a `-` operátory
- Operátory `<`, `>`, `<=`a `>=` pro porovnání
- Operátory rovnosti `==` a `!=`

Pomocí závorek, `()`můžete změnit pořadí vyhodnocování stanovené předností operátorů.

Úplný seznam C# operátorů seřazených podle priority najdete v části [Priorita operátorů](index.md#operator-precedence) [ C# v článku věnovaném operátorům](index.md) .

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ nemůže přetížit operátory související s ukazatelem `&`, `*`, `->`a `[]`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Pevné a mobilní proměnné](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [Operátor address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [Indirekce ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [Přístup ke členu ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [Přístup k prvku ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [Aritmetický ukazatel](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [Zvýšení a snížení ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [Porovnání ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>Viz také

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [UNSAFE – klíčové slovo](../keywords/unsafe.md)
- [klíčové slovo fixed](../keywords/fixed-statement.md)
- [stackalloc – operátor](stackalloc.md)
- [sizeof – operátor](sizeof.md)
