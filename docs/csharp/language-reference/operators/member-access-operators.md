---
title: Operátory přístupu členů a výrazy – odkaz jazyka C#
description: Další informace o operátory Jazyka C#, které můžete použít pro přístup k členům typu.
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
ms.openlocfilehash: da2ca4517bd007678d74ae9b76e10cad4c2696b4
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546637"
---
# <a name="member-access-operators-and-expressions-c-reference"></a>Operátory přístupu k členům a výrazy (odkaz C#)

Při přístupu k členu typu můžete použít následující operátory a výrazy:

- (členský přístup) : přístup k členovi oboru názvů nebo typu [ `.` ](#member-access-expression-)
- [(element pole nebo přístup k indexeru): pro přístup k prvku pole nebo indexeru typu `[]` ](#indexer-operator-)
- [a `?[]` (operátory s nulovým podmíněným podmínkou): provádět operaci přístupu k členu nebo prvku pouze v případě, že operand není `?.` ](#null-conditional-operators--and-)null
- (vyvolání) : volání přístupné metody nebo vyvolání delegáta [ `()` ](#invocation-expression-)
- (index od konce): označuje, že pozice prvku je od konce sekvence [ `^` ](#index-from-end-operator-)
- (rozsah) : určení rozsahu indexů, které můžete použít k získání rozsahu sekvenčních prvků [ `..` ](#range-operator-)

## <a name="member-access-expression-"></a>Výraz přístupu člena .

`.` Token se používá pro přístup k členu oboru názvů nebo typu, jak ukazují následující příklady:

- Slouží `.` k přístupu k vnořené oboru názvů v oboru názvů, jak ukazuje následující příklad [ `using` směrnice:](../keywords/using-directive.md)

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- Slouží `.` k vytvoření *kvalifikovaného názvu* pro přístup k typu v oboru názvů, jak ukazuje následující kód:

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  Použití [ `using` směrnice,](../keywords/using-directive.md) aby bylo použití kvalifikovaných názvů volitelné.

- Slouží `.` k přístupu k [členům typu](../../programming-guide/classes-and-structs/index.md#members), statickým a nestatickým, jak ukazuje následující kód:

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

Můžete také `.` použít pro přístup k [metodě rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Operátor indexeru []

Hranaté `[]`závorky , , se obvykle používají pro přístup k polím, indexeru nebo elementu ukazatele.

### <a name="array-access"></a>Přístup k poli

Následující příklad ukazuje, jak získat přístup k prvkům pole:

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

Pokud index pole je mimo hranice odpovídající dimenze pole, <xref:System.IndexOutOfRangeException> je vyvolána.

Jak ukazuje předchozí příklad, čtvercové závorky použijete také při deklarování typu pole nebo instance instance pole.

Další informace o polích naleznete v [tématu Arrays](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Přístup k indexeru

Následující příklad používá typ <xref:System.Collections.Generic.Dictionary%602> .NET k demonstraci přístupu indexeru:

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

Indexery umožňují indexovat instance uživatelem definovaného typu podobným způsobem jako indexování polí. Na rozdíl od indexů pole, které musí být celé číslo, parametry indexeru mohou být deklarovány jako libovolného typu.

Další informace o indexerech naleznete v tématu [Indexery](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Jiné použití []

Informace o přístupu k elementu ukazatele naleznete v části [Operátor přístupu elementu ukazatele []](pointer-related-operators.md#pointer-element-access-operator-) v článku [Operátory související s ukazatelem.](pointer-related-operators.md)

K určení [atributů](../../programming-guide/concepts/attributes/index.md)se také používají hranatá závorka :

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Operátory s nulovým podmíněným podmínkami?. A? []

K dispozici v C# 6 a novější, operátor s `?.`nulovou podmíněnou podmínkou použije přístup [člena](#member-access-expression-), nebo přístup k [elementu](#indexer-operator-), `?[]`, operace na jeho operand pouze v případě, že operand vyhodnotí na non-null; v opačném `null`případě vrátí . To je

- Pokud `a` je `null`vyhodnocena `a?.x` `a?[x]` , `null`výsledek nebo je .
- Pokud `a` je vyhodnocena na `a?.x` non-null, výsledek `a?[x]` nebo `a.x` `a[x]`je stejný jako výsledek nebo , v uvedeném pořadí.

  > [!NOTE]
  > Pokud `a.x` `a[x]` nebo vyvolá výjimku nebo `a?.x` `a?[x]` by vyvolat stejnou `a`výjimku pro non-null . Například pokud `a` je non-null pole `x` instance a je `a` `a?[x]` mimo hranice <xref:System.IndexOutOfRangeException>, by vyvolat .

Operátory s nulovým podmíněným podmínkami zkratují. To znamená, že pokud jedna operace v řetězci `null`operace přístupu podmíněného člena nebo prvku vrátí , zbytek řetězce neprovede. V následujícím `B` příkladu není `A` vyhodnocena, `null` pokud je vyhodnocena `C` a není vyhodnocena, pokud `A` nebo `B` vyhodnocuje na `null`:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Následující příklad ukazuje použití `?.` a `?[]` operátory:

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

Předchozí příklad také používá [operátor `??` null-coalescing](null-coalescing-operator.md) k určení alternativního výrazu k vyhodnocení v `null`případě, že výsledek operace s nulovou podmínkou je .

Operátor `?.` přístupu podmíněného člena null je také označován jako operátor Elvis.

### <a name="thread-safe-delegate-invocation"></a>Vyvolání delegáta bezpečného pro přístup z více vláken

Pomocí `?.` operátoru zkontrolujte, zda delegát není null a vyvolat jej způsobem bezpečným pro přístup z více vláken (například při [vyvolání události](../../../standard/events/how-to-raise-and-consume-events.md)), jak ukazuje následující kód:

```csharp
PropertyChanged?.Invoke(…)
```

Tento kód je ekvivalentní následující kód, který byste použili v C # 5 nebo starší:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-expression-"></a>Výraz vyvolání ()

Pomocí závorek `()`, můžete volat [metodu](../../programming-guide/classes-and-structs/methods.md) nebo vyvolat [delegáta](../../programming-guide/delegates/index.md).

Následující příklad ukazuje, jak volat metodu, s argumenty nebo bez argumentů a vyvolat delegáta:

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

Závorky můžete také použít při vyvolání [`new`](new-operator.md) [konstruktoru](../../programming-guide/classes-and-structs/constructors.md) s operátorem.

### <a name="other-usages-of-"></a>Ostatní použití ()

Závorky můžete také použít k úpravě pořadí, ve kterém chcete vyhodnotit operace ve výrazu. Další informace naleznete v tématu [C# operátory](index.md).

[Výrazy přetypování](type-testing-and-cast.md#cast-operator-), které provádějí explicitní převody typů, také používají závorky.

## <a name="index-from-end-operator-"></a>Index od koncového operátora ^

K dispozici v C# 8.0 a novější, `^` operátor označuje pozici prvku od konce sekvence. Pro posloupnost `length` `^n` délky odkazuje na `length - n` prvek s posunem od začátku sekvence. Například `^1` odkazuje na poslední prvek sekvence `^length` a odkazuje na první prvek sekvence.

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

Jak ukazuje předchozí příklad, `^e` výraz <xref:System.Index?displayProperty=nameWithType> je typu. Ve `^e`výrazu `e` musí být výsledek implicitně převoditelný na `int`.

Můžete také použít `^` operátor s [operátorem rozsahu](#range-operator-) k vytvoření rozsahu indexů. Další informace naleznete [v tématu Indexy a rozsahy](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Operátor rozsahu ..

K dispozici v C# 8.0 a `..` novější, operátor určuje začátek a konec rozsahu indexů jako jeho operandy. Levostranný operand je *včetně* začátku řady. Pravostranný operand je *exkluzivní* konec řady. Buď operandy může být index od začátku nebo od konce sekvence, jak ukazuje následující příklad:

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

Jak ukazuje předchozí příklad, `a..b` výraz <xref:System.Range?displayProperty=nameWithType> je typu. Ve `a..b`výrazu musí `a` `b` být výsledky a `int` musí <xref:System.Index>být implicitně převoditelné na nebo .

Můžete vynechat některý z operandů operátoru `..` a získat tak otevřený rozsah:

- `a..`je ekvivalentní`a..^0`
- `..b`je ekvivalentní`0..b`
- `..`je ekvivalentní`0..^0`

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

Další informace naleznete [v tématu Indexy a rozsahy](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Přetížení obsluhy

V `.` `()`, `^`, `..` a operátory nelze přetíženy. Operátor `[]` je také považován za nepřetížený operátor. [Indexery](../../programming-guide/indexers/index.md) slouží k podpoře indexování s typy definovanými uživatelem.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Přístup členů](~/_csharplang/spec/expressions.md#member-access)
- [Přístup k prvkům](~/_csharplang/spec/expressions.md#element-access)
- [Operátor s nulovým podmíněným podmínkou](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Výrazy vyvolání](~/_csharplang/spec/expressions.md#invocation-expressions)

Další informace o indexech a rozsahech naleznete v [poznámce k návrhu funkce](~/_csharplang/proposals/csharp-8.0/ranges.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [?? (operátor null-coalescing)](null-coalescing-operator.md)
- [:: operátor](namespace-alias-qualifier.md)
