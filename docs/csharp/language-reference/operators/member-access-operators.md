---
title: Operátory přístupu členů – C# referenční informace
description: Další informace C# o operátorech, které lze použít pro přístup ke členům typu.
ms.date: 05/09/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
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
ms.openlocfilehash: 763fdb442fa0037dafd51f89badd04436e24d254
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566830"
---
# <a name="member-access-operators-c-reference"></a>Operátory přístupu členů (C# referenční)

Při přístupu k členu typu můžete použít následující operátory:

- (přístup ke členu): přístup ke členu oboru názvů nebo typu [ `.` ](#member-access-operator-)
- [(element pole nebo přístup indexeru): pro přístup k prvku pole nebo indexeru typu `[]` ](#indexer-operator-)
- [a (podmíněnéoperátoryshodnotounull):kprovedeníoperacepřístupučlenaneboelementupouzevpřípadě,žeoperandjenenulový`?[]` `?.` ](#null-conditional-operators--and-)
- (vyvolání): pro volání metody, která je k dispozici, nebo vyvolání delegáta [ `()` ](#invocation-operator-)

## <a name="member-access-operator-"></a>Operátor přístupu ke členu.

`.` Token použijete pro přístup ke členu oboru názvů nebo typu, jak ukazuje následující příklad:

- Použijte `.` pro přístup k vnořenému oboru názvů v rámci oboru názvů, jak ukazuje následující [ `using` ](../keywords/using-directive.md) příklad direktivy:

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- Slouží `.` k vytvoření *kvalifikovaného názvu* pro přístup k typu v rámci oboru názvů, jak ukazuje následující kód:

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  Použijte směrnici pro použití kvalifikovaných názvů jako nepovinné. [ `using` ](../keywords/using-directive.md)

- Použijte `.` pro přístup ke [členům typu](../../programming-guide/classes-and-structs/index.md#members), statické a nestatické, jak ukazuje následující kód:

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

Můžete také použít `.` pro přístup k [metodě rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Operátor indexer []

Hranaté závorky `[]`se obvykle používají pro přístup k objektům Array, indexer nebo Pointer.

### <a name="array-access"></a>Přístup k poli

Následující příklad ukazuje, jak získat přístup k prvkům pole:

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

Pokud je index pole mimo hranice odpovídající dimenze pole, <xref:System.IndexOutOfRangeException> je vyvolána výjimka.

Jak ukazuje předchozí příklad, je také možné použít hranaté závorky, pokud deklarujete typ pole nebo instanci pole instance.

Další informace o polích naleznete v tématu [Arrays](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Přístup indexeru

Následující příklad používá typ .NET <xref:System.Collections.Generic.Dictionary%602> k demonstraci přístupu indexeru:

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

Indexery umožňují indexovat instance uživatelsky definovaného typu podobným způsobem jako indexování pole. Na rozdíl od indexů pole, který musí být celé číslo, argumenty indexeru lze deklarovat jako libovolný typ.

Další informace o indexerech najdete v tématu [indexery](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Další použití []

Informace o přístupu k prvkům ukazatele naleznete v části [operátor přístupu k prvku ukazatele []](pointer-related-operators.md#pointer-element-access-operator-) v článku o [operátorech souvisejících s ukazateli](pointer-related-operators.md) .

Pomocí hranatých závorek určíte [atributy](../../programming-guide/concepts/attributes/index.md):

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Podmíněné operátory s hodnotou null?. ani? []

K dispozici v 6 nebo novějším, operátor s hodnotou null aplikuje na `?.`operand přístup člena, `?[]`nebo element, operace na jeho operand pouze v C# případě, že se tento operand vyhodnocuje jako nenulový. Pokud je operand vyhodnocen `null`jako, výsledek použití operátoru je. `null` Operátor `?.` přístupu k podmíněnému členu s hodnotou null je také označován jako Elvis operátor.

Operátory podmíněné hodnotou null jsou krátkodobé okruhy. To znamená, že pokud se vrátí `null`jedna operace v řetězci podmíněného člena nebo operace přístupu k prvkům, zbytek řetězu se nespustí. V následujícím `B` příkladu není vyhodnocena, pokud `A` `null` je vyhodnocena `C` jako a není vyhodnocena v případě `null`, že `A` nebo `B` je vyhodnocena jako:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Následující příklad ukazuje použití `?.` operátorů a: `?[]`

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

Předchozí příklad také ukazuje použití operátoru nulového [slučování](null-coalescing-operator.md). Operátor pro sjednocení hodnoty null můžete použít k poskytnutí alternativního výrazu pro vyhodnocení pro případ, že je `null`výsledkem operace podmíněného zpracování hodnoty null.

### <a name="thread-safe-delegate-invocation"></a>Volání delegáta bezpečné pro přístup z více vláken

Použijte operátor ke kontrole, zda delegát není null a vyvolá ho v bezpečném režimu (například při [vyvolání události](../../../standard/events/how-to-raise-and-consume-events.md)), jak ukazuje následující kód: `?.`

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

Použijte závorky, `()`, pro volání [metody](../../programming-guide/classes-and-structs/methods.md) nebo vyvolání delegáta [](../../programming-guide/delegates/index.md).

Následující příklad ukazuje, jak zavolat metodu s argumenty nebo bez argumentů a vyvolat delegáta:

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

Při vyvolání [konstruktoru](../../programming-guide/classes-and-structs/constructors.md) s [`new`](new-operator.md) operátorem můžete také použít závorky.

### <a name="other-usages-of-"></a>Další použití pro ()

K určení pořadí, ve kterém se mají vyhodnotit operace ve výrazu, můžete také použít kulaté závorky. Další informace naleznete v části [Přidání závorek](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) v článku věnovaném [operátorům](../../programming-guide/statements-expressions-operators/operators.md) . Seznam operátorů seřazených podle priority najdete v tématu [ C# operátory](index.md).

[Výrazy přetypování](type-testing-and-cast.md#cast-operator-), které provádějí explicitní převody typů, používají také závorky.

## <a name="operator-overloadability"></a>Přetížení operátoru

Operátory `.` a`()` nemohou být přetíženy. `[]` Operátor je také považován za operátor, který není přetížen. Použijte [indexery](../../programming-guide/indexers/index.md) k podpoře indexování s uživatelsky definovanými typy.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Přístup ke členu](~/_csharplang/spec/expressions.md#member-access)
- [Přístup k prvkům](~/_csharplang/spec/expressions.md#element-access)
- [Podmíněný operátor s hodnotou null](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Výrazy vyvolání](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [?? (operátor slučování null)](null-coalescing-operator.md)
- [:: – operátor](namespace-alias-qualifier.md)
