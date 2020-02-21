---
title: Atributy
description: Zjistěte, F# jak atributy umožňují použít metadata pro programovací konstrukci.
ms.date: 02/19/2020
ms.openlocfilehash: 77b84713ab9360166b3634d406993cf209c8a623
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543635"
---
# <a name="attributes"></a><span data-ttu-id="37231-103">Atributy</span><span class="sxs-lookup"><span data-stu-id="37231-103">Attributes</span></span>

<span data-ttu-id="37231-104">Atributy umožňují použít metadata pro programovací konstrukci.</span><span class="sxs-lookup"><span data-stu-id="37231-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="37231-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37231-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="37231-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37231-106">Remarks</span></span>

<span data-ttu-id="37231-107">V předchozí syntaxi je *cíl* nepovinný a, pokud je k dispozici, určuje druh entity programu, na kterou se atribut vztahuje.</span><span class="sxs-lookup"><span data-stu-id="37231-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="37231-108">V tabulce, která se objeví později v tomto dokumentu, se zobrazí platné hodnoty pro *cíl* .</span><span class="sxs-lookup"><span data-stu-id="37231-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="37231-109">*Název atributu* odkazuje na název (případně kvalifikovaný pro obory názvů) platného typu atributu s příponou nebo bez přípony `Attribute`, která se obvykle používá v názvech typů atributů.</span><span class="sxs-lookup"><span data-stu-id="37231-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="37231-110">Například typ `ObsoleteAttribute` může být zkrácen na pouze `Obsolete` v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="37231-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="37231-111">*Argumenty* jsou argumenty konstruktoru pro typ atributu.</span><span class="sxs-lookup"><span data-stu-id="37231-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="37231-112">Pokud má atribut konstruktor bez parametrů, lze seznam argumentů a kulaté závorky vynechat.</span><span class="sxs-lookup"><span data-stu-id="37231-112">If an attribute has a parameterless constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="37231-113">Atributy podporují Poziční argumenty i pojmenované argumenty.</span><span class="sxs-lookup"><span data-stu-id="37231-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="37231-114">*Poziční argumenty* jsou argumenty, které jsou používány v pořadí, ve kterém jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="37231-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="37231-115">Pojmenované argumenty lze použít, pokud má atribut veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="37231-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="37231-116">Můžete je nastavit pomocí následující syntaxe v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="37231-116">You can set these by using the following syntax in the argument list.</span></span>

```fsharp
property-name = property-value
```

<span data-ttu-id="37231-117">Tyto inicializace vlastností mohou být v libovolném pořadí, ale musí následovat za libovolnými pozičními argumenty.</span><span class="sxs-lookup"><span data-stu-id="37231-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="37231-118">Následuje příklad atributu, který používá poziční argumenty a inicializace vlastností:</span><span class="sxs-lookup"><span data-stu-id="37231-118">The following is an example of an attribute that uses positional arguments and property initializations:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="37231-119">V tomto příkladu je atribut `DllImportAttribute`, který se používá v zkráceném formátu.</span><span class="sxs-lookup"><span data-stu-id="37231-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="37231-120">První argument je poziční parametr a druhý je vlastnost.</span><span class="sxs-lookup"><span data-stu-id="37231-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="37231-121">Atributy jsou programovací konstrukce .NET, která umožňuje objekt známý jako *atribut* , který má být přidružen k typu nebo jinému prvku programu.</span><span class="sxs-lookup"><span data-stu-id="37231-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="37231-122">Prvek program, pro který je atribut použit, je označován jako *cíl atributu*.</span><span class="sxs-lookup"><span data-stu-id="37231-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="37231-123">Atribut obvykle obsahuje metadata o jeho cíli.</span><span class="sxs-lookup"><span data-stu-id="37231-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="37231-124">V tomto kontextu metadata mohou být jakákoli data o jiném typu než jeho pole a členové.</span><span class="sxs-lookup"><span data-stu-id="37231-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="37231-125">Atributy v F# lze použít u následujících programovacích konstrukcí: funkce, metody, sestavení, moduly, typy (třídy, záznamy, struktury, rozhraní, delegáti, výčty, sjednocení atd.), konstruktory, vlastnosti, pole, parametry, parametry typu a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="37231-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="37231-126">Atributy nejsou povoleny u vazeb `let` v rámci tříd, výrazů nebo výrazů pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="37231-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="37231-127">Obvykle se deklarace atributu zobrazuje přímo před deklarací cíle atributu.</span><span class="sxs-lookup"><span data-stu-id="37231-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="37231-128">Deklarace více atributů lze použít společně následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="37231-128">Multiple attribute declarations can be used together, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="37231-129">Můžete zadat dotaz na atributy za běhu pomocí reflexe rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="37231-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="37231-130">Můžete deklarovat více atributů jednotlivě, jako v předchozím příkladu kódu, nebo je můžete deklarovat v jedné sadě hranatých závorek, pokud použijete středník pro oddělení jednotlivých atributů a konstruktorů, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="37231-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="37231-131">Obvykle zjištěné atributy zahrnují atribut `Obsolete`, atributy pro požadavky na zabezpečení, atributy pro podporu modelu COM, atributy, které se vztahují k vlastnictví kódu a atributy, které označují, zda lze typ serializovat.</span><span class="sxs-lookup"><span data-stu-id="37231-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="37231-132">Následující příklad ukazuje použití atributu `Obsolete`.</span><span class="sxs-lookup"><span data-stu-id="37231-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="37231-133">Pro cíle atributů `assembly` a `module`použijete atributy na `do` vazbu na nejvyšší úrovni v sestavení.</span><span class="sxs-lookup"><span data-stu-id="37231-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="37231-134">Do deklarace atributu můžete zahrnout slovo `assembly` nebo `module` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="37231-134">You can include the word `assembly` or `module` in the attribute declaration, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="37231-135">Pokud vynecháte cíl atributu pro atribut, který je použit pro `do` vazby, F# kompilátor se pokusí určit cíl atributu, který dává smysl pro tento atribut.</span><span class="sxs-lookup"><span data-stu-id="37231-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="37231-136">Mnoho tříd atributů má atribut typu `System.AttributeUsageAttribute`, který obsahuje informace o možných cílech podporovaných pro tento atribut.</span><span class="sxs-lookup"><span data-stu-id="37231-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="37231-137">Pokud `System.AttributeUsageAttribute` označuje, že atribut podporuje funkce jako cíle, atribut je pořízen pro použití pro hlavní vstupní bod programu.</span><span class="sxs-lookup"><span data-stu-id="37231-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="37231-138">Pokud `System.AttributeUsageAttribute` označuje, že atribut podporuje sestavení jako cíle, kompilátor vezme atribut, který má být použit pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="37231-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="37231-139">Většina atributů se nevztahuje na funkce i sestavení, ale v případech, kdy jsou, se atribut povede pro použití v hlavní funkci programu.</span><span class="sxs-lookup"><span data-stu-id="37231-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="37231-140">Pokud je cíl atributu explicitně zadán, je atribut použit pro zadaný cíl.</span><span class="sxs-lookup"><span data-stu-id="37231-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="37231-141">Přestože nemusíte obvykle explicitně určovat cíl atributu, platné hodnoty pro *cíl* v atributu spolu s příklady použití jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="37231-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute along with examples of usage are shown in the following table:</span></span>

<table>
  <tr>
    <th><span data-ttu-id="37231-142">Cíl atributu</span><span class="sxs-lookup"><span data-stu-id="37231-142">Attribute target</span></span></td>
    <th><span data-ttu-id="37231-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="37231-143">Example</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="37231-144">sestavení</span><span class="sxs-lookup"><span data-stu-id="37231-144">assembly</span></span></td>
    <td><pre><code class="lang-fsharp">[&lt;assembly: AssemblyVersion("1.0.0.0")&gt;]</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="37231-145">return</span><span class="sxs-lookup"><span data-stu-id="37231-145">return</span></span></td>
    <td><pre><code class="lang-fsharp">let function1 x : [&lt;return: MyCustomAttributeThatWorksOnReturns&gt;] int = x + 1</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="37231-146">pole</span><span class="sxs-lookup"><span data-stu-id="37231-146">field</span></span></td>
    <td><pre><code class="lang-fsharp">[&lt;DefaultValue&gt;] val mutable x: int</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="37231-147">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="37231-147">property</span></span></td>
    <td><pre><code class="lang-fsharp">[&lt;Obsolete&gt;] this.MyProperty = x</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="37231-148">bajty</span><span class="sxs-lookup"><span data-stu-id="37231-148">param</span></span></td>
    <td><pre><code class="lang-fsharp">member this.MyMethod([&lt;Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="37231-149">type</span><span class="sxs-lookup"><span data-stu-id="37231-149">type</span></span></td>
    <td>
        <pre><code class="lang-fsharp">
[&lt;type: StructLayout(LayoutKind.Sequential)&gt;]
type MyStruct =
  struct
    val x : byte
    val y : int
  end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="37231-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37231-150">See also</span></span>

- [<span data-ttu-id="37231-151">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="37231-151">F# Language Reference</span></span>](index.md)
