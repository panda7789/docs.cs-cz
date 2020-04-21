---
title: Operátory související s ukazatelem – odkaz jazyka C#
description: Další informace o operátory Jazyka C#, které můžete použít při práci s ukazateli.
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
ms.openlocfilehash: 7eb6666d10c44c342f69c7cfc763feb1b7b98c9d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738606"
---
# <a name="pointer-related-operators-c-reference"></a>Operátory související s ukazatelem (odkaz C#

Pro práci s ukazateli můžete použít následující operátory:

- Unární [ `&` (adresa- of)](#address-of-operator-) operátor: získat adresu proměnné
- Unární [ `*` (směrový bod)](#pointer-indirection-operator-) operátor: chcete-li získat proměnnou špičatou ukazatelem
- [ `->` Operátory (přístup u členů)](#pointer-member-access-operator--) a [ `[]` (přístup k prvkům)](#pointer-element-access-operator-)
- Aritmetické obsluze [ `+`, `-` `++`, , a`--`](#pointer-arithmetic-operators)
- Srovnávací operátory [ `==` `>`, `<=` `!=`, `<`, , a`>=`](#pointer-comparison-operators)

Informace o typech ukazatelů naleznete v tématu [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> Každá operace s ukazateli vyžaduje [nebezpečný](../keywords/unsafe.md) kontext. Kód, který obsahuje nebezpečné bloky, [`-unsafe`](../compiler-options/unsafe-compiler-option.md) musí být zkompilován s možností kompilátoru.

## <a name="address-of-operator-amp"></a><a name="address-of-operator-"></a>Adresa operátora&amp;

Unární `&` operátor vrátí adresu svého operandu:

[!code-csharp[address of local](snippets/PointerOperators.cs#AddressOf)]

Operand `&` provozovatele musí být pevná proměnná. *Pevné* proměnné jsou proměnné, které se nacházejí v umístěních úložiště, které nejsou ovlivněny provozem [systému uvolňování paměti](../../../standard/garbage-collection/index.md). V předchozím příkladu je `number` místní proměnná pevnou proměnnou, protože je umístěna v zásobníku. Proměnné, které jsou umístěny v umístěníúložiště, které mohou být ovlivněny systémem uvolňování paměti (například přemístěné) se nazývají *pohyblivé* proměnné. Pole objektů a prvky pole jsou příklady pohyblivých proměnných. Můžete získat adresu pohyblivé proměnné, pokud "opravit", nebo "pin", to s [ `fixed` příkazem](../keywords/fixed-statement.md). Získaná adresa je `fixed` platná pouze uvnitř bloku příkazu. Následující příklad ukazuje, jak `fixed` používat `&` příkaz a operátor:

[!code-csharp[address of fixed](snippets/PointerOperators.cs#AddressOfFixed)]

Nelze získat adresu konstanty nebo hodnoty.

Další informace o pevných a pohyblivých proměnných naleznete v části [Pevné a pohyblivé proměnné](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

Binární `&` operátor vypočítá [logické and](boolean-logical-operators.md#logical-and-operator-) jeho logické operandy nebo [bitové logické AND](bitwise-and-shift-operators.md#logical-and-operator-) jeho integrální operandy.

## <a name="pointer-indirection-operator-"></a>Operátor přesměrování ukazatele *

Unární ukazatel dereference `*` operátor získá proměnnou, na kterou jeho operand odkazuje. Je také známý jako dereference operátor. Operand operátoru `*` musí být typu ukazatele.

[!code-csharp[pointer indirection](snippets/PointerOperators.cs#PointerIndirection)]

`*` Operátor nelze použít na výraz `void*`typu .

Binární `*` operátor vypočítá [součin](arithmetic-operators.md#multiplication-operator-) jeho číselné operandy.

## <a name="pointer-member-access-operator--"></a>Operátor přístupu člena ukazatele ->

Operátor `->` kombinuje [dereference ukazatele](#pointer-indirection-operator-) a [přístup členů](member-access-operators.md#member-access-expression-). To znamená, `x` pokud je `T*` ukazatel `y` typu a je `T`přístupný člen typu , výraz formuláře

```csharp
x->y
```

je ekvivalentem

```csharp
(*x).y
```

Následující příklad ukazuje použití operátoru: `->`

[!code-csharp[pointer member access](snippets/PointerOperators.cs#MemberAccess)]

`->` Operátor nelze použít na výraz `void*`typu .

## <a name="pointer-element-access-operator-"></a>Operátor přístupu k elementu ukazatele []

Pro výraz `p` typu ukazatele je přístup prvku ukazatele `p[n]` formuláře `*(p + n)`vyhodnocen jako `n` , kde musí `int` `uint`být typu implicitně převoditelného na , , `long`, nebo `ulong`. Informace o chování operátoru `+` s ukazateli naleznete v tématu Sčítání nebo [odčítání integrální hodnoty do nebo z oddílu ukazatele.](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer)

Následující příklad ukazuje, jak získat přístup k `[]` prvkům pole s ukazatelem a operátorem:

[!code-csharp[pointer element access](snippets/PointerOperators.cs#ElementAccess)]

V předchozím příkladu [ `stackalloc` výraz](stackalloc.md) přiděluje blok paměti v zásobníku.

> [!NOTE]
> Operátor přístupu prvku ukazatele nekontroluje chyby mimo rozsah.

Nelze použít `[]` pro přístup k elementu `void*`ukazatele s výrazem typu .

Operátor můžete také `[]` použít pro [přístup k prvku pole nebo indexeru](member-access-operators.md#indexer-operator-).

## <a name="pointer-arithmetic-operators"></a>Aritmetické operátory ukazatele

S ukazateli můžete provádět následující aritmetické operace:

- Sčítání nebo odečtení integrální hodnoty k ukazateli nebo od něj
- Odečtení dvou ukazatelů
- Zvýšení nebo snížení ukazatele

Tyto operace nelze provádět s `void*`ukazateli typu .

Informace o podporovaných aritmetických operacích s číselnými typy naleznete [v tématu Aritmetické operátory](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Sčítání nebo odčítání integrální hodnoty do ukazatele nebo z ukazatele

Pro ukazatel `p` typu `T*` a `n` výraz typu implicitně `int`převoditelný na , `uint`, , `long`nebo `ulong`, sčítání a odčítání jsou definovány takto:

- Oba `p + n` `n + p` a výrazy vytvořit `T*` ukazatel typu, `n * sizeof(T)` který je `p`výsledkem přidání na adresu danou .
- Výraz `p - n` vytvoří ukazatel typu, `T*` který je výsledkem odečtení `n * sizeof(T)` `p`od adresy zadané .

[ `sizeof` Operátor](sizeof.md) získá velikost typu v bajtů.

Následující příklad ukazuje použití operátoru `+` s ukazatelem:

[!code-csharp[pointer addition](snippets/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>Odečtení ukazatele

Pro dva `p1` ukazatele `p2` a `T*`typu `p1 - p2` výraz vytváří rozdíl mezi adresami `p1` `p2` danými `sizeof(T)`a dělené . Typ výsledku je `long`. To znamená, `p1 - p2` že `((long)(p1) - (long)(p2)) / sizeof(T)`je vypočítán jako .

Následující příklad ukazuje odčítání ukazatele:

[!code-csharp[pointer subtraction](snippets/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>Přírůstek a snížení ukazatele

Operátor `++` přírůstek [přidá](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 do operandu ukazatele. Operátor `--` snížení [odečte](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 z jeho operand ukazovátku.

Oba operátory jsou podporovány ve`p++` `p--`dvou formách:`++p` `--p`postfix ( a ) a prefix ( a ). Výsledek `p++` a `p--` je hodnota `p` *před* operací. Výsledek `++p` a `--p` je hodnota `p` *po* operaci.

Následující příklad ukazuje chování operátorů přípony i přírůstku předpony:

[!code-csharp[pointer increment](snippets/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>Operátory porovnání ukazatelů

Operandy `==` `!=` `<` `>` `<=`libovolného typu ukazatele, včetně `void*` `>=` . Tito operátoři porovnávají adresy dané dvěma operandy, jako by se jednalo o nepodepsaná celá čísla.

Informace o chování těchto operátorů pro operandy jiných typů naleznete v [článcích Operátory rovnosti](equality-operators.md) a [Operátory porovnání.](comparison-operators.md)

## <a name="operator-precedence"></a>Priorita operátorů

Následující seznam seřídí operátory související s ukazatelem od nejvyšší priority k nejnižší:

- Operátory přírůstek `x++` a `x--` snížení přípony a operátory `->` a `[]`
- Operátory přírůstku `++x` a snížení předpony `*` a operátory a operátory `&` `--x`
- Doplňkové `+` `-` látky a obsluha
- Srovnání `<` `>`, `<=`, `>=` , a operátory
- Rovnost `==` a `!=` provozovatelé

Pomocí závorek `()`, můžete změnit pořadí hodnocení uloženého prioritou operátoru.

Úplný seznam operátorů jazyka C# seřazené podle úrovně priority naleznete v části [Priorita operátora](index.md#operator-precedence) v článku [operátorů jazyka C#.](index.md)

## <a name="operator-overloadability"></a>Přetížení obsluhy

Uživatelem definovaný typ nemůže přetížit `*` `->`operátory `[]` `&`související s ukazatelem , , a .

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Pevné a pohyblivé proměnné](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [Adresa operátora](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [Přesměrování ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [Přístup člena ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [Přístup k elementu ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [Aritmetika ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [Přírůstek a snížení ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [Porovnání ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [nebezpečné klíčové slovo](../keywords/unsafe.md)
- [pevné klíčové slovo](../keywords/fixed-statement.md)
- [stackalloc](stackalloc.md)
- [sizeof – operátor](sizeof.md)
