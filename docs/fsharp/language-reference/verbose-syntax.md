---
title: Podrobná syntaxe (F#)
description: 'Informace o rozdílu mezi podrobné a jednoduchý syntaxe v programovací jazyk F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: fd040a66a789bc6717fd14e6a9f28274c9e3542b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="verbose-syntax"></a><span data-ttu-id="91097-103">Podrobná syntaxe</span><span class="sxs-lookup"><span data-stu-id="91097-103">Verbose Syntax</span></span>

<span data-ttu-id="91097-104">Nejsou k dispozici pro mnoho konstrukce v jazyce F # dvě formy syntaxe: *podrobná syntaxe* a *prostá syntaxe*.</span><span class="sxs-lookup"><span data-stu-id="91097-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="91097-105">Podrobná syntaxe není jako běžně používá, ale nabízí výhodu v podobě méně citlivé na odsazení.</span><span class="sxs-lookup"><span data-stu-id="91097-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="91097-106">Prostá syntaxe je kratší a používá odsazení signál začátek a konec konstrukce, nikoli jako další klíčová slova `begin`, `end`, `in`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="91097-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="91097-107">Výchozí syntaxe je prostá syntaxe.</span><span class="sxs-lookup"><span data-stu-id="91097-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="91097-108">Toto téma popisuje syntaxe konstrukce jazyka F #, není-li povoleno prostá syntaxe.</span><span class="sxs-lookup"><span data-stu-id="91097-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="91097-109">Podrobná syntaxe je vždy povolena, tak i v případě, že povolíte prostá syntaxe, když můžete nadále používat podrobná syntaxe pro některé konstruktory.</span><span class="sxs-lookup"><span data-stu-id="91097-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="91097-110">Prostá syntaxe můžete zakázat pomocí `#light "off"` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="91097-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>


## <a name="table-of-constructs"></a><span data-ttu-id="91097-111">Tabulka konstrukce</span><span class="sxs-lookup"><span data-stu-id="91097-111">Table of Constructs</span></span>
<span data-ttu-id="91097-112">Následující tabulka ukazuje jednoduchý a podrobné syntaxi pro konstruktory jazyka F # v kontextech tam, kde je rozdíl mezi dvěma formuláři.</span><span class="sxs-lookup"><span data-stu-id="91097-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="91097-113">V této tabulce, úhel závorky (&lt;&gt;) uzavřete prvky uživatelem zadané syntaxe.</span><span class="sxs-lookup"><span data-stu-id="91097-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="91097-114">Naleznete v dokumentaci pro každý jazyk konstrukce pro podrobnější informace o syntaxi používaných v rámci těchto konstrukce.</span><span class="sxs-lookup"><span data-stu-id="91097-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>



<table>
<tr>
<th><span data-ttu-id="91097-115">Jazyk – konstrukce</span><span class="sxs-lookup"><span data-stu-id="91097-115">Language construct</span></span></th>
<th><span data-ttu-id="91097-116">Prostá syntaxe</span><span class="sxs-lookup"><span data-stu-id="91097-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="91097-117">Podrobná syntaxe</span><span class="sxs-lookup"><span data-stu-id="91097-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="91097-118">složené výrazy</span><span class="sxs-lookup"><span data-stu-id="91097-118">compound expressions</span></span>
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


<span data-ttu-id="91097-119">vnořené `let` vazby</span><span class="sxs-lookup"><span data-stu-id="91097-119">nested `let` bindings</span></span>

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
<span data-ttu-id="91097-120">blok kódu</span><span class="sxs-lookup"><span data-stu-id="91097-120">code block</span></span>
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
<tr><td><span data-ttu-id="91097-121">záznam</span><span class="sxs-lookup"><span data-stu-id="91097-121">record</span></span>
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
<tr><td><span data-ttu-id="91097-122">třída</span><span class="sxs-lookup"><span data-stu-id="91097-122">class</span></span>
</td><td><span data-ttu-id="91097-123">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="91097-123">
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
<tr><td><span data-ttu-id="91097-124">– struktura</span><span class="sxs-lookup"><span data-stu-id="91097-124">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="91097-125">rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="91097-125">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="91097-126">rozhraní</span><span class="sxs-lookup"><span data-stu-id="91097-126">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="91097-127">objekt výraz</span><span class="sxs-lookup"><span data-stu-id="91097-127">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="91097-128">implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="91097-128">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="91097-129">Type – rozšíření</span><span class="sxs-lookup"><span data-stu-id="91097-129">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="91097-130">module</span><span class="sxs-lookup"><span data-stu-id="91097-130">module</span></span></td><td>

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



## <a name="see-also"></a><span data-ttu-id="91097-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="91097-131">See Also</span></span>
[<span data-ttu-id="91097-132">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="91097-132">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="91097-133">Direktivy kompilátoru</span><span class="sxs-lookup"><span data-stu-id="91097-133">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="91097-134">Pravidla formátování kódu</span><span class="sxs-lookup"><span data-stu-id="91097-134">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
