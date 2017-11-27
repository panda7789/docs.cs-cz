---
title: "Podrobná syntaxe (F#)"
description: "Informace o rozdílu mezi podrobné a jednoduchý syntaxe v programovací jazyk F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0a6792b3-b312-4453-a025-21d9760eee5d
ms.openlocfilehash: 2cef359a879897825733a3186be97b38896f5953
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="verbose-syntax"></a><span data-ttu-id="8dea7-104">Podrobná syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dea7-104">Verbose Syntax</span></span>

<span data-ttu-id="8dea7-105">Nejsou k dispozici pro mnoho konstrukce v jazyce F # dvě formy syntaxe: *podrobná syntaxe* a *prostá syntaxe*.</span><span class="sxs-lookup"><span data-stu-id="8dea7-105">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="8dea7-106">Podrobná syntaxe není jako běžně používá, ale nabízí výhodu v podobě méně citlivé na odsazení.</span><span class="sxs-lookup"><span data-stu-id="8dea7-106">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="8dea7-107">Prostá syntaxe je kratší a používá odsazení signál začátek a konec konstrukce, nikoli jako další klíčová slova `begin`, `end`, `in`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="8dea7-107">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="8dea7-108">Výchozí syntaxe je prostá syntaxe.</span><span class="sxs-lookup"><span data-stu-id="8dea7-108">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="8dea7-109">Toto téma popisuje syntaxe konstrukce jazyka F #, není-li povoleno prostá syntaxe.</span><span class="sxs-lookup"><span data-stu-id="8dea7-109">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="8dea7-110">Podrobná syntaxe je vždy povolena, tak i v případě, že povolíte prostá syntaxe, když můžete nadále používat podrobná syntaxe pro některé konstruktory.</span><span class="sxs-lookup"><span data-stu-id="8dea7-110">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="8dea7-111">Prostá syntaxe můžete zakázat pomocí `#light "off"` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="8dea7-111">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>


## <a name="table-of-constructs"></a><span data-ttu-id="8dea7-112">Tabulka konstrukce</span><span class="sxs-lookup"><span data-stu-id="8dea7-112">Table of Constructs</span></span>
<span data-ttu-id="8dea7-113">Následující tabulka ukazuje jednoduchý a podrobné syntaxi pro konstruktory jazyka F # v kontextech tam, kde je rozdíl mezi dvěma formuláři.</span><span class="sxs-lookup"><span data-stu-id="8dea7-113">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="8dea7-114">V této tabulce, úhel závorky (&lt;&gt;) uzavřete prvky uživatelem zadané syntaxe.</span><span class="sxs-lookup"><span data-stu-id="8dea7-114">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="8dea7-115">Naleznete v dokumentaci pro každý jazyk konstrukce pro podrobnější informace o syntaxi používaných v rámci těchto konstrukce.</span><span class="sxs-lookup"><span data-stu-id="8dea7-115">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>



<table>
<tr>
<th><span data-ttu-id="8dea7-116">Jazyk – konstrukce</span><span class="sxs-lookup"><span data-stu-id="8dea7-116">Language construct</span></span></th>
<th><span data-ttu-id="8dea7-117">Prostá syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dea7-117">Lightweight syntax</span></span></th>
<th><span data-ttu-id="8dea7-118">Podrobná syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dea7-118">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="8dea7-119">složené výrazy</span><span class="sxs-lookup"><span data-stu-id="8dea7-119">compound expressions</span></span>
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


<span data-ttu-id="8dea7-120">vnořené `let` vazby</span><span class="sxs-lookup"><span data-stu-id="8dea7-120">nested `let` bindings</span></span>

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
<span data-ttu-id="8dea7-121">blok kódu</span><span class="sxs-lookup"><span data-stu-id="8dea7-121">code block</span></span>
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
<tr><td><span data-ttu-id="8dea7-122">záznam</span><span class="sxs-lookup"><span data-stu-id="8dea7-122">record</span></span>
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
<tr><td><span data-ttu-id="8dea7-123">třída</span><span class="sxs-lookup"><span data-stu-id="8dea7-123">class</span></span>
</td><td><span data-ttu-id="8dea7-124">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="8dea7-124">
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
<tr><td><span data-ttu-id="8dea7-125">– struktura</span><span class="sxs-lookup"><span data-stu-id="8dea7-125">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="8dea7-126">rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="8dea7-126">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="8dea7-127">rozhraní</span><span class="sxs-lookup"><span data-stu-id="8dea7-127">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="8dea7-128">objekt výraz</span><span class="sxs-lookup"><span data-stu-id="8dea7-128">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="8dea7-129">implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="8dea7-129">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="8dea7-130">Type – rozšíření</span><span class="sxs-lookup"><span data-stu-id="8dea7-130">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="8dea7-131">module</span><span class="sxs-lookup"><span data-stu-id="8dea7-131">module</span></span></td><td>

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



## <a name="see-also"></a><span data-ttu-id="8dea7-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="8dea7-132">See Also</span></span>
[<span data-ttu-id="8dea7-133">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="8dea7-133">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="8dea7-134">Direktivy kompilátoru</span><span class="sxs-lookup"><span data-stu-id="8dea7-134">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="8dea7-135">Pravidla formátování kódu</span><span class="sxs-lookup"><span data-stu-id="8dea7-135">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
