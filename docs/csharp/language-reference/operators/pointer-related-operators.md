---
title: Ukazatel související operators – C# odkaz
description: Další informace o C# operátory, které můžete použít při práci s ukazateli.
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
ms.openlocfilehash: 03d6ed19ef01be7712ff2fdde0c1be2a6673e64f
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401434"
---
# <a name="pointer-related-operators-c-reference"></a>Ukazatel související s operátory (C# odkaz)

Práce s ukazateli můžete použít následující operátory:

- Unární [ `&` (adresa of)](#address-of-operator-) operátor: při získávání adresy proměnné
- Unární [ `*` (dereferenci ukazatele)](#pointer-indirection-operator-) operátor: získání proměnné, na kterou odkazuje ukazatel
- [ `->` (Přístup ke členu)](#pointer-member-access-operator--) a [ `[]` (přístup k prvkům)](#pointer-element-access-operator-) operátory
- Aritmetické operátory [ `+`, `-`, `++`, a `--`](#pointer-arithmetic-operators)
- Operátory porovnání [ `==`, `!=`, `<`, `>`, `<=`, a `>=`](#pointer-comparison-operators)

Informace o typy ukazatelů, naleznete v tématu [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> Všechny operace s ukazateli vyžaduje [nebezpečné](../keywords/unsafe.md) kontextu. Kód, který obsahuje nebezpečné bloky musí být kompilována s [ `-unsafe` ](../compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.

## <a name="address-of-operator-"></a> Operátor address-of &amp;

Unární `&` operátor vrátí adresu svého operandu:

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

Operand `&` operator musí být pevná proměnná. *Oprava* proměnné jsou proměnné, které se nacházejí v umístění úložiště, které operace nemá vliv [systému uvolňování paměti](../../../standard/garbage-collection/index.md). V předchozím příkladu, místní proměnná `number` je pevná proměnná, protože se nachází v zásobníku. Proměnné, které se nacházejí v umístění úložiště, které mohou být ovlivněny systému uvolňování paměti (například přemístění) se nazývají *přesouvatelný* proměnné. Pole objektů a prvky pole jsou příkladem přesouvatelný proměnné. Pokud "Opravit" nebo "připnout", můžete získat adresu přesouvatelný proměnné s [oprava](../keywords/fixed-statement.md) příkazu. Získané adresa je platná jenom po dobu trvání `fixed` blok příkazů. Následující příklad ukazuje způsob použití `fixed` příkazu a `&` operátor:

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

Nelze získat adresu konstanta nebo hodnota.

Další informace o pevné a přesouvatelný proměnných najdete v tématu [Fixed a přesunutelný proměnné](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

Binární soubor `&` operátor výpočetní prostředí [logický operátor AND](boolean-logical-operators.md#logical-and-operator-) z operandů logická nebo [bitové logické AND](bitwise-and-shift-operators.md#logical-and-operator-) z operandů integrální.

## <a name="pointer-indirection-operator-"></a>Operátor dereference ukazatele *

Unární operátor dereference ukazatele `*` získá proměnné, na kterou operand ukazuje. Je také známý jako operátor zrušení odkazu. Operand `*` operator musí být typu ukazatele.

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

Nelze použít `*` operátoru ve výrazu typu `void*`.

Binární soubor `*` operátor výpočetní prostředí [produktu](arithmetic-operators.md#multiplication-operator-) z operandů číselná.

## <a name="pointer-member-access-operator--"></a>Operátor přístupu členů ukazatel ->

`->` Operátor kombinuje [dereferenci ukazatele](#pointer-indirection-operator-) a [přístup ke členu](member-access-operators.md#member-access-operator-). To znamená pokud `x` je ukazatel typu `T*` a `y` je přístupný člen `T`, výraz ve tvaru

```csharp
x->y
```

je ekvivalentem

```csharp
(*x).y
```

Následující příklad ukazuje použití `->` operátor:

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

Nelze použít `->` operátoru ve výrazu typu `void*`.

## <a name="pointer-element-access-operator-"></a>Operator []. přístup k elementu ukazatele

Pro výraz `p` typu ukazatel, ukazatel přístup k prvkům ve tvaru `p[n]` se vyhodnotí jako `*(p + n)`, kde `n` musí být implicitně převeditelný na typu `int`, `uint`, `long`, nebo `ulong`. Informace o chování `+` operátor s ukazateli, najdete v článku [sčítání a odčítání celočíselnou hodnotu na nebo z ukazatele na](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) oddílu.

Následující příklad ukazuje, jak přistupovat k prvkům pole pomocí ukazatele a `[]` operátor:

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

V příkladu se používá [ `stackalloc` operátor](stackalloc.md) přidělení bloku paměti na zásobníku.

> [!NOTE]
> Operátor přístupu k elementu ukazatel není celočíselných vyhledávat chyby.

Nemůžete použít `[]` pro přístup k prvkům ukazatel se výraz typu `void*`.

Můžete také použít `[]` operátor pro [pole přístup k elementu nebo indexeru](member-access-operators.md#indexer-operator-).

## <a name="pointer-arithmetic-operators"></a>Aritmetické operátory ukazatele

Můžete provádět následující aritmetických operací s ukazatele:

- Můžete přidávat nebo odebírat integrální hodnotu na nebo z ukazatele na
- Odečtení dvou ukazatelů
- Zvýšení nebo snížení ukazatel

Nelze provádět tyto operace s odkazy typu `void*`.

Informace o podporovaných aritmetických operací s číselnými typy najdete v tématu [aritmetické operátory](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Sčítání a odčítání celočíselnou hodnotu na nebo z ukazatele na

Ukazatele `p` typu `T*` a výraz `n` implicitně převést na typ `int`, `uint`, `long`, nebo `ulong`, sčítání a odčítání jsou definovány takto:

- Obě `p + n` a `n + p` výrazy vytvořit ukazatel typu `T*` , která je výsledkem sečtení `n * sizeof(T)` adresu uvedenou ve `p`.
- `p - n` Výraz vytvoří ukazatel typu `T*` , že výsledky daných `n * sizeof(T)` z adresy poskytnuté `p`.

[ `sizeof` Operátor](../keywords/sizeof.md) získá velikost typu v bajtech.

Následující příklad ukazuje použití `+` operátorem pomocí ukazatele:

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>Odečtení ukazatele

Pro dva ukazatele `p1` a `p2` typu `T*`, výraz `p1 - p2` tvoří rozdíl mezi adresami zadanými `p1` a `p2` dělený `sizeof(T)`. Typ výsledku je `long`. To znamená `p1 - p2` je vypočítán jako `((long)(p1) - (long)(p2)) / sizeof(T)`.

Následující příklad ukazuje odečtení ukazatele:

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>Ukazatel přírůstek a snížení

`++` Operátoru Inkrementace [přidá](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 operand ukazatel. `--` Operátor dekrementace [odečte](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 z jeho operand ukazatele.

Oba operátory jsou podporovány ve dvou formách: přípony (`p++` a `p--`) a předpony (`++p` a `--p`). Výsledek `p++` a `p--` je hodnota `p` *před* operaci. Výsledek `++p` a `--p` je hodnota `p` *po* operaci.

Následující příklad ukazuje chování operátory zvýšení přípony a předpony:

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>Operátory porovnání ukazatele

Můžete použít `==`, `!=`, `<`, `>`, `<=`, a `>=` operátory porovnání operandy libovolný typ ukazatele, včetně `void*`. Tyto operátory porovnávají adresy poskytnuté dva operandy, jako by byly celých čísel bez znaménka.

Informace o chování těchto operátorů pro operandy jiných typů, najdete v článku [operátory rovnosti](equality-operators.md) a [operátory porovnání](comparison-operators.md) článků.

## <a name="operator-precedence"></a>Priorita operátorů

Následující ukazatel seznamu objednávek související s operátory od nejvyšší priority k nejnižší:

- Zvýšení příponového operátora `x++` a dekrementace `x--` operátory a `->` a `[]` operátory
- Předponového `++x` a dekrementace `--x` operátory a `&` a `*` operátory
- Additive `+` a `-` operátory
- Porovnání `<`, `>`, `<=`, a `>=` operátory
- Rovnost `==` a `!=` operátory

Použít závorky, `()`, chcete-li změnit pořadí vyhodnocování stanovené prioritou operátorů.

Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ nejde přetížit ukazatel související s operátory `&`, `*`, `->`, a `[]`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Oprava a přesunutelný proměnné](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [Operátor address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [Dereferenci ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [Přístupu k členovi](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [Přístup k prvkům ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [Aritmetika ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [Ukazatel přírůstek a snížení](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [Porovnání ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [unsafe keyword](../keywords/unsafe.md)
- [klíčové slovo fixed](../keywords/fixed-statement.md)
- [stackalloc – operátor](stackalloc.md)
- [sizeof – operátor](../keywords/sizeof.md)
