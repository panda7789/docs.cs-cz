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
ms.openlocfilehash: 830aef8546191df3df4a70e350ba561367a9e474
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512358"
---
# <a name="pointer-related-operators-c-reference"></a>Operátory související s ukazateli (C# referenční)

Pro práci s ukazateli můžete použít následující operátory:

- Unární operátor ( [ Address-of):prozískáníadresy`&` ](#address-of-operator-) proměnné
- Unární operátor ( [ indirekceukazatele):prozískáníproměnné,nakterouodkazuje`*` ](#pointer-indirection-operator-) ukazatel
- Operátory [(přístup ke členům) a (přístup k prvkům) `->` ](#pointer-member-access-operator--) [ `[]` ](#pointer-element-access-operator-)
- Aritmetické [ `+`operátory `-`,, `++`a`--`](#pointer-arithmetic-operators)
- Operátory [ `==`porovnání ,`!=`, `<` ,,a`<=` `>``>=`](#pointer-comparison-operators)

Informace o typech ukazatelů naleznete v tématu [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> Jakákoli operace s ukazateli vyžaduje nezabezpečený kontext. [](../keywords/unsafe.md) Kód, který obsahuje nebezpečné bloky, musí být zkompilován s [`-unsafe`](../compiler-options/unsafe-compiler-option.md) možností kompilátoru.

## <a name="address-of-operator-"></a>Address-of – operátor&amp;

Unární `&` operátor vrátí adresu svého operandu:

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

Operandem `&` operátoru musí být pevná proměnná. *Pevné* proměnné jsou proměnné, které jsou umístěny v umístěních úložiště, která nejsou ovlivněna operací [uvolňování paměti](../../../standard/garbage-collection/index.md). V předchozím příkladu je místní proměnná `number` pevnou proměnnou, protože se nachází v zásobníku. Proměnné, které jsou umístěné v umístění úložiště, které může být ovlivněno systémem uvolňování paměti (například přemístěné) , se nazývají pohyblivé proměnné. V příkladech pohyblivých proměnných jsou pole objektů a prvky pole. Adresu pohyblivé proměnné můžete získat, pokud "opravíte" nebo "PIN", pomocí příkazu [fixed](../keywords/fixed-statement.md) . Získaná adresa je platná pouze po dobu trvání `fixed` bloku příkazu. Následující příklad ukazuje, jak použít `fixed` příkaz `&` a operátor:

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

Nemůžete získat adresu konstanty nebo hodnoty.

Další informace o pevných a pohyblivých proměnných naleznete v části [pevné a mobilní](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) proměnné [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

Binární `&` operátor vypočítá [logický a](boolean-logical-operators.md#logical-and-operator-) jeho logický operandy nebo bitovou logickou hodnotu [a](bitwise-and-shift-operators.md#logical-and-operator-) její celočíselné operandy.

## <a name="pointer-indirection-operator-"></a>Operátor dereference ukazatele *

Operátor `*` dereference unárního ukazatele získá proměnnou, do které se operandy vykáže. Označuje se také jako operátor odkázání. Operand `*` operátoru musí být typu ukazatele.

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

`*` Operátor nelze použít na výraz typu `void*`.

Binární `*` operátor vypočítá [součin](arithmetic-operators.md#multiplication-operator-) svých číselných operandů.

## <a name="pointer-member-access-operator--"></a>Operátor přístupu členů ukazatele->

Operátor `->` kombinuje [nepřímý odkaz na ukazatele](#pointer-indirection-operator-) a [přístup ke členu](member-access-operators.md#member-access-operator-). To znamená, že `x` Pokud je ukazatel typu `T*` a `y` je přístupným členem `T`, výraz formuláře

```csharp
x->y
```

je ekvivalentem

```csharp
(*x).y
```

Následující příklad ukazuje použití `->` operátoru:

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

`->` Operátor nelze použít na výraz typu `void*`.

## <a name="pointer-element-access-operator-"></a>Operátor přístupu k elementu ukazatele []

Pro výraz `p` typu ukazatele je přístup k elementu formuláře `p[n]` vyhodnocen jako `*(p + n)`, kde `n` musí být typu implicitně převoditelný na `int`, `uint`, `long`nebo `ulong`. Informace o chování `+` operátoru s ukazateli naleznete v části [sčítání nebo odčítání celočíselné hodnoty nebo z ukazatele na ukazatel](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) .

Následující příklad ukazuje, jak přistupovat k prvkům pole s ukazatelem a `[]` operátorem:

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

V příkladu se pomocí [ `stackalloc` operátoru](stackalloc.md) přidělí blok paměti v zásobníku.

> [!NOTE]
> Operátor přístupu elementu ukazatele nekontroluje chyby mimo hranice.

Nemůžete `[]` použít pro přístup k prvku ukazatele s výrazem `void*`typu.

`[]` Operátor můžete použít také pro [prvek pole nebo pro přístup k indexeru](member-access-operators.md#indexer-operator-).

## <a name="pointer-arithmetic-operators"></a>Aritmetické operátory ukazatele

S ukazateli můžete provádět následující aritmetické operace:

- Přidat nebo odečíst celočíselnou hodnotu do nebo z ukazatele
- Odečíst dva ukazatele
- Zvýšení nebo snížení ukazatele

Tyto operace nelze provést s ukazateli typu `void*`.

Informace o podporovaných aritmetických operacích s číselnými typy naleznete v tématu [aritmetické operátory](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Sčítání nebo odečítání celočíselné hodnoty do nebo z ukazatele

Pro ukazatel `p` typu `long` `int` `ulong` `uint`a výraz `n` typu implicitně převoditelné na,, nebo sčítání a odčítání jsou definovány takto: `T*`

- Oba `p + n` výrazy `n + p` a vytvoří ukazatel typu `T*` , který je `p`výsledkem přidání `n * sizeof(T)` na adresu danou adresou.
- Výraz vytvoří ukazatel typu `T*` , který je `n * sizeof(T)` výsledkem odečtení od adresy uvedené `p`v. `p - n`

Operátor získá velikost typu v bajtech. [ `sizeof` ](sizeof.md)

Následující příklad ukazuje použití `+` operátoru s ukazatelem:

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>Odečtení ukazatele

`p1` Pro dva ukazatele a `p2` typ `T*`je `p1 - p2` `p1` výsledkemvýrazu`p2` rozdíl mezi adresami předanými a dělenou. `sizeof(T)` Typ výsledku je `long`. To znamená, `p1 - p2` že je vypočítávána jako. `((long)(p1) - (long)(p2)) / sizeof(T)`

Následující příklad ukazuje odčítání ukazatele:

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>Zvýšení a snížení ukazatele

Operátor přírůstku přidá hodnotu 1 k operandu ukazatele. [](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) `++` Operátor snížení odečte 1 od jeho operandu ukazatele. [](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) `--`

Oba operátory jsou podporovány ve dvou formulářích: přípona`p++` ( `p--`a) a předpona `--p`(`++p` a). Výsledek `p++` a `p--` je hodnota `p` *před* operací. Výsledek `++p` a `--p` je hodnota `p` *po* operaci.

Následující příklad demonstruje chování obou operátorů přípony i prefixu:

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>Operátory porovnání ukazatelů

`==` `void*`Operátory ,`!=` ,`>`,, a`<=`můžete použít k porovnání operandů libovolného typu ukazatele, včetně. `<` `>=` Tyto operátory porovnávají adresy zadané dvěma operandy, jako by šlo o celá čísla bez znaménka.

Informace o chování těchto operátorů pro operandy jiných typů naleznete v článcích [operátory rovnosti](equality-operators.md) a [operátory porovnání](comparison-operators.md) .

## <a name="operator-precedence"></a>Priorita operátorů

Následující seznam uvádí operátory související s ukazateli počínaje od nejvyšší priority k nejnižší:

- Operátory `x++` přírůstku `x--` a snížení přípony `->` a `[]` operátory a
- Operátory `++x` přírůstku `--x` a snížení předpony `*` a `&` operátory a
- `+` Doplňková `-` a operátor
- Operátory `<`porovnání `>`, ,a`<=` `>=`
- Rovnost `==` a `!=` operátory

Použijte závorky, `()`Chcete-li změnit pořadí vyhodnocování stanovené předností operátorů.

Úplný seznam C# operátorů seřazených podle priority úrovně naleznete v tématu [ C# operátory](index.md).

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ nemůže `&`přetížit operátory související s ukazatelem `->`, `*`, a `[]`.

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

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [UNSAFE – klíčové slovo](../keywords/unsafe.md)
- [klíčové slovo fixed](../keywords/fixed-statement.md)
- [stackalloc – operátor](stackalloc.md)
- [sizeof – operátor](sizeof.md)
