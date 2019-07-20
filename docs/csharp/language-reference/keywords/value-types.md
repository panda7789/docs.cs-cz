---
title: Typy hodnot – C# referenční informace
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 72771ee494b6be7142ce3f9bec43dcb8aa8a8401
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363081"
---
# <a name="value-types-c-reference"></a>Typy hodnot (C# referenční)

Existují dva druhy typů hodnot:

- [Struktury](struct.md)

- [Výčty](enum.md)

## <a name="main-features-of-value-types"></a>Hlavní funkce typů hodnot

Proměnná typu hodnoty obsahuje hodnotu typu. Například proměnná `int` typu může obsahovat hodnotu `42`. To se liší od proměnné typu odkazu, který obsahuje odkaz na instanci typu, označovanou také jako objekt. Pokud přiřadíte novou hodnotu proměnné typu hodnoty, je tato hodnota zkopírována. Pokud přiřadíte novou hodnotu proměnné typu odkazu, je odkaz zkopírován, nikoli samotný objekt.

Všechny typy hodnot jsou implicitně odvozeny z <xref:System.ValueType?displayProperty=nameWithType>.

Na rozdíl od typů odkazů nemůžete odvodit nový typ z hodnotového typu. Nicméně, podobně jako typy odkazů, struktury mohou implementovat rozhraní.

Proměnné typu hodnoty nemůžou `null` být ve výchozím nastavení. Proměnné odpovídajícího typu s možnou [hodnotou null](../../../csharp/programming-guide/nullable-types/index.md) ale mohou `null`být.

Každý typ hodnoty má implicitní konstruktor bez parametrů, který inicializuje výchozí hodnotu tohoto typu. Informace o výchozích hodnotách hodnotových typů najdete v [tabulce s výchozími hodnotami](default-values-table.md).

## <a name="simple-types"></a>Jednoduché typy

*Jednoduché typy* jsou množinou předdefinovaných typů struktury poskytovaných C# a tvořené následujícími typy:

- [Integrální typy](../builtin-types/integral-numeric-types.md): číselné typy integer a typ [znaku](char.md)
- [Typy s plovoucí desetinnou čárkou](../builtin-types/floating-point-numeric-types.md)
- [bool](bool.md)

Jednoduché typy jsou identifikovány pomocí klíčových slov, ale tato klíčová slova jsou jednoduše aliasy pro předdefinované <xref:System> typy struktury v oboru názvů. Například [int](../builtin-types/integral-numeric-types.md) je alias <xref:System.Int32?displayProperty=nameWithType>. Úplný seznam aliasů najdete v tématu [tabulka předdefinovaných typů](built-in-types-table.md).

Jednoduché typy se liší od jiných typů struktury v tom, že umožňují určité další operace:

- Jednoduché typy lze inicializovat pomocí literálů. Například je literál `'A'` `char` `int`typu, který je literálem typu. `2001`

- Můžete deklarovat konstanty jednoduchých typů pomocí klíčového slova [const](const.md) . Není možné mít konstanty jiných typů struktury.

- Výrazy konstant, jejichž operandy jsou všechny jednoduché konstanty typu, jsou vyhodnocovány v době kompilace.

Další informace naleznete v části [jednoduché typy](~/_csharplang/spec/types.md#simple-types) [ C# specifikace jazyka](../language-specification/index.md).

## <a name="initializing-value-types"></a>Inicializace typů hodnot

Místní proměnné v C# nástroji musí být před použitím inicializovány. Například je možné deklarovat místní proměnnou bez inicializace jako v následujícím příkladu:

```csharp
int myInt;
```

Nemůžete ho použít před inicializací. Můžete ji inicializovat pomocí následujícího příkazu:

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

Tento příkaz je ekvivalentní následujícímu příkazu:

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

Můžete samozřejmě mít deklaraci a inicializaci ve stejném příkazu jako v následujících příkladech:

```csharp
int myInt = new int();
```

ani

```csharp
int myInt = 0;
```

Použití operátoru [New](../operators/new-operator.md) volá konstruktor bez parametrů konkrétního typu a přiřadí výchozí hodnotu proměnné. V předchozím příkladu konstruktor bez parametrů přiřadí hodnotu `0` k. `myInt` Další informace o hodnotách, které jsou přiřazeny voláním konstruktorů bez parametrů, naleznete v [tabulce Default Values](default-values-table.md).

S uživatelsky definovanými typy použijte [Nový](../operators/new-operator.md) k vyvolání konstruktoru bez parametrů. Například následující příkaz vyvolá konstruktor `Point` bez parametrů struktury:

```csharp
var p = new Point(); // Invoke parameterless constructor for the struct.
```

Po tomto volání se struktura považuje za jednoznačně přiřazenou; To znamená, že všichni její členové jsou inicializováni na jejich výchozí hodnoty.

Další informace o `new` operátoru naleznete v tématu [New](../operators/new-operator.md).

Informace o formátování výstupu číselných typů najdete v tématu [formátování tabulky číselných výsledků](formatting-numeric-results-table.md).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Typy](types.md)
- [Odkazové typy](reference-types.md)
- [Typy s možnou hodnotou null](../../programming-guide/nullable-types/index.md)
