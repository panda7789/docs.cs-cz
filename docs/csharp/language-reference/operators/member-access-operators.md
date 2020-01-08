---
title: Operátory přístupu členů – C# referenční informace
description: Další informace C# o operátorech, které lze použít pro přístup ke členům typu.
ms.date: 09/18/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: e69cc5a9634f0b5232562782557645894f94ce2e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345306"
---
# <a name="member-access-operators-c-reference"></a>Operátory přístupu členů (C# referenční)

Při přístupu k členu typu můžete použít následující operátory:

- [`.` (přístup do členů)](#member-access-operator-): přístup ke členu oboru názvů nebo typu
- [`[]` (element pole nebo přístup indexeru)](#indexer-operator-): pro přístup k prvku pole nebo indexeru typu
- [`?.` a `?[]` (koncoví operátoři s hodnotou null)](#null-conditional-operators--and-): k provedení operace přístupu člena nebo elementu pouze v případě, že operand je jiný než null
- [`()` (vyvolání)](#invocation-operator-): pro volání metody, která je k dispozici, nebo vyvolání delegáta
- [`^` (index z konce)](#index-from-end-operator-): k označení, že pozice prvku je od konce sekvence
- [`..` (rozsah)](#range-operator-): Pokud chcete zadat rozsah indexů, které můžete použít k získání rozsahu elementů Sequence.

## <a name="member-access-operator-"></a>Operátor přístupu ke členu.

Token `.` použijete pro přístup ke členu oboru názvů nebo typu, jak ukazuje následující příklad:

- Použijte `.` pro přístup k vnořenému oboru názvů v rámci oboru názvů, jak ukazuje následující příklad [direktivy`using`](../keywords/using-directive.md) :

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- Použijte `.` k vytvoření *kvalifikovaného názvu* pro přístup k typu v rámci oboru názvů, jak ukazuje následující kód:

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  Použijte [direktivu`using`](../keywords/using-directive.md) , aby bylo možné používat kvalifikované názvy jako nepovinné.

- Použijte `.` pro přístup ke [členům typu](../../programming-guide/classes-and-structs/index.md#members), statické a nestatické, jak ukazuje následující kód:

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

Pro přístup k [metodě rozšíření](../../programming-guide/classes-and-structs/extension-methods.md)můžete použít také `.`.

## <a name="indexer-operator-"></a>Operátor indexer []

Hranaté závorky, `[]`, se obvykle používají pro přístup k objektům Array, indexer nebo Pointer.

### <a name="array-access"></a>Přístup k poli

Následující příklad ukazuje, jak získat přístup k prvkům pole:

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

Pokud je index pole mimo hranice odpovídající dimenze pole, je vyvolána <xref:System.IndexOutOfRangeException>.

Jak ukazuje předchozí příklad, je také možné použít hranaté závorky, pokud deklarujete typ pole nebo instanci pole instance.

Další informace o polích naleznete v tématu [Arrays](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Přístup indexeru

Následující příklad používá typ <xref:System.Collections.Generic.Dictionary%602> .NET k demonstraci přístupu indexeru:

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

Indexery umožňují indexovat instance uživatelsky definovaného typu podobným způsobem jako indexování pole. Na rozdíl od indexů pole, který musí být celé číslo, lze parametry indexeru deklarovat jako libovolný typ.

Další informace o indexerech najdete v tématu [indexery](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Další použití []

Informace o přístupu k prvkům ukazatele naleznete v části [operátor přístupu k prvku ukazatele []](pointer-related-operators.md#pointer-element-access-operator-) v článku o [operátorech souvisejících s ukazateli](pointer-related-operators.md) .

Pomocí hranatých závorek určíte [atributy](../../programming-guide/concepts/attributes/index.md):

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Podmíněné operátory s hodnotou null?. ani? []

K dispozici v 6 nebo novějším, operátor s hodnotou null používá pro přístup C# [člena přístup](#member-access-operator-), `?.`nebo [k elementu](#indexer-operator-), `?[]`, operaci na jeho operand pouze v případě, že je tento operand vyhodnocen jako jiný než null; v opačném případě vrátí `null`. To je

- Pokud se `a` vyhodnotí jako `null`, výsledek `a?.x` nebo `a?[x]` je `null`.
- Pokud je `a` vyhodnocena jako nenulová, výsledek `a?.x` nebo `a?[x]` je stejný jako výsledek `a.x` nebo `a[x]`v uvedeném pořadí.

  > [!NOTE]
  > Pokud `a.x` nebo `a[x]` vyvolá výjimku, `a?.x` nebo `a?[x]` by vyvolal stejnou výjimku pro `a`, který není null. Například pokud `a` je instance pole, která není null a `x` je mimo hranice `a`, `a?[x]` by vyvolala <xref:System.IndexOutOfRangeException>.

Operátory podmíněné hodnotou null jsou krátkodobé okruhy. To znamená, že pokud jedna operace v řetězci podmíněného člena nebo operace přístupu k elementu vrátí `null`, zbytek řetězu se nespustí. V následujícím příkladu není `B` vyhodnocena, pokud `A` vyhodnocena `null` a `C` nejsou vyhodnoceny, pokud `A` nebo `B` vyhodnocena jako `null`:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Následující příklad ukazuje použití operátorů `?.` a `?[]`:

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

Předchozí příklad také používá [operátor slučování null `??`](null-coalescing-operator.md) k určení alternativního výrazu pro vyhodnocení pro případ, že je `null`výsledek operace podmíněného hodnoty null.

Podmíněný operátor přístupu člena s hodnotou null `?.` je také označován jako operátor Elvis.

### <a name="thread-safe-delegate-invocation"></a>Volání delegáta bezpečné pro přístup z více vláken

Použijte operátor `?.`, chcete-li zjistit, zda delegát není null, a vyvolat ho v bezpečném režimu (například při [vyvolání události](../../../standard/events/how-to-raise-and-consume-events.md)), jak ukazuje následující kód:

```csharp
PropertyChanged?.Invoke(…)
```

Tento kód je ekvivalentní následujícímu kódu, který byste použili v C# 5 nebo starších verzích:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a>Operátor vyvolání ()

Použijte kulaté závorky, `()`, pro volání [metody](../../programming-guide/classes-and-structs/methods.md) nebo vyvolání [delegáta](../../programming-guide/delegates/index.md).

Následující příklad ukazuje, jak zavolat metodu s argumenty nebo bez argumentů a vyvolat delegáta:

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

Závorky můžete použít také při volání [konstruktoru](../../programming-guide/classes-and-structs/constructors.md) s operátorem [`new`](new-operator.md) .

### <a name="other-usages-of-"></a>Další použití pro ()

Pomocí závorek můžete také upravit pořadí, ve kterém se mají vyhodnocovat operace ve výrazu. Další informace najdete v tématu [ C# operátory](index.md).

[Výrazy přetypování](type-testing-and-cast.md#cast-operator-), které provádějí explicitní převody typů, používají také závorky.

## <a name="index-from-end-operator-"></a>Index z operátoru end ^

K dispozici v C# 8,0 a novějším, operátor `^` označuje pozici elementu na konci sekvence. Pro sekvenci délky `length``^n` odkazuje na prvek s posunem `length - n` od začátku sekvence. Například `^1` odkazuje na poslední prvek sekvence a `^length` odkazuje na první prvek sekvence.

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

Jak ukazuje předchozí příklad, `^e` výrazů je typ <xref:System.Index?displayProperty=nameWithType>. Ve výrazu `^e`musí být výsledek `e` implicitně převoditelné na `int`.

Můžete také použít operátor `^` s [operátorem Range](#range-operator-) a vytvořit tak rozsah indexů. Další informace najdete v tématu [indexy a rozsahy](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Operátor rozsahu..

K dispozici v C# 8,0 a novějším, operátor `..` Určuje začátek a konec rozsahu indexů jako své operandy. Levý operand je *Celková* začátek rozsahu. Pravý operand je *výhradním* koncem rozsahu. Jedním z operandů může být index od začátku nebo po konci sekvence, jak ukazuje následující příklad:

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

Jak ukazuje předchozí příklad, `a..b` výrazů je typ <xref:System.Range?displayProperty=nameWithType>. Ve výrazu `a..b`musí být výsledky `a` a `b` implicitně převoditelné na `int` nebo <xref:System.Index>.

Můžete vynechat kterýkoli z operandů operátoru `..`, abyste získali rozsah otevřeného a koncového výrazu:

- `a..` je ekvivalentem `a..^0`
- `..b` je ekvivalentem `0..b`
- `..` je ekvivalentem `0..^0`

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

Další informace najdete v tématu [indexy a rozsahy](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Přetížení operátoru

Operátory `.`, `()`, `^`a `..` nelze přečítat. Operátor `[]` je také považován za operátor, který není přetížen. Použijte [indexery](../../programming-guide/indexers/index.md) k podpoře indexování s uživatelsky definovanými typy.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Přístup ke členu](~/_csharplang/spec/expressions.md#member-access)
- [Přístup k prvkům](~/_csharplang/spec/expressions.md#element-access)
- [Podmíněný operátor s hodnotou null](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Výrazy vyvolání](~/_csharplang/spec/expressions.md#invocation-expressions)

Další informace o indexech a oblastech najdete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/ranges.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [?? (operátor slučování null)](null-coalescing-operator.md)
- [:: – operátor](namespace-alias-qualifier.md)
