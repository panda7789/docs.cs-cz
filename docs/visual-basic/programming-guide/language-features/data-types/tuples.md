---
title: "Řazené kolekce členů v jazyce Visual Basic"
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2653b9dc8a6ecbcb718c20be8bd6275edf4cfb6e
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="tuples-visual-basic"></a><span data-ttu-id="62e6b-102">Řazené kolekce členů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62e6b-102">Tuples (Visual Basic)</span></span>

<span data-ttu-id="62e6b-103">Počínaje 2017 Visual Basic, jazyka Visual Basic má integrovanou podporu pro řazené kolekce členů, která umožňuje vytváření řazených kolekcí členů a přístup k elementům jednodušší řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="62e6b-103">Starting with Visual Basic 2017, the Visual Basic language offers built-in support for tuples that makes creating tuples and accessing the elements of tuples easier.</span></span> <span data-ttu-id="62e6b-104">Řazené kolekce členů je šedé – datová struktura, která má specifické číslo a pořadí hodnot.</span><span class="sxs-lookup"><span data-stu-id="62e6b-104">A tuple is a light-weight data structure that has a specific number and sequence of values.</span></span> <span data-ttu-id="62e6b-105">Pokud instanci můžete vytvořit řazenou kolekci členů, můžete definovat číslo a datový typ jednotlivých hodnota (nebo element).</span><span class="sxs-lookup"><span data-stu-id="62e6b-105">When you instantiate the tuple, you define the number and the data type of each value (or element).</span></span> <span data-ttu-id="62e6b-106">Například 2 řazené kolekce členů (nebo dvojici) má dva elementy.</span><span class="sxs-lookup"><span data-stu-id="62e6b-106">For example, a 2-tuple (or pair) has two elements.</span></span> <span data-ttu-id="62e6b-107">Může být první `Boolean` hodnotu, zatímco druhý `String`.</span><span class="sxs-lookup"><span data-stu-id="62e6b-107">The first might be a `Boolean` value, while the second is a `String`.</span></span> <span data-ttu-id="62e6b-108">Protože řazených kolekcí členů usnadňují ukládat víc hodnot v jednom objektu, se často používají jako lehký způsob, jak vrátit více hodnot z metody.</span><span class="sxs-lookup"><span data-stu-id="62e6b-108">Because tuples make it easy to store multiple values in a single object, they are often used as a lightweight way to return multiple values from a method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="62e6b-109">Vyžaduje podporu řazené kolekce členů <xref:System.ValueTuple> typu.</span><span class="sxs-lookup"><span data-stu-id="62e6b-109">Tuple support requires the <xref:System.ValueTuple> type.</span></span> <span data-ttu-id="62e6b-110">Pokud není nainstalovaná rozhraní .NET Framework 4.7, je nutné přidat balíček NuGet `System.ValueTuple`, která je k dispozici v galerii NuGet.</span><span class="sxs-lookup"><span data-stu-id="62e6b-110">If the .NET Framework 4.7 is not installed, you must add the NuGet package `System.ValueTuple`, which is available on the NuGet Gallery.</span></span> <span data-ttu-id="62e6b-111">Bez tohoto balíčku může se zobrazit chyba kompilace podobná "Předdefinované type 'ValueTuple(Of,,,)' není definované nebo importovat."</span><span class="sxs-lookup"><span data-stu-id="62e6b-111">Without this package, you may get a compilation error similar to, "Predefined type 'ValueTuple(Of,,,)' is not defined or imported."</span></span>

## <a name="instantiating-and-using-a-tuple"></a><span data-ttu-id="62e6b-112">Vytváření instancí a použití řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="62e6b-112">Instantiating and using a tuple</span></span>

<span data-ttu-id="62e6b-113">Řazené kolekce členů instance uzavřením závorkách zasílání rychlých zpráv hodnot oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="62e6b-113">You instantiate a tuple by enclosing its comma-delimited values im parentheses.</span></span> <span data-ttu-id="62e6b-114">Každý z těchto hodnot se pak stane pole řazenou kolekci členů.</span><span class="sxs-lookup"><span data-stu-id="62e6b-114">Each of those values then becomes a field of the tuple.</span></span> <span data-ttu-id="62e6b-115">Například následující kód definuje triple (nebo 3 řazené kolekce členů) `Date` jako svou první hodnotu `String` jako jeho sekundu a `Boolean` jako jeho třetí.</span><span class="sxs-lookup"><span data-stu-id="62e6b-115">For example, the following code defines a triple (or 3-tuple) with a `Date` as its first value, a `String` as its second, and a `Boolean` as its third.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

<span data-ttu-id="62e6b-116">Ve výchozím nastavení, název každého pole v řazené kolekce členů se skládá z řetězce `Item` společně s tohoto pole na základě jedné pozice v řazené kolekci členů.</span><span class="sxs-lookup"><span data-stu-id="62e6b-116">By default, the name of each field in a tuple consists of the string `Item` along with the field's one-based position in the tuple.</span></span> <span data-ttu-id="62e6b-117">Pro tento 3-řazené kolekce členů `Date` pole je `Item1`, `String` pole je `Item2`a `Boolean` pole je `Item3`.</span><span class="sxs-lookup"><span data-stu-id="62e6b-117">For this 3-tuple, the `Date` field is `Item1`, the `String` field is `Item2`, and the `Boolean` field is `Item3`.</span></span> <span data-ttu-id="62e6b-118">Tento příklad zobrazuje hodnoty polí řazené kolekce členů instanci v předchozím řádku kódu</span><span class="sxs-lookup"><span data-stu-id="62e6b-118">The following example displays the values of fields of the tuple instantiated in the previous line of code</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

<span data-ttu-id="62e6b-119">Čtení a zápis; jsou tato pole řazené kolekce členů jazyka Visual Basic poté, co jste instanci řazené kolekce členů, můžete její hodnoty upravit.</span><span class="sxs-lookup"><span data-stu-id="62e6b-119">The fields of a Visual Basic tuple are read-write; after you've instantiated a tuple, you can modify its values.</span></span> <span data-ttu-id="62e6b-120">Následující příklad změní dvě ze tří polí řazené kolekce členů vytvořili v předchozím příkladu a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="62e6b-120">The following example modifies two of the three fields of the tuple created in the previous example and displays the result.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a><span data-ttu-id="62e6b-121">Vytváření instancí a použití pojmenovaného řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="62e6b-121">Instantiating and using a named tuple</span></span>

<span data-ttu-id="62e6b-122">Místo použití výchozí názvy polí řazené kolekce členů, můžete vytvořit instanci *s názvem řazené kolekce členů* přiřazením vlastní názvy elementů řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="62e6b-122">Rather than using default names for a tuple's fields, you can instantiate a *named tuple* by assigning your own names to the tuple's elements.</span></span> <span data-ttu-id="62e6b-123">Pole řazené kolekce členů lze přistupovat pomocí jejich přiřazené názvy *nebo* jejich výchozí názvy.</span><span class="sxs-lookup"><span data-stu-id="62e6b-123">The tuple's fields can then be accessed by their assigned names *or* by their default names.</span></span> <span data-ttu-id="62e6b-124">Následující příklad vytvoří stejné 3-n-tice jako dříve, s tím rozdílem, že ji explicitně názvy první pole `EventDate`, druhý `Name`a třetí `IsHoliday`.</span><span class="sxs-lookup"><span data-stu-id="62e6b-124">The following example instantiates the same 3-tuple as previously, except that it explicitly names the first field `EventDate`, the second `Name`, and the third `IsHoliday`.</span></span> <span data-ttu-id="62e6b-125">Pak zobrazí hodnoty polí, upraví je a znovu zobrazuje hodnoty polí.</span><span class="sxs-lookup"><span data-stu-id="62e6b-125">It then displays the field values, modifies them, and displays the field values again.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="62e6b-126">Názvy elementů odvozené řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="62e6b-126">Inferred tuple element names</span></span>

<span data-ttu-id="62e6b-127">Počínaje 15.3 jazyka Visual Basic, Visual Basic můžete odvození názvy elementů řazené kolekce členů; není nutné explicitně přiřadit.</span><span class="sxs-lookup"><span data-stu-id="62e6b-127">Starting with Visual Basic 15.3, Visual Basic can infer the names of tuple elements; you do not have to assign them explicitly.</span></span> <span data-ttu-id="62e6b-128">Odvozené řazené kolekce členů názvy jsou užitečné při inicializaci řazenou kolekci členů ze sady proměnných a chcete, aby název elementu řazené kolekce členů být stejný jako název proměnné.</span><span class="sxs-lookup"><span data-stu-id="62e6b-128">Inferred tuple names are useful when you initialize a tuple from a set of variables, and you want the tuple element name to be the same as the variable name.</span></span> 

<span data-ttu-id="62e6b-129">Následující příklad vytvoří `stateInfo` řazené kolekce členů, která obsahuje tři explicitně s názvem elementů `state`, `stateName`, a `capital`.</span><span class="sxs-lookup"><span data-stu-id="62e6b-129">The following example creates a `stateInfo` tuple that contains three explicitly named elements, `state`, `stateName`, and `capital`.</span></span> <span data-ttu-id="62e6b-130">Všimněte si, že v pojmenování elementy, příkaz inicializace řazené kolekce členů jednoduše přiřadí pojmenované elementy hodnoty proměnných stejně jako s názvem.</span><span class="sxs-lookup"><span data-stu-id="62e6b-130">Note that, in naming the elements, the tuple initialization statement simply assigns the named elements the values of the identically named variables.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
<span data-ttu-id="62e6b-131">Protože elementy a proměnné mají stejný název, Visual Basic – kompilátor můžete odvození názvy polí, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="62e6b-131">Because elements and variables have the same name, the Visual Basic compiler can infer the names of the fields, as the following example shows.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

<span data-ttu-id="62e6b-132">Pokud chcete povolit názvy elementů interred řazené kolekce členů, je nutné zadat verzi kompilátoru jazyka Visual Basic pro použití v projektu jazyka Visual Basic (\*.vbproj) souboru:</span><span class="sxs-lookup"><span data-stu-id="62e6b-132">To enable interred tuple element names, you must define the version of the Visual Basic compiler to use in your Visual Basic project (\*.vbproj) file:</span></span> 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 

The version number can be any version of the Visual Basic compiler starting with 15.3. Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.

In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:

- The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.

- The candidate name is duplicated in the tuple.
 
When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime. Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`. 
  
## Tuples versus structures

A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types. For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure. It is designed to be a lightweight container for data. Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have. These include:

- Customer members. You cannot define your own properties, methods, or events for a tuple.

- Validation. You cannot validate the data assigned to fields.

- Immutability. Visual Basic tuples are mutable. In contrast, a custom structure allows you to control whether an instance is mutable or immutable.

If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.

A Visual Basic tuple does inherit the members of its **ValueTuple** type. In addition to its fields, these include the following methods:

| Member | Description |
| ---|---|
| CompareTo | Compares the current tuple to another tuple with the same number of elements. |
| Equals | Determines whether the current tuple is equal to another tuple or object. |
| GetHashCode | Calculates the hash code for the current instance. |
| ToString | Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields. |

In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.

## Assignment and tuples

Visual Basic supports assignment between tuple types that have the same number of fields. The field types can be converted if one of the following is true:

- The source and target field are of the same type.

- A widening (or implicit) conversion of the source type to the target type is defined. 

- `Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined. This conversion can throw an exception if the source value is outside the range of the target type.

Other conversions are not considered for assignments. Let's look at the kinds of assignments that are allowed between tuple types.

Consider these variables used in the following examples:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields. Their field names are the default `Item1` and `Item2`. The last two variables, `named` and `differentName` have semantic field names. Note that these two tuples have different names for the fields.

All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical. Therefore, all of these assignments work:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notice that the names of the tuples are not assigned. The values of the fields are assigned following the order of the fields in the tuple.

Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`. This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuples with different numbers of fields are not assignable:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="62e6b-133">Řazené kolekce členů jako metodu návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="62e6b-133">Tuples as method return values</span></span>

<span data-ttu-id="62e6b-134">Metoda může vrátit pouze jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="62e6b-134">A method can return only a single value.</span></span> <span data-ttu-id="62e6b-135">Často ale chcete volání metoda vrátí více hodnot.</span><span class="sxs-lookup"><span data-stu-id="62e6b-135">Frequently, though, you'd like a method call to return multiple values.</span></span> <span data-ttu-id="62e6b-136">Toto omezení obejít několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="62e6b-136">There are several ways to work around this limitation:</span></span>

- <span data-ttu-id="62e6b-137">Můžete vytvořit vlastní třídu nebo strukturu, jehož vlastnosti nebo pole představují hodnoty vrácené metodou.</span><span class="sxs-lookup"><span data-stu-id="62e6b-137">You can create a custom class or structure whose properties or fields represent values returned by the method.</span></span> <span data-ttu-id="62e6b-138">Proto je těžké řešení; To vyžaduje, aby definujete vlastní typ, jehož jediným účelem je načítání hodnot z volání metody.</span><span class="sxs-lookup"><span data-stu-id="62e6b-138">Thus is a heavyweight solution; it requires that you define a custom type whose only purpose is to retrieve values from a method call.</span></span>

- <span data-ttu-id="62e6b-139">Můžete vrátit jednu hodnotu z metody a vrátit zbývající hodnoty předáním odkazu na metodu.</span><span class="sxs-lookup"><span data-stu-id="62e6b-139">You can return a single value from the method, and return the remaining values by passing them by reference to the method.</span></span> <span data-ttu-id="62e6b-140">To zahrnuje režií při vytváření instance proměnné a rizika nechtěném přepsání hodnotu proměnné, kterou předáte odkazem.</span><span class="sxs-lookup"><span data-stu-id="62e6b-140">This involves the overhead of instantiating a variable and risks inadvertently overwriting the value of the variable that you pass by reference.</span></span>

- <span data-ttu-id="62e6b-141">Můžete použít řazenou kolekci členů, která poskytuje jednoduché řešení pro načítání více vrácených hodnot.</span><span class="sxs-lookup"><span data-stu-id="62e6b-141">You can use a tuple, which provides a lightweight solution to retrieving multiple return values.</span></span>

<span data-ttu-id="62e6b-142">Například **TryParse** metody v rozhraní .NET vrátit `Boolean` hodnotu, která určuje, zda analýza operace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="62e6b-142">For example, the **TryParse** methods in .NET return a `Boolean` value that indicates whether the parsing operation succeeded.</span></span> <span data-ttu-id="62e6b-143">Výsledek analýzy operace se vrátí do proměnné předaná odkazu na metodu.</span><span class="sxs-lookup"><span data-stu-id="62e6b-143">The result of the parsing operation is returned in a variable passed by reference to the method.</span></span> <span data-ttu-id="62e6b-144">Za normálních okolností volání metoda analýzy, jako <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> vypadá podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="62e6b-144">Normally, a call to the a parsing method such as <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> looks like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

<span data-ttu-id="62e6b-145">Se jsme zabalení volání vrací řazenou kolekci členů z analýzy operace <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metoda vlastní metoda.</span><span class="sxs-lookup"><span data-stu-id="62e6b-145">We can return a tuple from the parsing operation if we wrap the call to the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method in our own method.</span></span> <span data-ttu-id="62e6b-146">V následujícím příkladu `NumericLibrary.ParseInteger` volání <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodu a vrátí pojmenované řazené kolekce členů s dva elementy.</span><span class="sxs-lookup"><span data-stu-id="62e6b-146">In the following example, `NumericLibrary.ParseInteger` calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method and returns a named tuple with two elements.</span></span> 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

<span data-ttu-id="62e6b-147">Pak můžete volat metodu s kódem podobně jako tento:</span><span class="sxs-lookup"><span data-stu-id="62e6b-147">You can then call the method with code like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a><span data-ttu-id="62e6b-148">Řazené kolekce členů jazyka Visual Basic a řazených kolekcí členů v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="62e6b-148">Visual Basic tuples and tuples in the .NET Framework</span></span>

<span data-ttu-id="62e6b-149">Visual Basic řazené kolekce členů je instance jednoho **System.ValueTuple** obecné typy, které byly zavedeny v 4.7 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="62e6b-149">A Visual Basic tuple is an instance of one of the **System.ValueTuple** generic types, which were introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="62e6b-150">Rozhraní .NET Framework také obsahuje sadu obecného **System.Tuple** třídy.</span><span class="sxs-lookup"><span data-stu-id="62e6b-150">The .NET Framework also includes a set of generic **System.Tuple** classes.</span></span> <span data-ttu-id="62e6b-151">Tyto třídy, ale liší od řazených kolekcí členů jazyka Visual Basic a **System.ValueTuple** obecné typy v mnoha různými způsoby:</span><span class="sxs-lookup"><span data-stu-id="62e6b-151">These classes, however, differ from Visual Basic tuples and the **System.ValueTuple** generic types in a number of ways:</span></span>

- <span data-ttu-id="62e6b-152">Elementy **řazené kolekce členů** třídy jsou vlastnosti s názvem `Item1`, `Item2`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="62e6b-152">The elements of the **Tuple** classes are properties named `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="62e6b-153">V jazyce Visual Basic řazených kolekcí členů a **ValueTuple** pole jsou typy, elementy řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="62e6b-153">In Visual Basic tuples and the **ValueTuple** types, tuple elements are fields.</span></span>

- <span data-ttu-id="62e6b-154">Nelze přiřadit řádkům elementy **řazené kolekce členů** instance nebo **ValueTuple** instance.</span><span class="sxs-lookup"><span data-stu-id="62e6b-154">You cannot assign meaningful names to the elements of a **Tuple** instance or of a **ValueTuple** instance.</span></span> <span data-ttu-id="62e6b-155">Visual Basic umožňuje přiřadit názvy, které komunikují význam pole.</span><span class="sxs-lookup"><span data-stu-id="62e6b-155">Visual Basic allows you to assign names that communicate the meaning of the fields.</span></span>

- <span data-ttu-id="62e6b-156">Vlastnosti **řazené kolekce členů** instance jsou jen pro čtení, jsou neměnné řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="62e6b-156">The properties of a **Tuple** instance are read-only; the tuples are immutable.</span></span> <span data-ttu-id="62e6b-157">V jazyce Visual Basic řazených kolekcí členů a **ValueTuple** typy, jsou řazené kolekce členů pole pro čtení a zápis; jsou měnitelný řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="62e6b-157">In Visual Basic tuples and the **ValueTuple** types, tuple fields are read-write; the tuples are mutable.</span></span>

- <span data-ttu-id="62e6b-158">Obecná **řazené kolekce členů** typy jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="62e6b-158">The generic **Tuple** types are reference types.</span></span> <span data-ttu-id="62e6b-159">Použití těchto **řazené kolekce členů** typy znamená přidělování objektů.</span><span class="sxs-lookup"><span data-stu-id="62e6b-159">Using these **Tuple** types means allocating objects.</span></span> <span data-ttu-id="62e6b-160">V aktivní cesty to může být měřitelný dopad na výkon vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="62e6b-160">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="62e6b-161">Řazené kolekce členů jazyka Visual Basic a **ValueTuple** typy jsou typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="62e6b-161">Visual Basic tuples and the **ValueTuple** types are value types.</span></span>

<span data-ttu-id="62e6b-162">Rozšiřující metody v <xref:System.TupleExtensions> třída usnadňují převod mezi řazených kolekcí členů jazyka Visual Basic a .NET **řazené kolekce členů** objekty.</span><span class="sxs-lookup"><span data-stu-id="62e6b-162">Extension methods in the <xref:System.TupleExtensions> class make it easy to convert between Visual Basic tuples and .NET **Tuple** objects.</span></span> <span data-ttu-id="62e6b-163">**ToTuple** metoda převede řazené kolekce členů jazyka Visual Basic .NET **řazené kolekce členů** objekt a **ToValueTuple** metoda převede .NET **řazené kolekce členů** objekt řazené kolekce členů jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="62e6b-163">The **ToTuple** method converts a Visual Basic tuple to a .NET **Tuple** object, and the **ToValueTuple** method converts a .NET **Tuple** object to a Visual Basic tuple.</span></span>

<span data-ttu-id="62e6b-164">Následující příklad vytvoří řazenou kolekci členů, převede ji na .NET **řazené kolekce členů** objekt a převede ji zpět do Visual Basic řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="62e6b-164">The following example creates a tuple, converts it to a .NET **Tuple** object, and converts it back to a Visual Basic tuple.</span></span> <span data-ttu-id="62e6b-165">V příkladu pak porovná tato řazené kolekce členů s původní, abyste zajistili, že jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="62e6b-165">The example then compares this tuple with the original one to ensure that they are equal.</span></span>

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a><span data-ttu-id="62e6b-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="62e6b-166">See also</span></span>

[<span data-ttu-id="62e6b-167">Referenční dokumentace jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62e6b-167">Visual Basic Language Reference</span></span>](index.md)  
