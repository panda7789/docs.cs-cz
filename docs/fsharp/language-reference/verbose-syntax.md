---
title: Podrobná syntaxe (F#)
description: 'Informace o rozdílu mezi syntaxi podrobné a jednoduchý programovací jazyk F #.'
ms.date: 05/16/2016
ms.openlocfilehash: b4f2354738da4692cb444e5e7dd9531d80d26664
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45647132"
---
# <a name="verbose-syntax"></a><span data-ttu-id="912a7-103">Podrobná syntaxe</span><span class="sxs-lookup"><span data-stu-id="912a7-103">Verbose Syntax</span></span>

<span data-ttu-id="912a7-104">Pro mnoho konstrukcí v jazyce F # existují dvě formy syntaxe: *podrobná syntaxe* a *nenáročném syntaxi*.</span><span class="sxs-lookup"><span data-stu-id="912a7-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="912a7-105">Podrobná syntaxe nepoužívá tak často, ale nabízí výhodu v podobě jsou méně citlivé na odsazení.</span><span class="sxs-lookup"><span data-stu-id="912a7-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="912a7-106">Prostá syntaxe je kratší a používá odsazení který signalizuje, že začátku a konce konstrukce, spíše než další klíčová slova, jako jsou `begin`, `end`, `in`, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="912a7-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="912a7-107">Výchozí syntaxe je nenáročném syntaxi.</span><span class="sxs-lookup"><span data-stu-id="912a7-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="912a7-108">Toto téma popisuje syntaxe konstrukce jazyka F #, pokud není povolené nenáročném syntaxi.</span><span class="sxs-lookup"><span data-stu-id="912a7-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="912a7-109">Podrobná syntaxe je vždy povolena, tak i v případě, že povolíte nenáročném syntaxi, můžete stále použít podrobné syntaxi pro některé konstruktory.</span><span class="sxs-lookup"><span data-stu-id="912a7-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="912a7-110">Prostá syntaxe můžete zakázat s použitím `#light "off"` směrnice.</span><span class="sxs-lookup"><span data-stu-id="912a7-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="912a7-111">Tabulka konstrukce</span><span class="sxs-lookup"><span data-stu-id="912a7-111">Table of Constructs</span></span>

<span data-ttu-id="912a7-112">Následující tabulka ukazuje jednoduchý a podrobné syntaxe konstrukce jazyka F # v kontextech tam, kde existuje rozdíl mezi dvě různými formami.</span><span class="sxs-lookup"><span data-stu-id="912a7-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="912a7-113">V této tabulce úhel hranaté závorky (&lt;&gt;) uzavřete syntaxe uživatelem zadané elementy.</span><span class="sxs-lookup"><span data-stu-id="912a7-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="912a7-114">Naleznete v dokumentaci pro každý konstrukce jazyka podrobnější informace o syntaxi použít v rámci těchto konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="912a7-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="912a7-115">Konstrukce jazyka</span><span class="sxs-lookup"><span data-stu-id="912a7-115">Language construct</span></span></th>
<th><span data-ttu-id="912a7-116">Prostá syntaxe</span><span class="sxs-lookup"><span data-stu-id="912a7-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="912a7-117">Podrobná syntaxe</span><span class="sxs-lookup"><span data-stu-id="912a7-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="912a7-118">složené výrazy</span><span class="sxs-lookup"><span data-stu-id="912a7-118">compound expressions</span></span>
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


<span data-ttu-id="912a7-119">vnořené `let` vazby</span><span class="sxs-lookup"><span data-stu-id="912a7-119">nested `let` bindings</span></span>

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
<span data-ttu-id="912a7-120">blok kódu</span><span class="sxs-lookup"><span data-stu-id="912a7-120">code block</span></span>
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
<tr><td><span data-ttu-id="912a7-121">Záznam</span><span class="sxs-lookup"><span data-stu-id="912a7-121">record</span></span>
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
<tr><td><span data-ttu-id="912a7-122">třída</span><span class="sxs-lookup"><span data-stu-id="912a7-122">class</span></span>
</td><td><span data-ttu-id="912a7-123">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="912a7-123">
```
type <class-name>(<params>) = ... ```

</span></span></td><td>

```
type <class-name>(<params>) =
    class
        ...
    end
```
</td>
</tr>
<tr><td><span data-ttu-id="912a7-124">– struktura</span><span class="sxs-lookup"><span data-stu-id="912a7-124">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="912a7-125">rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="912a7-125">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="912a7-126">rozhraní</span><span class="sxs-lookup"><span data-stu-id="912a7-126">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="912a7-127">výraz objektu</span><span class="sxs-lookup"><span data-stu-id="912a7-127">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="912a7-128">implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="912a7-128">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="912a7-129">Type – rozšíření</span><span class="sxs-lookup"><span data-stu-id="912a7-129">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="912a7-130">module</span><span class="sxs-lookup"><span data-stu-id="912a7-130">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="912a7-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="912a7-131">See also</span></span>

- [<span data-ttu-id="912a7-132">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="912a7-132">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="912a7-133">Direktivy kompilátoru</span><span class="sxs-lookup"><span data-stu-id="912a7-133">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="912a7-134">Pravidla formátování kódu</span><span class="sxs-lookup"><span data-stu-id="912a7-134">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
