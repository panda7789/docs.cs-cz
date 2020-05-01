---
title: Operátory přístupu členů a výrazy – reference jazyka C#
description: Přečtěte si o operátorech jazyka C#, které lze použít pro přístup ke členům typu.
ms.date: 04/17/2020
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
ms.openlocfilehash: 37a6cb7cd32a9d60607aec51b1994e4717c5349a
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624862"
---
# <a name="member-access-operators-and-expressions-c-reference"></a>Operátory a výrazy přístupu členů (Referenční dokumentace jazyka C#)

Při přístupu k členu typu můžete použít následující operátory a výrazy:

- [(přístup ke členu): přístup ke členu oboru názvů nebo typu `.` ](#member-access-expression-)
- [(element pole nebo přístup indexeru): pro přístup k prvku pole nebo indexeru typu `[]` ](#indexer-operator-)
- [a `?[]` podmíněné operátory s hodnotou null): k provedení operace přístupu člena nebo elementu pouze v případě, že operand je `?.` ](#null-conditional-operators--and-)nenulový
- (vyvolání): pro volání metody, která je k dispozici, nebo vyvolání delegáta [ `()` ](#invocation-expression-)
- [(index od konce): k označení, že pozice prvku je od konce sekvence `^` ](#index-from-end-operator-)
- (rozsah): Pokud chcete zadat rozsah indexů, které můžete použít k získání rozsahu elementů Sequence. [ `..` ](#range-operator-)

## <a name="member-access-expression-"></a>Výraz přístupu členů

`.` Token použijete pro přístup ke členu oboru názvů nebo typu, jak ukazuje následující příklad:

- Použijte `.` pro přístup k vnořenému oboru názvů v rámci oboru názvů, jak ukazuje následující příklad [ `using` direktivy](../keywords/using-directive.md) :

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- Slouží `.` k vytvoření *kvalifikovaného názvu* pro přístup k typu v rámci oboru názvů, jak ukazuje následující kód:

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  Použijte [ `using` směrnici](../keywords/using-directive.md) pro použití kvalifikovaných názvů jako nepovinné.

- Použijte `.` pro přístup ke [členům typu](../../programming-guide/classes-and-structs/index.md#members), statické a nestatické, jak ukazuje následující kód:

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

Můžete také použít `.` pro přístup k [metodě rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Operátor indexer []

Hranaté závorky `[]`se obvykle používají pro přístup k objektům Array, indexer nebo Pointer.

### <a name="array-access"></a>Přístup k poli

Následující příklad ukazuje, jak získat přístup k prvkům pole:

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

Pokud je index pole mimo hranice odpovídající dimenze pole, <xref:System.IndexOutOfRangeException> je vyvolána výjimka.

Jak ukazuje předchozí příklad, je také možné použít hranaté závorky, pokud deklarujete typ pole nebo instanci pole instance.

Další informace o polích naleznete v tématu [Arrays](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Přístup indexeru

Následující příklad používá typ .NET <xref:System.Collections.Generic.Dictionary%602> k demonstraci přístupu indexeru:

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

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

K dispozici v C# 6 a novějším, operátor s hodnotou null [member access](#member-access-expression-)aplikuje na `?.`operand přístup člena, nebo `?[]`k [elementu](#indexer-operator-), a operaci na jeho operand pouze v případě, že je tento operand vyhodnocen jako jiný než null; v opačném případě `null`vrátí. To je

- Pokud `a` `null`se vyhodnotí jako, výsledek `a?.x` nebo `a?[x]` je `null`.
- Pokud `a` se vyhodnotí jako jiné než null, výsledek `a?.x` nebo `a?[x]` je stejný jako výsledek `a.x` nebo `a[x]`v uvedeném pořadí.

  > [!NOTE]
  > Pokud `a.x` nebo `a[x]` vyvolá výjimku `a?.x` nebo `a?[x]` by vyvolala stejnou výjimku pro jinou hodnotu než null `a`. Například `a` Pokud je instance pole `x` `a`, která není null a je mimo hranice, `a?[x]` by vyvolala. <xref:System.IndexOutOfRangeException>

Operátory podmíněné hodnotou null jsou krátkodobé okruhy. To znamená, že pokud se vrátí `null`jedna operace v řetězci podmíněného člena nebo operace přístupu k prvkům, zbytek řetězu se nespustí. V `B` následujícím příkladu není vyhodnocena, pokud `A` je vyhodnocena jako `null` a `C` není vyhodnocena v případě, že `A` nebo `B` je vyhodnocena jako: `null`

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Následující příklad ukazuje použití operátorů `?.` a: `?[]`

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

Předchozí příklad také používá [ `??` operátor slučování null](null-coalescing-operator.md) k určení alternativního výrazu pro vyhodnocení pro případ, že je `null`výsledkem operace podmíněného zpracování hodnoty null.

Pokud `a.x` nebo `a[x]` je typ `T` `a?.x` hodnoty, která není null, nebo `a?[x]` je odpovídající [typ](../builtin-types/nullable-value-types.md) `T?`hodnoty s možnou hodnotou null. Pokud potřebujete výraz typu `T`, použijte operátor `??` slučování null na podmíněný výraz s hodnotou null, jak ukazuje následující příklad:

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

V `??` předchozím příkladu, pokud operátor nepoužíváte, se vyhodnotí `numbers?.Length < 2` `false` jako, `numbers` Pokud `null`je.

Operátor `?.` přístupu k podmíněnému členu s hodnotou null je také označován jako Elvis operátor.

> [!NOTE]
> V C# 8 [operátor null-striktní](null-forgiving.md) ukončí seznam předchozích operací s hodnotou null. Například výraz `x?.y!.z` je analyzován jako `(x?.y)!.z`. Z důvodu této interpretace `z` je vyhodnocena `x` i `null`v případě, že je, <xref:System.NullReferenceException>což může vést k.

### <a name="thread-safe-delegate-invocation"></a>Volání delegáta bezpečné pro přístup z více vláken

Použijte `?.` operátor ke kontrole, zda delegát není null a vyvolá ho v bezpečném režimu (například při [vyvolání události](../../../standard/events/how-to-raise-and-consume-events.md)), jak ukazuje následující kód:

```csharp
PropertyChanged?.Invoke(…)
```

Tento kód je ekvivalentní následujícímu kódu, který byste použili v C# 5 nebo starší:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

To je způsob bezpečný pro přístup z více vláken, aby bylo zajištěno, `handler` že je vyvolána pouze hodnota, která není null. Vzhledem k tomu, že instance delegátů jsou neměnné, nemůže žádné vlákno změnit `handler` hodnotu, na kterou odkazuje místní proměnná. Zejména pokud je kód, který je spuštěn jiným vláknem, odhlásil odběr `PropertyChanged` z události `PropertyChanged` a `null` stane `handler` se před vyvoláním, hodnota `handler` odkazovaná zůstává neovlivněno. `?.` Operátor vyhodnocuje svůj operand na levé straně více než jednou a zaručuje, že nemůže být změněn na `null` po ověření jako nenulového typu.

## <a name="invocation-expression-"></a>Výraz vyvolání ()

Použijte závorky, `()`, pro volání [metody](../../programming-guide/classes-and-structs/methods.md) nebo vyvolání [delegáta](../../programming-guide/delegates/index.md).

Následující příklad ukazuje, jak zavolat metodu s argumenty nebo bez argumentů a vyvolat delegáta:

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

Při vyvolání [konstruktoru](../../programming-guide/classes-and-structs/constructors.md) s [`new`](new-operator.md) operátorem můžete také použít závorky.

### <a name="other-usages-of-"></a>Další použití pro ()

Pomocí závorek můžete také upravit pořadí, ve kterém se mají vyhodnocovat operace ve výrazu. Další informace naleznete v tématu [operátory jazyka C#](index.md).

[Výrazy přetypování](type-testing-and-cast.md#cast-expression), které provádějí explicitní převody typů, používají také závorky.

## <a name="index-from-end-operator-"></a>Index z operátoru end ^

K dispozici v C# 8,0 a novějším, `^` operátor označuje pozici elementu na konci sekvence. Pro sekvenci délky `length` `^n` odkazuje na prvek s posunem `length - n` od začátku sekvence. Například `^1` odkazuje na poslední prvek sekvence a `^length` odkazuje na první prvek sekvence.

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

Jak ukazuje předchozí příklad, výraz `^e` je <xref:System.Index?displayProperty=nameWithType> typu. Ve výrazu `^e`je výsledek `e` nutné implicitně převést na `int`.

Můžete také použít `^` operátor s [operátorem Range](#range-operator-) a vytvořit tak rozsah indexů. Další informace najdete v tématu [indexy a rozsahy](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Operátor rozsahu..

K dispozici v C# 8,0 a novějších `..` operátor určuje začátek a konec rozsahu indexů jako své operandy. Levý operand je *Celková* začátek rozsahu. Pravý operand je *výhradním* koncem rozsahu. Jedním z operandů může být index od začátku nebo po konci sekvence, jak ukazuje následující příklad:

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

Jak ukazuje předchozí příklad, výraz `a..b` je <xref:System.Range?displayProperty=nameWithType> typu. Ve výrazu `a..b`jsou výsledky `a` a `b` musí být implicitně převoditelné na `int` nebo <xref:System.Index>.

Pokud chcete získat rozsah otevřeného a koncového výrazu `..` , můžete vynechat kterýkoli z operandů operátoru:

- `a..`je ekvivalentem`a..^0`
- `..b`je ekvivalentem`0..b`
- `..`je ekvivalentem`0..^0`

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

Další informace najdete v tématu [indexy a rozsahy](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Přetížení operátoru

`..` Operátory `.`, `()`, `^`a nemohou být přetíženy. `[]` Operátor je také považován za operátor, který není přetížen. Použijte [indexery](../../programming-guide/indexers/index.md) k podpoře indexování s uživatelsky definovanými typy.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Přístup ke členu](~/_csharplang/spec/expressions.md#member-access)
- [Přístup k prvkům](~/_csharplang/spec/expressions.md#element-access)
- [Podmíněný operátor s hodnotou null](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Výrazy vyvolání](~/_csharplang/spec/expressions.md#invocation-expressions)

Další informace o indexech a oblastech najdete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/ranges.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [?? (operátor slučování null)](null-coalescing-operator.md)
- [:: – operátor](namespace-alias-qualifier.md)
