---
title: Atributy (F#)
description: 'Zjistěte, jak povolit F # atributy metadata, která má být použita pro programovací konstrukce.'
ms.date: 05/16/2016
ms.openlocfilehash: 107f5d9cbcce28c97fc5b738759ef27649fc45a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565422"
---
# <a name="attributes"></a><span data-ttu-id="4fdb3-103">Atributy</span><span class="sxs-lookup"><span data-stu-id="4fdb3-103">Attributes</span></span>

<span data-ttu-id="4fdb3-104">Atributy povolit metadata, která má být použita pro programovací konstrukce.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="4fdb3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fdb3-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="4fdb3-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fdb3-106">Remarks</span></span>

<span data-ttu-id="4fdb3-107">V předchozích syntaxe *cíl* je volitelný a pokud je k dispozici, určuje druh program entita, která se vztahuje na atribut.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="4fdb3-108">Platné hodnoty pro *cíl* jsou uvedené v tabulce, která se zobrazí později v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="4fdb3-109">*Název atributu* odkazuje na název (může být kvalifikovaný pomocí oborů názvů) typu atributu platný, s nebo bez přípona `Attribute` , obvykle se používá v názvech typ atributu.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="4fdb3-110">Například typ `ObsoleteAttribute` lze zkrátit těsně `Obsolete` v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="4fdb3-111">*Argumenty* jsou argumenty pro konstruktor pro typ atributu.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="4fdb3-112">Pokud atribut má výchozí konstruktor, můžete vynechat seznam argumentů a závorek.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-112">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="4fdb3-113">Atributy podporovat poziční argumenty a pojmenované argumenty.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="4fdb3-114">*Poziční argumenty* argumenty, které se používají v pořadí, ve kterém jsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="4fdb3-115">Pojmenované argumenty lze použít, pokud má atribut veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="4fdb3-116">Můžete nastavit tak, že pomocí následující syntaxe v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-116">You can set these by using the following syntax in the argument list.</span></span>

```
*property-name* = *property-value*
```

<span data-ttu-id="4fdb3-117">Taková vlastnost inicializacích může být v libovolném pořadí, ale se musí řídit všechny poziční argumenty.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="4fdb3-118">Následuje příklad atribut, který používá poziční argumentů a inicializacích vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-118">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="4fdb3-119">V tomto příkladu je atribut `DllImportAttribute`, zde použít ve zkráceném tvaru.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="4fdb3-120">První argument je parametr poziční a druhý je vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="4fdb3-121">Atributy jsou .NET programovací konstrukce, která umožňuje objekt známé jako *atribut* přidruženou typu nebo jiného programu elementu.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="4fdb3-122">Element program, do které se použije atribut se označuje jako *atribut target*.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="4fdb3-123">Atribut obvykle obsahuje metadata o cíli.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="4fdb3-124">V tomto kontextu může být metadata žádná data o typu než jeho polí a členy.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="4fdb3-125">Atributy v jazyce F # lze použít pro následující programovací konstrukce: funkce, metody, sestavení, moduly, typy (třídy, záznamy, struktury, rozhraní, delegáti, výčty, sjednocení a tak dále), konstruktory, vlastnosti, pole, parametry, Zadejte parametry a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="4fdb3-126">Atributy nejsou povoleny na `let` vazby uvnitř tříd, výrazy a výrazy pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="4fdb3-127">Deklaraci atributu se obvykle zobrazuje přímo před deklaraci atribut target.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="4fdb3-128">Více deklarací atribut je možné společně, a to takto.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-128">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="4fdb3-129">V době běhu pomocí reflexe .NET můžete dotazovat atributy.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="4fdb3-130">Je možné deklarovat několik atributů jednotlivě, jako v předchozím příkladu kódu, nebo je možné deklarovat v jedné sadě závorky a pokud používáte středníkem oddělte jednotlivé atributy a konstruktory, jak je vidět tady.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="4fdb3-131">Obvykle došlo k atributy patří `Obsolete` atribut atributy pro aspekty zabezpečení, atributy pro podporu modelu COM, atributy, které se týkají vlastnictví kódu a atributy, která určuje, zda lze serializovat typu.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="4fdb3-132">Následující příklad ukazuje použití `Obsolete` atribut.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="4fdb3-133">Pro atribut cíle `assembly` a `module`, použijete atributy nejvyšší úrovně `do` vazby ve vašem sestavení.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="4fdb3-134">Můžete použít slovo `assembly` nebo `module` v deklaraci atributu, následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-134">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="4fdb3-135">Pokud je cílem atributu pro atribut u vynechat `do` vazby, kompilátor jazyka F # se pokusí určit atribut target, která je vhodná pro tento atribut.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="4fdb3-136">Mnoho atribut třídy mají atribut typu `System.AttributeUsageAttribute` , který obsahuje informace o možných cíle pro tento atribut podporována.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="4fdb3-137">Pokud `System.AttributeUsageAttribute` označuje, že atribut podporuje funkce jako cíle atribut se provede chcete použít pro hlavní vstupní bod programu.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="4fdb3-138">Pokud `System.AttributeUsageAttribute` označuje, že atribut podporuje sestavení jako cíle kompilátor trvá atribut, který chcete použít pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="4fdb3-139">Většina atributy se nevztahují na funkce a sestavení, ale v případech, kde udělají, je atribut prováděné chcete použít pro hlavní funkce programu.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="4fdb3-140">Pokud cílový atribut je explicitně zadána, atribut se používá k zadané cílové.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="4fdb3-141">I když není nutné obvykle zadat atribut cíle explicitně, platné hodnoty pro *cíl* v atributu, které jsou uvedeny v následující tabulce, společně s příklady využití.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="4fdb3-142">Atribut target</span><span class="sxs-lookup"><span data-stu-id="4fdb3-142">Attribute target</span></span></td>
    <th><span data-ttu-id="4fdb3-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fdb3-143">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="4fdb3-144">sestavení</span><span class="sxs-lookup"><span data-stu-id="4fdb3-144">assembly</span></span></td>
    <td><span data-ttu-id="4fdb3-145">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span><span class="sxs-lookup"><span data-stu-id="4fdb3-145">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="4fdb3-146">return</span><span class="sxs-lookup"><span data-stu-id="4fdb3-146">return</span></span></td>
    <td><span data-ttu-id="4fdb3-147">' umožní function1 x: [<return: Obsolete>] int = x + 1</span><span class="sxs-lookup"><span data-stu-id="4fdb3-147">`let function1 x : [<return: Obsolete>] int = x + 1`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="4fdb3-148">pole</span><span class="sxs-lookup"><span data-stu-id="4fdb3-148">field</span></span></td>
    <td><span data-ttu-id="4fdb3-149">"[<field: DefaultValue>] val měnitelný x: int.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-149">`[<field: DefaultValue>] val mutable x: int`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="4fdb3-150">property</span><span class="sxs-lookup"><span data-stu-id="4fdb3-150">property</span></span></td>
    <td><span data-ttu-id="4fdb3-151">"[<property: Obsolete>] to. MyProperty = x.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-151">`[<property: Obsolete>] this.MyProperty = x`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="4fdb3-152">Param</span><span class="sxs-lookup"><span data-stu-id="4fdb3-152">param</span></span></td>
    <td><span data-ttu-id="4fdb3-153">člen to. MyMethod ([<param: Out>] x: ref<int>) = x: = 10</span><span class="sxs-lookup"><span data-stu-id="4fdb3-153">`member this.MyMethod([<param: Out>] x : ref<int>) = x := 10`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="4fdb3-154">– typ</span><span class="sxs-lookup"><span data-stu-id="4fdb3-154">type</span></span></td>
    <td><span data-ttu-id="4fdb3-155">
        ```
        [<type: StructLayout(Sequential)>] zadejte MyStruct = struktura x: y bajtů: int end ```
    </span><span class="sxs-lookup"><span data-stu-id="4fdb3-155">
        ```
        [<type: StructLayout(Sequential)>] type MyStruct = struct x : byte y : int end ```
    </span></span></td> 
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="4fdb3-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fdb3-156">See Also</span></span>

[<span data-ttu-id="4fdb3-157">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="4fdb3-157">F# Language Reference</span></span>](index.md)
