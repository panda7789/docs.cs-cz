---
title: Podrobná syntaxe
description: Přečtěte si rozdíl mezi podrobnými a nezjednodušenou F# syntaxí v programovacím jazyce.
ms.date: 05/16/2016
ms.openlocfilehash: 575585b201acc1366980cfc5cf523c4117259084
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421182"
---
# <a name="verbose-syntax"></a><span data-ttu-id="0a851-103">Podrobná syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a851-103">Verbose Syntax</span></span>

<span data-ttu-id="0a851-104">K dispozici jsou dvě formy syntaxe pro mnoho konstrukcí v F# jazyce: *verbose syntaxe* a *prostá syntaxe*.</span><span class="sxs-lookup"><span data-stu-id="0a851-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="0a851-105">Podrobná syntaxe není tak, jak se běžně používá, ale má výhodu, že je méně citlivá na odsazení.</span><span class="sxs-lookup"><span data-stu-id="0a851-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="0a851-106">Zjednodušená syntaxe je kratší a používá odsazení k signalizaci začátku a konce konstrukcí, spíše než další klíčová slova, jako je `begin`, `end`, `in`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="0a851-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="0a851-107">Výchozí syntaxí je zjednodušená syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0a851-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="0a851-108">Toto téma popisuje syntaxi pro F# konstrukce, pokud není povolena zjednodušená syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0a851-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="0a851-109">Podrobná syntaxe je vždy povolena, takže i v případě, že povolíte zjednodušenou syntaxi, můžete pro některé konstrukty stále používat syntaxi verbose.</span><span class="sxs-lookup"><span data-stu-id="0a851-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="0a851-110">Pomocí direktivy `#light "off"` můžete zakázat zjednodušenou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="0a851-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="0a851-111">Tabulka konstrukcí</span><span class="sxs-lookup"><span data-stu-id="0a851-111">Table of Constructs</span></span>

<span data-ttu-id="0a851-112">Následující tabulka uvádí zjednodušenou a podrobnou syntaxi pro F# jazykové konstrukce v kontextech, kde existuje rozdíl mezi dvěma formuláři.</span><span class="sxs-lookup"><span data-stu-id="0a851-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="0a851-113">V této tabulce jsou lomené závorky (&lt;&gt;) ohraničující uživatelsky zadané prvky syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0a851-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="0a851-114">Podrobnější informace o syntaxi používané v rámci těchto konstrukcí naleznete v dokumentaci k jednotlivým jazykovým konstrukcím.</span><span class="sxs-lookup"><span data-stu-id="0a851-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="0a851-115">Jazyková konstrukce</span><span class="sxs-lookup"><span data-stu-id="0a851-115">Language construct</span></span></th>
<th><span data-ttu-id="0a851-116">Prostá syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a851-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="0a851-117">Podrobná syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a851-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="0a851-118">složené výrazy</span><span class="sxs-lookup"><span data-stu-id="0a851-118">compound expressions</span></span>
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

<span data-ttu-id="0a851-119">vnořené `let` vazby</span><span class="sxs-lookup"><span data-stu-id="0a851-119">nested `let` bindings</span></span>

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
<span data-ttu-id="0a851-120">blok kódu</span><span class="sxs-lookup"><span data-stu-id="0a851-120">code block</span></span>
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
<tr><td><span data-ttu-id="0a851-121">Zapisovací</span><span class="sxs-lookup"><span data-stu-id="0a851-121">record</span></span>
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
<tr><td><span data-ttu-id="0a851-122">třída</span><span class="sxs-lookup"><span data-stu-id="0a851-122">class</span></span>
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
<tr><td><span data-ttu-id="0a851-123">– struktura</span><span class="sxs-lookup"><span data-stu-id="0a851-123">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="0a851-124">rozlišené sjednocení</span><span class="sxs-lookup"><span data-stu-id="0a851-124">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="0a851-125">rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a851-125">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="0a851-126">výraz objektu</span><span class="sxs-lookup"><span data-stu-id="0a851-126">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="0a851-127">implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a851-127">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="0a851-128">Přípona typu</span><span class="sxs-lookup"><span data-stu-id="0a851-128">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="0a851-129">module</span><span class="sxs-lookup"><span data-stu-id="0a851-129">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="0a851-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a851-130">See also</span></span>

- [<span data-ttu-id="0a851-131">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="0a851-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="0a851-132">Direktivy kompilátoru</span><span class="sxs-lookup"><span data-stu-id="0a851-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="0a851-133">Pravidla formátování kódu</span><span class="sxs-lookup"><span data-stu-id="0a851-133">Code Formatting Guidelines</span></span>](../style-guide/formatting.md)
