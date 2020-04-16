---
title: Podrobná syntaxe
description: Naučte se rozdíl mezi podrobnou a zjednodušenou syntaxí v programovacím jazyce F#.
ms.date: 05/16/2016
ms.openlocfilehash: 722807695c56beb0d681b95a78ed8cb8c1df3ddf
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463909"
---
# <a name="verbose-syntax"></a>Podrobná syntaxe

Pro mnoho konstrukcí v jazyce F# jsou k dispozici dvě formy syntaxe: *syntaxe podrobné* a *zjednodušené syntaxe*. Syntaxe podrobné není tak běžně používaná, ale má tu výhodu, že je méně citlivá na odsazení. Zjednodušená syntaxe je kratší a používá odsazení k signalizaci `begin`začátku a konce konstrukcí, nikoli dalších klíčových slov, jako je , `end`, `in`a tak dále. Výchozí syntaxe je zjednodušená syntaxe. Toto téma popisuje syntaxi pro konstrukce Jazyka F#, pokud není povolena zjednodušená syntaxe. Podrobná syntaxe je vždy povolena, takže i když povolíte zjednodušenou syntaxi, můžete pro některé konstrukce stále používat podrobnou syntaxi. Můžete zakázat zjednodušenou `#light "off"` syntaxi pomocí směrnice.

## <a name="table-of-constructs"></a>Tabulka konstrukcí

V následující tabulce je uvedena zjednodušená a podrobná syntaxe pro konstrukce jazyka F# v kontextech, kde je rozdíl mezi těmito dvěma formami. V této tabulce úhlové&lt;&gt;závorky ( ) uzavřete uživatelem zadané syntaktické prvky. Podrobnější informace o syntaxi použité v rámci těchto konstrukcí naleznete v dokumentaci pro každý návrh jazyka.

<table>
<tr>
<th>Konstrukce jazyka</th>
<th>Odlehčená syntaxe</th>
<th>Podrobná syntaxe</th>
</tr>
<tr>
<td>
složené výrazy
</td>
<td>

```xml
<expression1 />
<expression2 />
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
<tr><td>Záznam
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
<tr><td>diskriminované unie</td><td>

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
<tr><td>rozšíření typu</td><td>

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

## <a name="see-also"></a>Viz také

- [Referenční příručka jazyka F#](index.md)
- [Direktivy kompilátoru](compiler-directives.md)
- [Pravidla formátování kódu](../style-guide/formatting.md)
