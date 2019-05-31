---
title: Hodnota typu – C# odkaz
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: af3eab1c2453f37aa5bd881dc9804d7504c89298
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422117"
---
# <a name="value-types-c-reference"></a>Typy hodnot (C# odkaz)

Existují dva druhy typů hodnot:

- [Struktury](struct.md)

- [Výčty](enum.md)

## <a name="main-features-of-value-types"></a>Hlavní funkce typů hodnot

Proměnné hodnotového typu obsahuje hodnotu typu. Například proměnná `int` typ může obsahovat hodnotu `42`. Tím se liší od proměnné typu odkazu, který obsahuje odkaz na instanci typu, označované také jako objekt. Když přiřadí novou hodnotu do proměnné typu hodnoty, tato hodnota je zkopírována. Když se přiřadí novou hodnotu do proměnné typu odkazu, odkaz je zkopírován, nikoli samotného objektu.

Všechny hodnotové typy jsou implicitně odvozena z <xref:System.ValueType?displayProperty=nameWithType>.

Na rozdíl od v případě typů odkazu nelze odvodit nový typ z typu hodnoty. Nicméně, jako jsou typy odkazů, struktury mohou implementovat rozhraní.

Hodnoty typových proměnných nesmí být `null` ve výchozím nastavení. Ale proměnné k odpovídající položce [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md) může být `null`.

Každý hodnotový typ má implicitní konstruktor bez parametrů, která inicializuje výchozí hodnota tohoto typu. Informace o výchozí hodnoty typů hodnot najdete v tématu [tabulka výchozích hodnot](default-values-table.md).

## <a name="simple-types"></a>Jednoduché typy

*Jednoduché typy* představují sadu předdefinovaných struktury typy poskytované C# a zahrnuje následující typy:

- [Integrální typy](integral-types-table.md): číselné typy celých čísel a [char](char.md) typu
- [Typy s plovoucí desetinnou čárkou](floating-point-types-table.md)
- [bool](bool.md)

Jednoduché typy jsou označeny pomocí klíčových slov, ale tato klíčová slova jsou pouze aliasy pro typy předdefinované struktury v <xref:System> oboru názvů. Například [int](int.md) je alias pro <xref:System.Int32?displayProperty=nameWithType>. Úplný seznam aliasů naleznete v tématu [tabulka předdefinovaných typů](built-in-types-table.md).

Jednoduché typy liší od jiné typy struct, že umožňují některé další operace:

- Jednoduché typy může být inicializována pomocí literálů. Například `'A'` je literál typu `char` a `2001` je literál typu `int`.

- Je možné deklarovat konstanty jednoduché typy s [const](const.md) – klíčové slovo. Není možné mít konstanty jiné typy struct.

- Výrazy konstant, jehož operandy jsou všechny jednoduchý typ konstanty, jsou vyhodnocovány v době kompilace.

Další informace najdete v tématu [jednoduché typy](~/_csharplang/spec/types.md#simple-types) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="initializing-value-types"></a>Inicializace typů hodnot

Lokální proměnné v jazyce C# musí být inicializován před jejich použití. Například může prohlásit místní proměnné bez inicializace jako v následujícím příkladu:

```csharp
int myInt;
```

Nelze ji použít předtím, než ji inicializovat. Můžete inicializovat pomocí následujícího příkazu:

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

Tento příkaz je ekvivalentem následujícího příkazu:

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

Můžete samozřejmě máte deklaraci a inicializaci ve stejném příkazu jako v následujících příkladech:

```csharp
int myInt = new int();
```

– nebo –

```csharp
int myInt = 0;
```

Použití [nové](new.md) operátor volá konstruktor určitého typu a přiřadí výchozí hodnotu proměnné. V předchozím příkladu konstruktor bez parametrů přiřazena hodnota `0` k `myInt`. Další informace o hodnoty přiřazené voláním výchozí konstruktory, naleznete v tématu [tabulka výchozích hodnot](default-values-table.md).

Pomocí uživatelem definované typy [nové](new.md) vyvolat konstruktor bez parametrů. Například následující příkaz volá konstruktor bez parametrů `Point` struktury:

```csharp
Point p = new Point(); // Invoke parameterless constructor for the struct.
```

Po tomto volání struktury považuje je jednoznačně přiřazovat; To znamená všech jejích členů jsou inicializovány na výchozích hodnotách.

Další informace o `new` operátoru, naleznete v tématu [nové](new.md).

Informace o formátování výstupu číselné typy najdete v tématu [tabulka formátování číselných výsledků](formatting-numeric-results-table.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Typy](types.md)
- [Odkazové typy](reference-types.md)
- [Typy s možnou hodnotou Null](../../programming-guide/nullable-types/index.md)
