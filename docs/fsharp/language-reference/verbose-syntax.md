---
title: Podrobná syntaxe
description: Informace o rozdílu mezi podrobné a jednoduché syntaxi F# programovací jazyk.
ms.date: 05/16/2016
ms.openlocfilehash: c770f2843276619cb2878198a537dcfb9c054b6b
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613782"
---
# <a name="verbose-syntax"></a><span data-ttu-id="59f34-103">Podrobná syntaxe</span><span class="sxs-lookup"><span data-stu-id="59f34-103">Verbose Syntax</span></span>

<span data-ttu-id="59f34-104">Nejsou k dispozici pro mnoho konstrukcí v dvě formy syntaxe F# jazyka: *podrobná syntaxe* a *nenáročném syntaxi*.</span><span class="sxs-lookup"><span data-stu-id="59f34-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="59f34-105">Podrobná syntaxe nepoužívá tak často, ale nabízí výhodu v podobě jsou méně citlivé na odsazení.</span><span class="sxs-lookup"><span data-stu-id="59f34-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="59f34-106">Prostá syntaxe je kratší a používá odsazení který signalizuje, že začátku a konce konstrukce, spíše než další klíčová slova, jako jsou `begin`, `end`, `in`, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="59f34-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="59f34-107">Výchozí syntaxe je nenáročném syntaxi.</span><span class="sxs-lookup"><span data-stu-id="59f34-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="59f34-108">Toto téma popisuje syntaxi pro F# vytvoří, pokud není povolené nenáročném syntaxi.</span><span class="sxs-lookup"><span data-stu-id="59f34-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="59f34-109">Podrobná syntaxe je vždy povolena, tak i v případě, že povolíte nenáročném syntaxi, můžete stále použít podrobné syntaxi pro některé konstruktory.</span><span class="sxs-lookup"><span data-stu-id="59f34-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="59f34-110">Prostá syntaxe můžete zakázat s použitím `#light "off"` směrnice.</span><span class="sxs-lookup"><span data-stu-id="59f34-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="59f34-111">Tabulka konstrukce</span><span class="sxs-lookup"><span data-stu-id="59f34-111">Table of Constructs</span></span>

<span data-ttu-id="59f34-112">Následující tabulka ukazuje jednoduchý a podrobné syntaxe F# jazykové konstrukce v kontextech tam, kde existuje rozdíl mezi dvě různými formami.</span><span class="sxs-lookup"><span data-stu-id="59f34-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="59f34-113">V této tabulce úhel hranaté závorky (&lt;&gt;) uzavřete syntaxe uživatelem zadané elementy.</span><span class="sxs-lookup"><span data-stu-id="59f34-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="59f34-114">Naleznete v dokumentaci pro každý konstrukce jazyka podrobnější informace o syntaxi použít v rámci těchto konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="59f34-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="59f34-115">Konstrukce jazyka</span><span class="sxs-lookup"><span data-stu-id="59f34-115">Language construct</span></span></th>
<th><span data-ttu-id="59f34-116">Prostá syntaxe</span><span class="sxs-lookup"><span data-stu-id="59f34-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="59f34-117">Podrobná syntaxe</span><span class="sxs-lookup"><span data-stu-id="59f34-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="59f34-118">složené výrazy</span><span class="sxs-lookup"><span data-stu-id="59f34-118">compound expressions</span></span>
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

<span data-ttu-id="59f34-119">vnořené `let` vazby</span><span class="sxs-lookup"><span data-stu-id="59f34-119">nested `let` bindings</span></span>

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
<span data-ttu-id="59f34-120">blok kódu</span><span class="sxs-lookup"><span data-stu-id="59f34-120">code block</span></span>
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
<tr><td><span data-ttu-id="59f34-121">record</span><span class="sxs-lookup"><span data-stu-id="59f34-121">record</span></span>
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
<tr><td><span data-ttu-id="59f34-122">třída</span><span class="sxs-lookup"><span data-stu-id="59f34-122">class</span></span>
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
<tr><td><span data-ttu-id="59f34-123">– struktura</span><span class="sxs-lookup"><span data-stu-id="59f34-123">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="59f34-124">rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="59f34-124">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="59f34-125">rozhraní</span><span class="sxs-lookup"><span data-stu-id="59f34-125">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="59f34-126">výraz objektu</span><span class="sxs-lookup"><span data-stu-id="59f34-126">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="59f34-127">implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="59f34-127">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="59f34-128">Type – rozšíření</span><span class="sxs-lookup"><span data-stu-id="59f34-128">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="59f34-129">module</span><span class="sxs-lookup"><span data-stu-id="59f34-129">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="59f34-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59f34-130">See also</span></span>

- [<span data-ttu-id="59f34-131">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="59f34-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="59f34-132">Direktivy kompilátoru</span><span class="sxs-lookup"><span data-stu-id="59f34-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="59f34-133">Pravidla formátování kódu</span><span class="sxs-lookup"><span data-stu-id="59f34-133">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)