---
title: "Záznamy (F#)"
description: "Zjistěte, jak F # záznamy představují jednoduché agregace pojmenovaných hodnot, případně se členy."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a3701ea-4308-4fa1-9b5c-b955c470f17a
ms.openlocfilehash: f5ade1db39431d99f10eb6967f02335123b83d34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="records"></a><span data-ttu-id="995d9-104">Záznamy</span><span class="sxs-lookup"><span data-stu-id="995d9-104">Records</span></span>

<span data-ttu-id="995d9-105">Záznamy představují jednoduché agregace pojmenovaných hodnot, případně se členy.</span><span class="sxs-lookup"><span data-stu-id="995d9-105">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="995d9-106">Od verze 4.1 F #, můžete buď být typy struktur nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="995d9-106">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="995d9-107">Typy odkazů ve výchozím nastavení jsou.</span><span class="sxs-lookup"><span data-stu-id="995d9-107">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="995d9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="995d9-108">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="995d9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="995d9-109">Remarks</span></span>
<span data-ttu-id="995d9-110">V předchozích syntaxi *typename* je název typu záznamu, *label1* a *label2* jsou názvy hodnot, označuje jako *popisky*, a *type1* a *type2* jsou typy tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="995d9-110">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="995d9-111">*seznam členů* je volitelný seznam členů pro typ.</span><span class="sxs-lookup"><span data-stu-id="995d9-111">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="995d9-112">Můžete použít `[<Struct>]` atributů k vytvoření záznamu struktura místo záznam, který je typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="995d9-112">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="995d9-113">Tady jsou některé příklady.</span><span class="sxs-lookup"><span data-stu-id="995d9-113">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="995d9-114">Když každý popisek na samostatném řádku, je volitelný středník.</span><span class="sxs-lookup"><span data-stu-id="995d9-114">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="995d9-115">Můžete nastavit hodnoty ve výrazech známé jako *záznam výrazy*.</span><span class="sxs-lookup"><span data-stu-id="995d9-115">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="995d9-116">Kompilátor odvodí typ ze štítků používá (pokud jsou popisky dostatečně odlišné od jiných typů záznamů).</span><span class="sxs-lookup"><span data-stu-id="995d9-116">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="995d9-117">Složené závorky ({}) vložte jej záznamu.</span><span class="sxs-lookup"><span data-stu-id="995d9-117">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="995d9-118">Následující kód ukazuje výraz záznam, který inicializuje záznam se tři float prvky s popisky `x`, `y` a `z`.</span><span class="sxs-lookup"><span data-stu-id="995d9-118">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="995d9-119">Nepoužívejte zkráceném tvaru, pokud může být jiný typ, který má také stejné popisky.</span><span class="sxs-lookup"><span data-stu-id="995d9-119">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="995d9-120">Popisky nedávno deklarovaný typ mají přednost před těch, které dříve deklarovaný typ, tak v předchozím příkladu `mypoint3D` je odvodit být `Point3D`.</span><span class="sxs-lookup"><span data-stu-id="995d9-120">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="995d9-121">Explicitně zadaný typ záznamu, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="995d9-121">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="995d9-122">Metody lze definovat pro typy záznamů stejně jako typy tříd.</span><span class="sxs-lookup"><span data-stu-id="995d9-122">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="995d9-123">Vytvoření záznamů pomocí záznamu výrazy</span><span class="sxs-lookup"><span data-stu-id="995d9-123">Creating Records by Using Record Expressions</span></span>
<span data-ttu-id="995d9-124">Záznamy lze inicializovat pomocí štítků, které jsou definovány v záznamu.</span><span class="sxs-lookup"><span data-stu-id="995d9-124">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="995d9-125">Výraz, který to se označuje jako *záznam výraz*.</span><span class="sxs-lookup"><span data-stu-id="995d9-125">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="995d9-126">Použijte složené závorky a vložte jej záznam použít středník jako oddělovač.</span><span class="sxs-lookup"><span data-stu-id="995d9-126">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="995d9-127">Následující příklad ukazuje, jak vytvořit záznam.</span><span class="sxs-lookup"><span data-stu-id="995d9-127">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="995d9-128">Středníky za poslední pole v záznamu výraz a v definici typu jsou volitelné, bez ohledu na to, zda jsou tato pole vše na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="995d9-128">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="995d9-129">Když vytvoříte záznam, je nutné zadat hodnoty pro každé pole.</span><span class="sxs-lookup"><span data-stu-id="995d9-129">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="995d9-130">Nemůže odkazovat na hodnoty dalších polí ve výrazu inicializace pro každé pole.</span><span class="sxs-lookup"><span data-stu-id="995d9-130">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="995d9-131">V následujícím kódu, typ `myRecord2` je odvozeno z názvy polí.</span><span class="sxs-lookup"><span data-stu-id="995d9-131">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="995d9-132">Volitelně můžete zadat název typu explicitně.</span><span class="sxs-lookup"><span data-stu-id="995d9-132">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="995d9-133">Jinou formu konstrukce záznam může být užitečné, když máte zkopírováním existujícího záznamu, a případně změnit některé hodnoty polí.</span><span class="sxs-lookup"><span data-stu-id="995d9-133">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="995d9-134">To ukazuje následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="995d9-134">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="995d9-135">Tento formulář výrazu záznamu je volána *kopírování a aktualizace záznamů výraz*.</span><span class="sxs-lookup"><span data-stu-id="995d9-135">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="995d9-136">Záznamy jsou neměnné ve výchozím nastavení; změněné záznamy však můžete snadno vytvořit pomocí výrazu kopírování a aktualizace.</span><span class="sxs-lookup"><span data-stu-id="995d9-136">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="995d9-137">Můžete také explicitně zadat měnitelný pole.</span><span class="sxs-lookup"><span data-stu-id="995d9-137">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="995d9-138">Nepoužívejte atribut DefaultValue s polí záznamu.</span><span class="sxs-lookup"><span data-stu-id="995d9-138">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="995d9-139">Lepší přístup je definovat výchozí instance záznamů vložením polí, která jsou inicializovány výchozí hodnoty a pak použít kopii a aktualizovat záznam výraz nastavit všechna pole, které se liší od výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="995d9-139">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a><span data-ttu-id="995d9-140">Pro porovnávání se záznamy</span><span class="sxs-lookup"><span data-stu-id="995d9-140">Pattern Matching with Records</span></span>
<span data-ttu-id="995d9-141">Záznamy lze použít s porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="995d9-141">Records can be used with pattern matching.</span></span> <span data-ttu-id="995d9-142">Můžete explicitně zadat některá pole a zadejte proměnné pro další pole, které budou přiřazeny, pokud je nalezena shoda.</span><span class="sxs-lookup"><span data-stu-id="995d9-142">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="995d9-143">Následující příklad kódu to dokládá.</span><span class="sxs-lookup"><span data-stu-id="995d9-143">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="995d9-144">Výstup tohoto kódu je následující.</span><span class="sxs-lookup"><span data-stu-id="995d9-144">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="995d9-145">Rozdíly mezi záznamy a třídy</span><span class="sxs-lookup"><span data-stu-id="995d9-145">Differences Between Records and Classes</span></span>
<span data-ttu-id="995d9-146">Polí záznamů se liší od třídy, že jsou automaticky zveřejněné jako vlastnosti, které mají použít při vytváření nebo kopírování záznamů.</span><span class="sxs-lookup"><span data-stu-id="995d9-146">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="995d9-147">Vytváření záznamů se také liší od třídy konstrukce.</span><span class="sxs-lookup"><span data-stu-id="995d9-147">Record construction also differs from class construction.</span></span> <span data-ttu-id="995d9-148">V záznamu typu nelze definovat konstruktor.</span><span class="sxs-lookup"><span data-stu-id="995d9-148">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="995d9-149">Místo toho použije syntaxe vytváření popsaných v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="995d9-149">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="995d9-150">Třídy mají žádné přímé vztah mezi konstruktor parametry, polí a vlastností.</span><span class="sxs-lookup"><span data-stu-id="995d9-150">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="995d9-151">Jako typy union a struktura mají záznamy sémantiku strukturální rovnosti.</span><span class="sxs-lookup"><span data-stu-id="995d9-151">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="995d9-152">Třídy mají referenční rovnosti sémantiku.</span><span class="sxs-lookup"><span data-stu-id="995d9-152">Classes have reference equality semantics.</span></span> <span data-ttu-id="995d9-153">Následující příklad kódu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="995d9-153">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="995d9-154">Pokud píšete stejný kód s třídami, objekty dvou tříd by nerovné, protože tyto dvě hodnoty by představují dva objekty v haldě a pouze adresy by být porovnána (Pokud přepíše typu třídy `System.Object.Equals` metoda).</span><span class="sxs-lookup"><span data-stu-id="995d9-154">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="995d9-155">Pokud třeba referenční rovnost pro záznamy, přidejte atribut `[<ReferenceEquality>]` výše záznamu.</span><span class="sxs-lookup"><span data-stu-id="995d9-155">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="995d9-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="995d9-156">See Also</span></span>
[<span data-ttu-id="995d9-157">Typy F #</span><span class="sxs-lookup"><span data-stu-id="995d9-157">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="995d9-158">Třídy</span><span class="sxs-lookup"><span data-stu-id="995d9-158">Classes</span></span>](classes.md)

[<span data-ttu-id="995d9-159">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="995d9-159">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="995d9-160">Referenční rovnost</span><span class="sxs-lookup"><span data-stu-id="995d9-160">Reference-Equality</span></span>](https://msdn.microsoft.com/en-us/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[<span data-ttu-id="995d9-161">Shoda vzoru</span><span class="sxs-lookup"><span data-stu-id="995d9-161">Pattern Matching</span></span>](pattern-matching.md)
