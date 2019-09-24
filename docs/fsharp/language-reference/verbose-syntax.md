---
title: Podrobná syntaxe
description: Přečtěte si rozdíl mezi podrobnými a nezjednodušenou F# syntaxí v programovacím jazyce.
ms.date: 05/16/2016
ms.openlocfilehash: d2459da60bba5d88bd23615c8bf09ba64f7c22c4
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214033"
---
# <a name="verbose-syntax"></a>Podrobná syntaxe

K dispozici jsou dvě formy syntaxe pro mnoho konstrukcí v F# jazyce: *verbose syntaxe* a *prostá syntaxe*. Podrobná syntaxe není tak, jak se běžně používá, ale má výhodu, že je méně citlivá na odsazení. Zjednodušená syntaxe je kratší a používá odsazení k signalizaci začátku a konce konstrukcí, spíše než další klíčová slova jako `begin`, `end`, `in`a tak dále. Výchozí syntaxí je zjednodušená syntaxe. Toto téma popisuje syntaxi pro F# konstrukce, pokud není povolena zjednodušená syntaxe. Podrobná syntaxe je vždy povolena, takže i v případě, že povolíte zjednodušenou syntaxi, můžete pro některé konstrukty stále používat syntaxi verbose. Pomocí `#light "off"` direktivy můžete zakázat zjednodušenou syntaxi.

## <a name="table-of-constructs"></a>Tabulka konstrukcí

Následující tabulka uvádí zjednodušenou a podrobnou syntaxi pro F# jazykové konstrukce v kontextech, kde existuje rozdíl mezi dvěma formuláři. V této tabulce jsou uvedené lomené&lt;závorky (&gt;) ohraničující uživatelsky zadané prvky syntaxe. Podrobnější informace o syntaxi používané v rámci těchto konstrukcí naleznete v dokumentaci k jednotlivým jazykovým konstrukcím.

<table>
<tr>
<th>Jazyková konstrukce</th>
<th>Prostá syntaxe</th>
<th>Podrobná syntaxe</th>
</tr>
<tr>
<td>
složené výrazy
</td>
<td>

```xml
<expression1>
<expression2>
```

</td><td>

```fsharp
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>

vnořené `let` vazby

</td><td>

```fsharp
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```fsharp
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
blok kódu
</td><td>

```fsharp
(
    <expression1>
    <expression2>
)
```

</td><td>

```fsharp
begin
    <expression1>;
    <expression2>;
end
```

</td>
</tr>
<tr><td>
`for...do`
</td><td>

```fsharp
for counter = start to finish do
    ...
```

</td><td>

```fsharp
for counter = start to finish do
    ...
done
```

</td>
</tr>
<tr><td>
`while...do`
</td><td>

```fsharp
while <condition> do
    ...
```

</td><td>

```fsharp
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```fsharp
for var in start .. finish do
    ...
```

</td><td>

```fsharp
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```fsharp
do
    ...
```

</td><td>

```fsharp
do
    ...
in
```

</td>
</tr>
<tr><td>record
</td><td>

```fsharp
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```fsharp
type <record-name> =
    {
        <field-declarations>
    }
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>třída
</td><td>

```fsharp
type <class-name>(<params>) =
    ...
```

</td><td>

```fsharp
type <class-name>(<params>) =
    class
        ...
    end
```

</td>
</tr>
<tr><td>– struktura</td><td>

```fsharp
[<StructAttribute>]
type <structure-name> =
    ...
```

</td><td>

```fsharp
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td>rozlišené sjednocení</td><td>

```fsharp
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```

</td><td>

```fsharp
type <union-name> =
    | ...
    | ...
    ...
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>rozhraní</td><td>

```fsharp
type <interface-name> =
    ...
```

</td><td>

```fsharp
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td>výraz objektu</td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td>implementace rozhraní</td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>Přípona typu</td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>module</td><td>

```fsharp
module <module-name> =
    ...
```

</td><td>

```fsharp
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Direktivy kompilátoru](compiler-directives.md)
- [Pravidla formátování kódu](code-formatting-guidelines.md)
