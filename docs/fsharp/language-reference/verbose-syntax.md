---
title: Podrobná syntaxe (F#)
description: 'Informace o rozdílu mezi syntaxi podrobné a jednoduchý programovací jazyk F #.'
ms.date: 05/16/2016
ms.openlocfilehash: e697c6fe619df7ffe12f7d4e2a234a5a5cb401ff
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50044760"
---
# <a name="verbose-syntax"></a>Podrobná syntaxe

Pro mnoho konstrukcí v jazyce F # existují dvě formy syntaxe: *podrobná syntaxe* a *nenáročném syntaxi*. Podrobná syntaxe nepoužívá tak často, ale nabízí výhodu v podobě jsou méně citlivé na odsazení. Prostá syntaxe je kratší a používá odsazení který signalizuje, že začátku a konce konstrukce, spíše než další klíčová slova, jako jsou `begin`, `end`, `in`, a tak dále. Výchozí syntaxe je nenáročném syntaxi. Toto téma popisuje syntaxe konstrukce jazyka F #, pokud není povolené nenáročném syntaxi. Podrobná syntaxe je vždy povolena, tak i v případě, že povolíte nenáročném syntaxi, můžete stále použít podrobné syntaxi pro některé konstruktory. Prostá syntaxe můžete zakázat s použitím `#light "off"` směrnice.

## <a name="table-of-constructs"></a>Tabulka konstrukce

Následující tabulka ukazuje jednoduchý a podrobné syntaxe konstrukce jazyka F # v kontextech tam, kde existuje rozdíl mezi dvě různými formami. V této tabulce úhel hranaté závorky (&lt;&gt;) uzavřete syntaxe uživatelem zadané elementy. Naleznete v dokumentaci pro každý konstrukce jazyka podrobnější informace o syntaxi použít v rámci těchto konstruktorů.

<table>
<tr>
<th>Konstrukce jazyka</th>
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

```
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
<tr><td>rozlišovaná sjednocení</td><td>

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
<tr><td>Type – rozšíření</td><td>

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
