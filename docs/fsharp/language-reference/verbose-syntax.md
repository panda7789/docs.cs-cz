---
title: Podrobná syntaxe (F#)
description: 'Informace o rozdílu mezi podrobné a jednoduchý syntaxe v programovací jazyk F #.'
ms.date: 05/16/2016
ms.openlocfilehash: b0bed66b4a76c5ab11e6c9e7aaf695f864e74ca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="verbose-syntax"></a>Podrobná syntaxe

Nejsou k dispozici pro mnoho konstrukce v jazyce F # dvě formy syntaxe: *podrobná syntaxe* a *prostá syntaxe*. Podrobná syntaxe není jako běžně používá, ale nabízí výhodu v podobě méně citlivé na odsazení. Prostá syntaxe je kratší a používá odsazení signál začátek a konec konstrukce, nikoli jako další klíčová slova `begin`, `end`, `in`a tak dále. Výchozí syntaxe je prostá syntaxe. Toto téma popisuje syntaxe konstrukce jazyka F #, není-li povoleno prostá syntaxe. Podrobná syntaxe je vždy povolena, tak i v případě, že povolíte prostá syntaxe, když můžete nadále používat podrobná syntaxe pro některé konstruktory. Prostá syntaxe můžete zakázat pomocí `#light "off"` – direktiva.


## <a name="table-of-constructs"></a>Tabulka konstrukce
Následující tabulka ukazuje jednoduchý a podrobné syntaxi pro konstruktory jazyka F # v kontextech tam, kde je rozdíl mezi dvěma formuláři. V této tabulce, úhel závorky (&lt;&gt;) uzavřete prvky uživatelem zadané syntaxe. Naleznete v dokumentaci pro každý jazyk konstrukce pro podrobnější informace o syntaxi používaných v rámci těchto konstrukce.



<table>
<tr>
<th>Jazyk – konstrukce</th>
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

```
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>


vnořené `let` vazby

</td><td>
```
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```
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

```
(
    <expression1>
    <expression2>
)
```

</td><td>

```
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

```
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

```
while <condition> do
    ...
```

</td><td>

```
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```
for var in start .. finish do
    ...
```

</td><td>

```
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```
do
    ...
```

</td><td>

```
do
    ...
in
```

</td>
</tr>
<tr><td>záznam
</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```
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
```
type <class-name>(<params>) = ... ```

</td><td>

```
type <class-name>(<params>) =
    class
        ...
    end
```
</td>
</tr>
<tr><td>– struktura</td><td>

```
[<StructAttribute>]
type <structure-name> =
    ...
```
</td><td>

```
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td>rozlišovaná sjednocení</td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```
</td><td>

```
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

```
type <interface-name> =
    ...
```
</td><td>

```
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td>objekt výraz</td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```
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

```
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>Type – rozšíření</td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>module</td><td>

```
module <module-name> =
    ...
```

</td><td>

```
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>



## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Direktivy kompilátoru](compiler-directives.md)

[Pravidla formátování kódu](code-formatting-guidelines.md)
