---
title: Atributy
description: Zjistěte, F# jak atributy umožňují použít metadata pro programovací konstrukci.
ms.date: 05/16/2016
ms.openlocfilehash: c9691a13ff1e9e892e93a967136a99849da25f1f
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567502"
---
# <a name="attributes"></a><span data-ttu-id="26b3e-103">Atributy</span><span class="sxs-lookup"><span data-stu-id="26b3e-103">Attributes</span></span>

<span data-ttu-id="26b3e-104">Atributy umožňují použít metadata pro programovací konstrukci.</span><span class="sxs-lookup"><span data-stu-id="26b3e-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="26b3e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26b3e-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="26b3e-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26b3e-106">Remarks</span></span>

<span data-ttu-id="26b3e-107">V předchozí syntaxi je *cíl* nepovinný a, pokud je k dispozici, určuje druh entity programu, na kterou se atribut vztahuje.</span><span class="sxs-lookup"><span data-stu-id="26b3e-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="26b3e-108">V tabulce, která se objeví později v tomto dokumentu, se zobrazí platné hodnoty pro *cíl* .</span><span class="sxs-lookup"><span data-stu-id="26b3e-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="26b3e-109">*Název atributu* odkazuje na název (případně kvalifikovaný pro obory názvů) platného typu atributu, s příponou `Attribute` , která se obvykle používá v názvech typů atributů.</span><span class="sxs-lookup"><span data-stu-id="26b3e-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="26b3e-110">Například typ `ObsoleteAttribute` může být zkrácen na pouze `Obsolete` v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="26b3e-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="26b3e-111">*Argumenty* jsou argumenty konstruktoru pro typ atributu.</span><span class="sxs-lookup"><span data-stu-id="26b3e-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="26b3e-112">Pokud má atribut výchozí konstruktor, seznam argumentů a kulaté závorky lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="26b3e-112">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="26b3e-113">Atributy podporují Poziční argumenty i pojmenované argumenty.</span><span class="sxs-lookup"><span data-stu-id="26b3e-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="26b3e-114">*Poziční argumenty* jsou argumenty, které jsou používány v pořadí, ve kterém jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="26b3e-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="26b3e-115">Pojmenované argumenty lze použít, pokud má atribut veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="26b3e-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="26b3e-116">Můžete je nastavit pomocí následující syntaxe v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="26b3e-116">You can set these by using the following syntax in the argument list.</span></span>

```
*property-name* = *property-value*
```

<span data-ttu-id="26b3e-117">Tyto inicializace vlastností mohou být v libovolném pořadí, ale musí následovat za libovolnými pozičními argumenty.</span><span class="sxs-lookup"><span data-stu-id="26b3e-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="26b3e-118">Následuje příklad atributu, který používá poziční argumenty a inicializace vlastností.</span><span class="sxs-lookup"><span data-stu-id="26b3e-118">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="26b3e-119">V tomto příkladu je `DllImportAttribute`atribut použit v zkráceném formátu.</span><span class="sxs-lookup"><span data-stu-id="26b3e-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="26b3e-120">První argument je poziční parametr a druhý je vlastnost.</span><span class="sxs-lookup"><span data-stu-id="26b3e-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="26b3e-121">Atributy jsou programovací konstrukce .NET, která umožňuje objekt známý jako *atribut* , který má být přidružen k typu nebo jinému prvku programu.</span><span class="sxs-lookup"><span data-stu-id="26b3e-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="26b3e-122">Prvek program, pro který je atribut použit, je označován jako *cíl atributu*.</span><span class="sxs-lookup"><span data-stu-id="26b3e-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="26b3e-123">Atribut obvykle obsahuje metadata o jeho cíli.</span><span class="sxs-lookup"><span data-stu-id="26b3e-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="26b3e-124">V tomto kontextu metadata mohou být jakákoli data o jiném typu než jeho pole a členové.</span><span class="sxs-lookup"><span data-stu-id="26b3e-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="26b3e-125">Atributy v F# lze použít u následujících programovacích konstrukcí: funkce, metody, sestavení, moduly, typy (třídy, záznamy, struktury, rozhraní, delegáti, výčty, sjednocení atd.), konstruktory, vlastnosti, pole, parametry, parametry typu a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="26b3e-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="26b3e-126">Atributy nejsou povoleny u `let` vazeb uvnitř tříd, výrazů nebo výrazů pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="26b3e-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="26b3e-127">Obvykle se deklarace atributu zobrazuje přímo před deklarací cíle atributu.</span><span class="sxs-lookup"><span data-stu-id="26b3e-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="26b3e-128">V následujícím příkladu lze použít více deklarací atributů.</span><span class="sxs-lookup"><span data-stu-id="26b3e-128">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="26b3e-129">Můžete zadat dotaz na atributy za běhu pomocí reflexe rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="26b3e-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="26b3e-130">Můžete deklarovat více atributů jednotlivě, jako v předchozím příkladu kódu, nebo je můžete deklarovat v jedné sadě hranatých závorek, pokud použijete středník pro oddělení jednotlivých atributů a konstruktorů, jak je znázorněno zde.</span><span class="sxs-lookup"><span data-stu-id="26b3e-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="26b3e-131">Obvykle zjištěné atributy zahrnují `Obsolete` atribut, atributy pro požadavky na zabezpečení, atributy pro podporu modelu COM, atributy, které se vztahují k vlastnictví kódu, a atributy, které označují, zda lze typ serializovat.</span><span class="sxs-lookup"><span data-stu-id="26b3e-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="26b3e-132">Následující příklad demonstruje použití `Obsolete` atributu.</span><span class="sxs-lookup"><span data-stu-id="26b3e-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="26b3e-133">Pro cíle `assembly` atributů a `module`použijte atributy pro vazbu nejvyšší úrovně `do` v sestavení.</span><span class="sxs-lookup"><span data-stu-id="26b3e-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="26b3e-134">Můžete zahrnout slovo `assembly` nebo `module` v deklaraci atributu následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="26b3e-134">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="26b3e-135">Pokud vynecháte cíl atributu pro atribut aplikovaný na `do` vazbu, F# kompilátor se pokusí určit cíl atributu, který dává smysl pro tento atribut.</span><span class="sxs-lookup"><span data-stu-id="26b3e-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="26b3e-136">Mnoho tříd atributů má atribut typu `System.AttributeUsageAttribute` , který obsahuje informace o možných cílech podporovaných pro tento atribut.</span><span class="sxs-lookup"><span data-stu-id="26b3e-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="26b3e-137">`System.AttributeUsageAttribute` Pokud určuje, že atribut podporuje funkce jako cíle, atribut je použit pro hlavní vstupní bod programu.</span><span class="sxs-lookup"><span data-stu-id="26b3e-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="26b3e-138">Pokud je `System.AttributeUsageAttribute` indikováno, že atribut podporuje sestavení jako cíle, kompilátor vezme atribut, který má být použit pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="26b3e-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="26b3e-139">Většina atributů se nevztahuje na funkce i sestavení, ale v případech, kdy jsou, se atribut povede pro použití v hlavní funkci programu.</span><span class="sxs-lookup"><span data-stu-id="26b3e-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="26b3e-140">Pokud je cíl atributu explicitně zadán, je atribut použit pro zadaný cíl.</span><span class="sxs-lookup"><span data-stu-id="26b3e-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="26b3e-141">Přestože nemusíte obvykle explicitně určovat cíl atributu, platné hodnoty pro *cíl* v atributu jsou uvedeny v následující tabulce, spolu s příklady použití.</span><span class="sxs-lookup"><span data-stu-id="26b3e-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="26b3e-142">Cíl atributu</span><span class="sxs-lookup"><span data-stu-id="26b3e-142">Attribute target</span></span></td>
    <th><span data-ttu-id="26b3e-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="26b3e-143">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="26b3e-144">sestavení</span><span class="sxs-lookup"><span data-stu-id="26b3e-144">assembly</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]</code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="26b3e-145">return</span><span class="sxs-lookup"><span data-stu-id="26b3e-145">return</span></span></td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1</code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="26b3e-146">pole</span><span class="sxs-lookup"><span data-stu-id="26b3e-146">field</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int</code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="26b3e-147">property</span><span class="sxs-lookup"><span data-stu-id="26b3e-147">property</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x</code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="26b3e-148">bajty</span><span class="sxs-lookup"><span data-stu-id="26b3e-148">param</span></span></td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="26b3e-149">– typ</span><span class="sxs-lookup"><span data-stu-id="26b3e-149">type</span></span></td>
    <td>
        <pre lang="fsharp"><code>
[&lt;type: StructLayout(Sequential)&gt;] 
type MyStruct = 
struct 
x : byte
y : int
end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="26b3e-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26b3e-150">See also</span></span>

- [<span data-ttu-id="26b3e-151">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="26b3e-151">F# Language Reference</span></span>](index.md)
