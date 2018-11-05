---
title: Odvození typu (F#)
description: Zjistěte, jak kompilátor F# odvodí typy hodnot, proměnné, parametry a návratové hodnoty.
ms.date: 05/16/2016
ms.openlocfilehash: fd826ac48fb9a70aa6f4ff746599c11b7e21a02e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43865693"
---
# <a name="type-inference"></a><span data-ttu-id="0fa5b-103">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="0fa5b-103">Type Inference</span></span>

<span data-ttu-id="0fa5b-104">Toto téma popisuje, jak kompilátor F# odvodí typy hodnot, proměnné, parametry a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="0fa5b-105">Odvození typu, obecné</span><span class="sxs-lookup"><span data-stu-id="0fa5b-105">Type Inference in General</span></span>

<span data-ttu-id="0fa5b-106">Představu o odvození typu je, že není nutné určit typy konstrukce F# s výjimkou případů, kdy kompilátor nemůže odvodit jednoznačně typ.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="0fa5b-107">Vynechání explicitního typu informace neznamená, že F# je jazyk dynamicky zadávaných nebo že jsou hodnoty v jazyce F# slabě typované.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="0fa5b-108">F# je staticky psaný jazyk, což znamená, že kompilátor odvodí přesný typ pro každou konstrukci během kompilace.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="0fa5b-109">Pokud není k dispozici dostatek informací pro kompilátor k odvození typů každý konstrukce, musíte zadat informace o dalších typu, obvykle tak, že přidáte anotace explicitního typu někde v kódu.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>

## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="0fa5b-110">Odvozování parametrů a návratové typy</span><span class="sxs-lookup"><span data-stu-id="0fa5b-110">Inference of Parameter and Return Types</span></span>

<span data-ttu-id="0fa5b-111">V seznamu parametrů není nutné zadat typ každého parametru.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="0fa5b-112">A ještě, F# je staticky psaný jazyk, a proto všechny hodnoty a výrazu má jednoznačného typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="0fa5b-113">Pro tyto typy, které explicitně nezadáte kompilátor odvodí typ na základě kontextu.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="0fa5b-114">Pokud typ není jinak zadán, je odvozen je obecný.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="0fa5b-115">Pokud tento kód použije hodnotu nekonzistentně, tak, že neexistuje žádné jeden odvodit typ, který splňuje všechna použití hodnoty, že kompilátor nahlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="0fa5b-116">Návratový typ funkce je určen podle typu posledního výrazu ve funkci.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="0fa5b-117">Například v následujícím kódu, typy parametrů `a` a `b` a návratový typ je odvozen bude `int` protože literál `100` je typu `int`.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="0fa5b-118">Odvození typu proměnné můžete ovlivnit tak, že změníte literály.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="0fa5b-119">Pokud provedete `100` `uint32` přidáním přípona `u`, typy `a`, `b`, a návratová hodnota jsou odvozena jako `uint32`.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="0fa5b-120">Můžete také ovlivnit odvození typu pomocí jiných objektů, které znamenají omezení typu, například funkcí a metod, které pracují s pouze určitého typu.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="0fa5b-121">Navíc můžete použít anotace explicitního typu funkce nebo metoda parametry a proměnné ve výrazech, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="0fa5b-122">Pokud dochází ke konfliktům mezi jiná omezení dojít k chybám.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="0fa5b-123">Můžete také explicitně určit návratové hodnoty funkce tím, že poskytuje anotaci typu všechny parametry.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="0fa5b-124">Běžný případ, kdy je užitečné u parametru anotaci typu je, když je parametr typu objektu a chcete, použijte člena.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a><span data-ttu-id="0fa5b-125">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="0fa5b-125">Automatic Generalization</span></span>

<span data-ttu-id="0fa5b-126">Pokud kód této funkce není závislá na typ parametru, kompilátor považuje za parametr je obecný.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="0fa5b-127">Tento postup se nazývá *Automatická generalizace*, a může být výkonná Podpora zápisu obecný kód bez zvýšení složitosti.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="0fa5b-128">Například následující funkce kombinuje dva parametry typu do řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="0fa5b-129">Typ je odvozen bude</span><span class="sxs-lookup"><span data-stu-id="0fa5b-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="0fa5b-130">Další informace</span><span class="sxs-lookup"><span data-stu-id="0fa5b-130">Additional Information</span></span>

<span data-ttu-id="0fa5b-131">Odvození typu je podrobněji popsané v ve specifikaci jazyka F#.</span><span class="sxs-lookup"><span data-stu-id="0fa5b-131">Type inference is described in more detail in the F# Language Specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fa5b-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fa5b-132">See also</span></span>

- [<span data-ttu-id="0fa5b-133">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="0fa5b-133">Automatic Generalization</span></span>](generics/automatic-generalization.md)
