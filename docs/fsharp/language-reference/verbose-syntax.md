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
# <a name="verbose-syntax"></a><span data-ttu-id="ac1e1-103">Podrobná syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac1e1-103">Verbose Syntax</span></span>

<span data-ttu-id="ac1e1-104">Pro mnoho konstrukcí v jazyce F# jsou k dispozici dvě formy syntaxe: *syntaxe podrobné* a *zjednodušené syntaxe*.</span><span class="sxs-lookup"><span data-stu-id="ac1e1-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="ac1e1-105">Syntaxe podrobné není tak běžně používaná, ale má tu výhodu, že je méně citlivá na odsazení.</span><span class="sxs-lookup"><span data-stu-id="ac1e1-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="ac1e1-106">Zjednodušená syntaxe je kratší a používá odsazení k signalizaci `begin`začátku a konce konstrukcí, nikoli dalších klíčových slov, jako je , `end`, `in`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="ac1e1-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="ac1e1-107">Výchozí syntaxe je zjednodušená syntaxe.</span><span class="sxs-lookup"><span data-stu-id="ac1e1-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="ac1e1-108">Toto téma popisuje syntaxi pro konstrukce Jazyka F#, pokud není povolena zjednodušená syntaxe.</span><span class="sxs-lookup"><span data-stu-id="ac1e1-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="ac1e1-109">Podrobná syntaxe je vždy povolena, takže i když povolíte zjednodušenou syntaxi, můžete pro některé konstrukce stále používat podrobnou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="ac1e1-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="ac1e1-110">Můžete zakázat zjednodušenou `#light "off"` syntaxi pomocí směrnice.</span><span class="sxs-lookup"><span data-stu-id="ac1e1-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="ac1e1-111">Tabulka konstrukcí</span><span class="sxs-lookup"><span data-stu-id="ac1e1-111">Table of Constructs</span></span>

<span data-ttu-id="ac1e1-112">V následující tabulce je uvedena zjednodušená a podrobná syntaxe pro konstrukce jazyka F# v kontextech, kde je rozdíl mezi těmito dvěma formami.</span><span class="sxs-lookup"><span data-stu-id="ac1e1-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="ac1e1-113">V této tabulce úhlové&lt;&gt;závorky ( ) uzavřete uživatelem zadané syntaktické prvky.</span><span class="sxs-lookup"><span data-stu-id="ac1e1-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="ac1e1-114">Podrobnější informace o syntaxi použité v rámci těchto konstrukcí naleznete v dokumentaci pro každý návrh jazyka.</span><span class="sxs-lookup"><span data-stu-id="ac1e1-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="ac1e1-115">Konstrukce jazyka</span><span class="sxs-lookup"><span data-stu-id="ac1e1-115">Language construct</span></span></th>
<th><span data-ttu-id="ac1e1-116">Odlehčená syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac1e1-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="ac1e1-117">Podrobná syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac1e1-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="ac1e1-118">složené výrazy</span><span class="sxs-lookup"><span data-stu-id="ac1e1-118">compound expressions</span></span>
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

<span data-ttu-id="ac1e1-119">vnořené `let` vazby</span><span class="sxs-lookup"><span data-stu-id="ac1e1-119">nested `let` bindings</span></span>

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
<span data-ttu-id="ac1e1-120">blok kódu</span><span class="sxs-lookup"><span data-stu-id="ac1e1-120">code block</span></span>
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
<tr><td><span data-ttu-id="ac1e1-121">Záznam</span><span class="sxs-lookup"><span data-stu-id="ac1e1-121">record</span></span>
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
<tr><td><span data-ttu-id="ac1e1-122">třída</span><span class="sxs-lookup"><span data-stu-id="ac1e1-122">class</span></span>
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
<tr><td><span data-ttu-id="ac1e1-123">– struktura</span><span class="sxs-lookup"><span data-stu-id="ac1e1-123">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="ac1e1-124">diskriminované unie</span><span class="sxs-lookup"><span data-stu-id="ac1e1-124">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="ac1e1-125">rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac1e1-125">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="ac1e1-126">výraz objektu</span><span class="sxs-lookup"><span data-stu-id="ac1e1-126">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="ac1e1-127">implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac1e1-127">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="ac1e1-128">rozšíření typu</span><span class="sxs-lookup"><span data-stu-id="ac1e1-128">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="ac1e1-129">module</span><span class="sxs-lookup"><span data-stu-id="ac1e1-129">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="ac1e1-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac1e1-130">See also</span></span>

- [<span data-ttu-id="ac1e1-131">Referenční příručka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="ac1e1-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="ac1e1-132">Direktivy kompilátoru</span><span class="sxs-lookup"><span data-stu-id="ac1e1-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="ac1e1-133">Pravidla formátování kódu</span><span class="sxs-lookup"><span data-stu-id="ac1e1-133">Code Formatting Guidelines</span></span>](../style-guide/formatting.md)
