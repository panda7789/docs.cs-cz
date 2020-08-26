---
title: Záznamy
description: 'Přečtěte si, jak záznamy F # reprezentují jednoduché agregované hodnoty pojmenovaných hodnot, volitelně s členy.'
ms.date: 08/15/2020
ms.openlocfilehash: a72c0f15b58407e7d759e2fb5a1b35a7fc0d29e3
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812351"
---
# <a name="records"></a><span data-ttu-id="605e4-103">Záznamy</span><span class="sxs-lookup"><span data-stu-id="605e4-103">Records</span></span>

<span data-ttu-id="605e4-104">Záznamy reprezentují jednoduché agregované hodnoty pojmenovaných hodnot, volitelně s členy.</span><span class="sxs-lookup"><span data-stu-id="605e4-104">Records represent simple aggregates of named values, optionally with members.</span></span> <span data-ttu-id="605e4-105">Můžou být buď struktury, nebo typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="605e4-105">They can either be structs or reference types.</span></span>  <span data-ttu-id="605e4-106">Ve výchozím nastavení jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="605e4-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="605e4-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="605e4-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="605e4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="605e4-108">Remarks</span></span>

<span data-ttu-id="605e4-109">V předchozí syntaxi je *TypeName* názvem typu záznamu, *Label1* a *Label2* jsou názvy hodnot, označované jako *popisky*a *typ1* a *typ2* jsou typy těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="605e4-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="605e4-110">*Member-list* je volitelný seznam členů pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="605e4-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="605e4-111">Atribut můžete použít `[<Struct>]` k vytvoření záznamu struktury namísto záznamu, který je odkazovým typem.</span><span class="sxs-lookup"><span data-stu-id="605e4-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="605e4-112">Dále je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="605e4-112">Following are some examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="605e4-113">Když je každý popisek na samostatném řádku, je středník volitelný.</span><span class="sxs-lookup"><span data-stu-id="605e4-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="605e4-114">Můžete nastavit hodnoty ve výrazech známých jako *výrazy záznamu*.</span><span class="sxs-lookup"><span data-stu-id="605e4-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="605e4-115">Kompilátor odvodí typ z použitých popisků (pokud jsou popisky dostatečně odlišné od jiných typů záznamů).</span><span class="sxs-lookup"><span data-stu-id="605e4-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="605e4-116">Složené závorky ({}) uzavírají výraz záznamu.</span><span class="sxs-lookup"><span data-stu-id="605e4-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="605e4-117">Následující kód ukazuje výraz záznamu, který inicializuje záznam se třemi elementy float s popisky `x` `y` a `z` .</span><span class="sxs-lookup"><span data-stu-id="605e4-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="605e4-118">Nepoužívejte zkrácený tvar, pokud může existovat jiný typ, který má také stejné popisky.</span><span class="sxs-lookup"><span data-stu-id="605e4-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="605e4-119">Popisky posledního deklarovaného typu mají přednost před dříve deklarovaným typem, takže v předchozím příkladu `mypoint3D` je odvozeno `Point3D` .</span><span class="sxs-lookup"><span data-stu-id="605e4-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="605e4-120">Typ záznamu lze explicitně zadat, jak je uvedeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="605e4-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="605e4-121">Metody lze definovat pro typy záznamů stejně jako pro typy tříd.</span><span class="sxs-lookup"><span data-stu-id="605e4-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="605e4-122">Vytváření záznamů pomocí výrazů záznamu</span><span class="sxs-lookup"><span data-stu-id="605e4-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="605e4-123">Záznamy můžete inicializovat pomocí popisků, které jsou definovány v záznamu.</span><span class="sxs-lookup"><span data-stu-id="605e4-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="605e4-124">Výraz, který to dělá, se označuje jako *výraz záznamu*.</span><span class="sxs-lookup"><span data-stu-id="605e4-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="605e4-125">K uzavření výrazu záznamu použijte složené závorky a jako oddělovač použijte středník.</span><span class="sxs-lookup"><span data-stu-id="605e4-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="605e4-126">Následující příklad ukazuje, jak vytvořit záznam.</span><span class="sxs-lookup"><span data-stu-id="605e4-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="605e4-127">Středníky za posledním polem v rámci výrazu záznamu a definice typu jsou volitelné, bez ohledu na to, zda jsou všechna pole na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="605e4-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="605e4-128">Když vytvoříte záznam, je nutné zadávat hodnoty pro každé pole.</span><span class="sxs-lookup"><span data-stu-id="605e4-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="605e4-129">Nelze odkazovat na hodnoty jiných polí v inicializačním výrazu pro každé pole.</span><span class="sxs-lookup"><span data-stu-id="605e4-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="605e4-130">V následujícím kódu `myRecord2` je typ odvozen z názvů polí.</span><span class="sxs-lookup"><span data-stu-id="605e4-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="605e4-131">Volitelně můžete zadat název typu explicitně.</span><span class="sxs-lookup"><span data-stu-id="605e4-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="605e4-132">Další forma konstrukce záznamu může být užitečná v případě, že je nutné zkopírovat existující záznam a případně změnit některé hodnoty polí.</span><span class="sxs-lookup"><span data-stu-id="605e4-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="605e4-133">Tento příklad ilustruje následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="605e4-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="605e4-134">Tato forma výrazu záznamu se nazývá *výraz pro kopírování a aktualizaci záznamů*.</span><span class="sxs-lookup"><span data-stu-id="605e4-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="605e4-135">Ve výchozím nastavení jsou záznamy neměnné. Můžete však snadno vytvářet upravené záznamy pomocí výrazu kopírování a aktualizace.</span><span class="sxs-lookup"><span data-stu-id="605e4-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="605e4-136">Můžete také explicitně zadat proměnlivé pole.</span><span class="sxs-lookup"><span data-stu-id="605e4-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="605e4-137">Nepoužívejte atribut DefaultValue s poli záznamu.</span><span class="sxs-lookup"><span data-stu-id="605e4-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="605e4-138">Lepším řešením je definování výchozích instancí záznamů s poli, která jsou inicializovaná na výchozí hodnoty, a pak pomocí výrazu záznamu pro kopírování a aktualizace nastavit pole, která se liší od výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="605e4-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="creating-mutually-recursive-records"></a><span data-ttu-id="605e4-139">Vytváření vzájemně rekurzivních záznamů</span><span class="sxs-lookup"><span data-stu-id="605e4-139">Creating Mutually Recursive Records</span></span>

<span data-ttu-id="605e4-140">Při vytváření záznamu můžete chtít, aby byl závislý na jiném typu, který chcete později definovat.</span><span class="sxs-lookup"><span data-stu-id="605e4-140">Sometime when creating a record, you may want to have it depend on another type that you would like to define afterwards.</span></span> <span data-ttu-id="605e4-141">Jedná se o chybu kompilace, pokud nedefinujete typy záznamů, které se mají vzájemně rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="605e4-141">This is a compile error unless you define the record types to be mutually recursive.</span></span>

<span data-ttu-id="605e4-142">Definování vzájemně rekurzivních záznamů se provádí pomocí `and` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="605e4-142">Defining mutually recursive records is done with the `and` keyword.</span></span> <span data-ttu-id="605e4-143">To umožňuje propojit 2 nebo více typů záznamů dohromady.</span><span class="sxs-lookup"><span data-stu-id="605e4-143">This lets you link 2 or more record types together.</span></span>

<span data-ttu-id="605e4-144">Například následující kód definuje `Person` `Address` typ a jako vzájemně rekurzivní:</span><span class="sxs-lookup"><span data-stu-id="605e4-144">For example, the following code defines a `Person` and `Address` type as mutually recursive:</span></span>

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string
    Occupant: Person }
```

<span data-ttu-id="605e4-145">Pokud jste definovali předchozí příklad bez `and` klíčového slova, pak nebylo zkompilováno.</span><span class="sxs-lookup"><span data-stu-id="605e4-145">If you were to define the previous example without the `and` keyword, then it would not compile.</span></span> <span data-ttu-id="605e4-146">`and`Klíčové slovo je vyžadováno pro vzájemně rekurzivní definice.</span><span class="sxs-lookup"><span data-stu-id="605e4-146">The `and` keyword is required for mutually recursive definitions.</span></span>

## <a name="pattern-matching-with-records"></a><span data-ttu-id="605e4-147">Porovnávání vzorů se záznamy</span><span class="sxs-lookup"><span data-stu-id="605e4-147">Pattern Matching with Records</span></span>

<span data-ttu-id="605e4-148">Záznamy lze použít se porovnáváním vzorů.</span><span class="sxs-lookup"><span data-stu-id="605e4-148">Records can be used with pattern matching.</span></span> <span data-ttu-id="605e4-149">Můžete určit některá pole explicitně a zadat proměnné pro jiná pole, která budou přiřazena při výskytu shody.</span><span class="sxs-lookup"><span data-stu-id="605e4-149">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="605e4-150">Následující příklad kódu to dokládá.</span><span class="sxs-lookup"><span data-stu-id="605e4-150">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="605e4-151">Výstup tohoto kódu je následující.</span><span class="sxs-lookup"><span data-stu-id="605e4-151">The output of this code is as follows.</span></span>

```console
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="records-and-members"></a><span data-ttu-id="605e4-152">Záznamy a členové</span><span class="sxs-lookup"><span data-stu-id="605e4-152">Records and members</span></span>

<span data-ttu-id="605e4-153">Můžete určit členy v záznamech, podobně jako u tříd.</span><span class="sxs-lookup"><span data-stu-id="605e4-153">You can specify members on records much like you can with classes.</span></span> <span data-ttu-id="605e4-154">Pro pole není podporována žádná podpora.</span><span class="sxs-lookup"><span data-stu-id="605e4-154">There is no support for fields.</span></span> <span data-ttu-id="605e4-155">Běžným přístupem je definování `Default` statického člena pro snadné vytváření záznamů:</span><span class="sxs-lookup"><span data-stu-id="605e4-155">A common approach is to define a `Default` static member for easy record construction:</span></span>

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    static member Default =
        { Name = "Phillip"
          Age = 12
          Address = "123 happy fun street" }

let defaultPerson = Person.Default
```

<span data-ttu-id="605e4-156">Použijete-li samotný identifikátor, tento identifikátor odkazuje na instanci záznamu, jehož člen je označován:</span><span class="sxs-lookup"><span data-stu-id="605e4-156">If you use a self identifier, that identifier refers to the instance of the record whose member is called:</span></span>

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    member this.WeirdToString() =
        this.Name + this.Address + string this.Age

let p = { Name = "a"; Age = 12; Address = "abc123 }
let weirdString = p.WeirdToString()
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="605e4-157">Rozdíly mezi záznamy a třídami</span><span class="sxs-lookup"><span data-stu-id="605e4-157">Differences Between Records and Classes</span></span>

<span data-ttu-id="605e4-158">Pole záznamu se liší od tříd v tom, že jsou automaticky vystavena jako vlastnosti a používají se při vytváření a kopírování záznamů.</span><span class="sxs-lookup"><span data-stu-id="605e4-158">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="605e4-159">Konstrukce záznamu se také liší od konstrukce třídy.</span><span class="sxs-lookup"><span data-stu-id="605e4-159">Record construction also differs from class construction.</span></span> <span data-ttu-id="605e4-160">V typu záznamu nelze definovat konstruktor.</span><span class="sxs-lookup"><span data-stu-id="605e4-160">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="605e4-161">Místo toho se použije syntaxe konstrukce popsaná v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="605e4-161">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="605e4-162">Třídy nemají žádný přímý vztah mezi parametry konstruktoru, poli a vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="605e4-162">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="605e4-163">Podobně jako typy sjednocení a struktury mají záznamy strukturální sémantiku rovnosti.</span><span class="sxs-lookup"><span data-stu-id="605e4-163">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="605e4-164">Třídy mají odkaz na sémantiku rovnosti.</span><span class="sxs-lookup"><span data-stu-id="605e4-164">Classes have reference equality semantics.</span></span> <span data-ttu-id="605e4-165">Následující příklad kódu to demonstruje.</span><span class="sxs-lookup"><span data-stu-id="605e4-165">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="605e4-166">Výstup tohoto kódu je následující:</span><span class="sxs-lookup"><span data-stu-id="605e4-166">The output of this code is as follows:</span></span>

```console
The records are equal.
```

<span data-ttu-id="605e4-167">Pokud píšete stejný kód s třídami, objekty obou tříd by byly neshodné, protože dvě hodnoty by představovaly dva objekty na haldě a byly porovnány pouze adresy (Pokud typ třídy Přepisuje `System.Object.Equals` metodu).</span><span class="sxs-lookup"><span data-stu-id="605e4-167">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="605e4-168">Pokud potřebujete referenční rovnost záznamů, přidejte atribut `[<ReferenceEquality>]` nad záznam.</span><span class="sxs-lookup"><span data-stu-id="605e4-168">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="605e4-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="605e4-169">See also</span></span>

- [<span data-ttu-id="605e4-170">Typy F#</span><span class="sxs-lookup"><span data-stu-id="605e4-170">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="605e4-171">Třídy</span><span class="sxs-lookup"><span data-stu-id="605e4-171">Classes</span></span>](classes.md)
- [<span data-ttu-id="605e4-172">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="605e4-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="605e4-173">Rovnost odkazů</span><span class="sxs-lookup"><span data-stu-id="605e4-173">Reference-Equality</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-referenceequalityattribute.html)
- [<span data-ttu-id="605e4-174">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="605e4-174">Pattern Matching</span></span>](pattern-matching.md)
