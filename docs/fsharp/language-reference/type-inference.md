---
title: Odvození typu
description: Zjistěte, jak F# kompilátor odvodí typy hodnot, proměnných, parametrů a vrácených hodnot.
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630180"
---
# <a name="type-inference"></a><span data-ttu-id="a43f5-103">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="a43f5-103">Type Inference</span></span>

<span data-ttu-id="a43f5-104">Toto téma popisuje, jak F# kompilátor odvodí typy hodnot, proměnných, parametrů a vrácených hodnot.</span><span class="sxs-lookup"><span data-stu-id="a43f5-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="a43f5-105">Odvození typu obecně</span><span class="sxs-lookup"><span data-stu-id="a43f5-105">Type Inference in General</span></span>

<span data-ttu-id="a43f5-106">Účelem odvození typu je, že nemusíte určovat typy F# konstrukcí s výjimkou případů, kdy kompilátor nemůže jednoznačně odvodit typ.</span><span class="sxs-lookup"><span data-stu-id="a43f5-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="a43f5-107">Vynechání explicitních informací o typu neznamená F# , že je to dynamicky typový jazyk nebo že F# hodnoty v jsou slabě typované.</span><span class="sxs-lookup"><span data-stu-id="a43f5-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="a43f5-108">F#je jazyk staticky typu, což znamená, že kompilátor při kompilaci odvodit přesný typ pro každý konstruktor.</span><span class="sxs-lookup"><span data-stu-id="a43f5-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="a43f5-109">Není-li pro kompilátor k dispozici dostatek informací pro odvození typů každé konstrukce, je nutné zadat další informace o typu, obvykle přidáním explicitních anotací typu někam do kódu.</span><span class="sxs-lookup"><span data-stu-id="a43f5-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>

## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="a43f5-110">Odvození parametrů a návratových typů</span><span class="sxs-lookup"><span data-stu-id="a43f5-110">Inference of Parameter and Return Types</span></span>

<span data-ttu-id="a43f5-111">V seznamu parametrů není nutné zadávat typ každého parametru.</span><span class="sxs-lookup"><span data-stu-id="a43f5-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="a43f5-112">A dosud F# je jazyk staticky typu, a proto každá hodnota a výraz má v době kompilace určitý typ.</span><span class="sxs-lookup"><span data-stu-id="a43f5-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="a43f5-113">Pro typy, které neurčíte explicitně, kompilátor odvodí typ na základě kontextu.</span><span class="sxs-lookup"><span data-stu-id="a43f5-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="a43f5-114">Pokud není typ uveden jinak, je odvozena jako obecná.</span><span class="sxs-lookup"><span data-stu-id="a43f5-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="a43f5-115">Pokud kód používá hodnotu nekonzistentní, takovým způsobem, že neexistuje žádný odvozený typ, který splňuje všechna použití hodnoty, kompilátor ohlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="a43f5-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="a43f5-116">Návratový typ funkce je určen typem posledního výrazu ve funkci.</span><span class="sxs-lookup"><span data-stu-id="a43f5-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="a43f5-117">Například v `a` následujícím kódu jsou typy parametrů a `b` a návratový typ odvoditelné `int` , protože literál `100` je typu `int`.</span><span class="sxs-lookup"><span data-stu-id="a43f5-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="a43f5-118">Odvození typu můžete ovlivnit změnou literálů.</span><span class="sxs-lookup"><span data-stu-id="a43f5-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="a43f5-119">`u` `b` Pokudvytvoříte`a`připojením k příponě, jsou typy, a návratové hodnoty odvozeny `uint32`. `100` `uint32`</span><span class="sxs-lookup"><span data-stu-id="a43f5-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="a43f5-120">Odvození typu můžete také ovlivnit pomocí jiných konstrukcí, které zaznamenají omezení typu, jako jsou funkce a metody, které pracují pouze s konkrétním typem.</span><span class="sxs-lookup"><span data-stu-id="a43f5-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="a43f5-121">Můžete také použít explicitní anotace typu na parametry Function nebo Method nebo na proměnné ve výrazech, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="a43f5-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="a43f5-122">Při výskytu konfliktů mezi různými omezeními dojde k chybám.</span><span class="sxs-lookup"><span data-stu-id="a43f5-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="a43f5-123">Můžete také explicitně zadat návratovou hodnotu funkce poskytnutím anotace typu po všech parametrech.</span><span class="sxs-lookup"><span data-stu-id="a43f5-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="a43f5-124">Běžný případ, kdy je anotace typu užitečná pro parametr, je, když je parametr typem objektu a chcete použít člena.</span><span class="sxs-lookup"><span data-stu-id="a43f5-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a><span data-ttu-id="a43f5-125">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="a43f5-125">Automatic Generalization</span></span>

<span data-ttu-id="a43f5-126">Pokud kód funkce není závislý na typu parametru, kompilátor považuje parametr za obecný.</span><span class="sxs-lookup"><span data-stu-id="a43f5-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="a43f5-127">To se nazývá *Automatická generalizace*a může to být účinná podpora pro psaní obecného kódu bez zvýšené složitosti.</span><span class="sxs-lookup"><span data-stu-id="a43f5-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="a43f5-128">Například následující funkce kombinuje dva parametry libovolného typu do řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="a43f5-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="a43f5-129">Typ je odvozený.</span><span class="sxs-lookup"><span data-stu-id="a43f5-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="a43f5-130">Další informace</span><span class="sxs-lookup"><span data-stu-id="a43f5-130">Additional Information</span></span>

<span data-ttu-id="a43f5-131">Odvození typu je podrobněji popsáno ve specifikaci F# jazyka.</span><span class="sxs-lookup"><span data-stu-id="a43f5-131">Type inference is described in more detail in the F# Language Specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="a43f5-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a43f5-132">See also</span></span>

- [<span data-ttu-id="a43f5-133">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="a43f5-133">Automatic Generalization</span></span>](./generics/automatic-generalization.md)
