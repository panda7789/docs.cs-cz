---
title: Operátory přístupu členů - C# odkaz
description: Další informace o C# operátory, které můžete použít pro přístup ke členům typu.
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
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
ms.openlocfilehash: 2c5f569b0ad68132e07b009ec9968c766bb965f5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633519"
---
# <a name="member-access-operators"></a>Operátory pro přístup k členům

Při přístupu k člena typu můžete použít následující operátory:

- [`.` (přístup ke členu) ](#member-access-operator-): přístup k oboru názvů nebo typ
- [`[]` (element nebo indexovací člen přístup k poli) ](#indexer-operator-): přístup k elementu pole nebo typ indexeru
- [`?.` a `?[]` (podmíněné operátory s null)](#null-conditional-operators--and-): k provedení operace přístupu člen nebo element, pouze pokud operand je jiná než null
- [`()` (volání) ](#invocation-operator-): volání metody používaná nebo vyvolat delegáta

## <a name="member-access-operator-"></a>Operátor přístupu členů.

Můžete použít `.` token pro přístup k oboru názvů nebo typ, jak ukazují následující příklady:

- Použití `.` pro přístup k vnořené oboru názvů v oboru názvů, jako následující příklad [ `using` směrnice](../keywords/using-directive.md) ukazuje:

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- Použití `.` do formuláře *kvalifikovaný název* pro přístup k typu v rámci oboru názvů, jak ukazuje následující kód:

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  Použít [ `using` směrnice](../keywords/using-directive.md) provést volitelné použijte kvalifikované názvy.

- Použití `.` přístup [členy typu](../../programming-guide/classes-and-structs/index.md#members), statické a nestatické, pokud jako ukazuje následující kód:

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

Můžete také použít `.` k přístupu [– metoda rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Indexer operator [].

Hranaté závorky, `[]`, se obvykle používají pro přístup k prvkům pole, indexovací člen nebo ukazatel.

### <a name="array-access"></a>Přístup k poli

Následující příklad ukazuje, jak přistupovat k prvkům pole:

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

Pokud pole indexu je mimo hranice odpovídající dimenze v poli, <xref:System.IndexOutOfRangeException> je vyvolána výjimka.

Jak ukazuje předchozí příklad, také použijete hranaté závorky při deklaraci typu pole nebo vytvoření instance pole instance.

Další informace o polích naleznete v tématu [pole](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Přístup indexeru

Následující příklad používá .NET <xref:System.Collections.Generic.Dictionary%602> typu k předvedení přístup indexeru:

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

Indexery umožňují index instance typu uživatelem definované v podobným způsobem jako indexování pole. Na rozdíl od indexy pole, které musí být celé číslo, mohou být deklarovány argumenty indexeru být libovolného typu.

Další informace o indexerech najdete v tématu [indexery](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Další použití]

Informace o přístup k prvkům ukazatel najdete v tématu [postupy: přístup k elementu pole pomocí ukazatele](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).

Můžete také použít hranaté závorky k určení [atributy](../../programming-guide/concepts/attributes/index.md):

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Podmíněné operátory s Null?. a? []

K dispozici v C# 6 nebo novější, platí null podmíněného operátoru přístupu ke členu `?.`, nebo přístup k prvkům `?[]`, operace svého operandu pouze v případě, že operand vyhodnocen jako jinou hodnotu než null. Pokud je operand vyhodnocen jako `null`, je výsledek použití operátoru `null`.

Podmíněné operátory s null jsou short-circuiting. To znamená, pokud jedna operace v řetězci Podmíněný člen nebo element přístup operace vrátí `null`, neprovede zbytek řetězce. V následujícím příkladu `B` není vyhodnocen, pokud `A` vyhodnotí jako `null` a `C` není vyhodnocen, pokud `A` nebo `B` vyhodnotí jako `null`:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Následující příklad ukazuje použití `?.` a `?[]` operátory:

[!code-csharp-interactive[null-conditional operators](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

Předchozí příklad také ukazuje využití [operátoru nulového sjednocení](null-coalescing-operator.md). Můžete použít poskytnout alternativní výraz k vyhodnocení v případě, že je výsledek operace null podmíněného operátoru nulového sjednocení `null`.

### <a name="thread-safe-delegate-invocation"></a>Volání delegáta bezpečným pro vlákno

Použití `?.` operátor pro kontrolu, pokud delegát je jiná než null a vyvolání způsobem bezpečným pro vlákno (například když je [vyvolat událost](../../../standard/events/how-to-raise-and-consume-events.md)), jak ukazuje následující kód:

```csharp
PropertyChanged?.Invoke(…)
```

Kód následující kód, který použijete v odpovídá C# 5 nebo starším systémem:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a>Operátor vyvolání)

Použít závorky, `()`, aby volal [metoda](../../programming-guide/classes-and-structs/methods.md) nebo vyvolat [delegovat](../../programming-guide/delegates/index.md).

Následující příklad ukazuje, jak volat metodu, s nebo bez argumentů a vyvolání delegáta:

[!code-csharp-interactive[invocation with ()](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

Můžete také použít závorky, při vyvolání [konstruktor](../../programming-guide/classes-and-structs/constructors.md) s [ `new` ](../keywords/new-operator.md) operátor.

### <a name="other-usages-of-"></a>Další využití)

Je také použít k určení pořadí, ve kterém se má vyhodnotit operací ve výrazu závorky. Další informace najdete v tématu [závorek](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) část [operátory](../../programming-guide/statements-expressions-operators/operators.md) článku. Seznam operátorů seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).

[Výrazy přetypování](invocation-operator.md#cast-expression), které vyvolat operátor převodu, také pomocí závorek.

## <a name="operator-overloadability"></a>Overloadability – operátor

`.` a `()` nemohou být přetíženy operátory. `[]` Operátor bude také považován za bez přetěžovatelný operátor. Použití [indexery](../../programming-guide/indexers/index.md) pro podporu indexování pomocí uživatelem definovaných typů.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Přístup ke členu](~/_csharplang/spec/expressions.md#member-access)
- [Přístup k prvkům](~/_csharplang/spec/expressions.md#element-access)
- [Null – podmíněný operátor](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Výrazy typu Invocation](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [?? (operátoru nulového sjednocení)](null-coalescing-operator.md)
