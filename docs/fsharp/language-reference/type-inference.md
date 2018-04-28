---
title: Odvození typu (F#)
description: 'Zjistěte, jak kompilátor jazyka F # odvodí typy hodnot, proměnné, parametry a návratové hodnoty.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: b5f7861c0a638baebfe72c9b4cf7dca119339ae3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="type-inference"></a><span data-ttu-id="54212-103">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="54212-103">Type Inference</span></span>

<span data-ttu-id="54212-104">Toto téma popisuje, jak kompilátor jazyka F # odvodí typy hodnot, proměnné, parametry a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="54212-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="54212-105">Odvození typu Obecné</span><span class="sxs-lookup"><span data-stu-id="54212-105">Type Inference in General</span></span>
<span data-ttu-id="54212-106">Představu o odvození typu je, že nemusíte určit typy F # konstrukce kromě při kompilátor nelze odvodit jednoznačně typu.</span><span class="sxs-lookup"><span data-stu-id="54212-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="54212-107">Vynechání explicitního typu informace neznamená, že F # je dynamicky zadávaných jazyk nebo jestli jsou hodnoty v jazyce F # slabě typované.</span><span class="sxs-lookup"><span data-stu-id="54212-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="54212-108">F # je staticky typové jazyk, což znamená, že kompilátor deduces přesném typu pro každou konstrukci během kompilace.</span><span class="sxs-lookup"><span data-stu-id="54212-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="54212-109">Pokud není k dispozici dostatek informací pro kompilátor odvodit typy každý konstrukce, musíte zadat informace o dalších typu, obvykle přidáním explicitního typu poznámky někde v kódu.</span><span class="sxs-lookup"><span data-stu-id="54212-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>


## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="54212-110">Odvození parametr a návratové typy</span><span class="sxs-lookup"><span data-stu-id="54212-110">Inference of Parameter and Return Types</span></span>
<span data-ttu-id="54212-111">V seznamu parametrů nemáte zadejte typ jednotlivé parametry.</span><span class="sxs-lookup"><span data-stu-id="54212-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="54212-112">A ještě, F # je staticky typové jazyk a tedy každých hodnota a výraz typu určit přesně v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="54212-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="54212-113">Pro tyto typy, které explicitně nezadáte kompilátor odvodí typ na základě kontextu.</span><span class="sxs-lookup"><span data-stu-id="54212-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="54212-114">Pokud typ není jinak zadán, je odvodit být obecný.</span><span class="sxs-lookup"><span data-stu-id="54212-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="54212-115">Pokud kód používá hodnotu nekonzistentně, tak, že neexistuje žádná jednoho odvodit typ, který splňuje všechny používá hodnoty, že kompilátor ohlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="54212-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="54212-116">Návratový typ funkce je určen podle typu poslední výraz ve funkci.</span><span class="sxs-lookup"><span data-stu-id="54212-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="54212-117">Například v následujícím kódu, typy parametrů `a` a `b` a návratový typ se odvodit být `int` protože literálové `100` je typu `int`.</span><span class="sxs-lookup"><span data-stu-id="54212-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="54212-118">Odvození typu můžete ovlivnit změnou literály.</span><span class="sxs-lookup"><span data-stu-id="54212-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="54212-119">Provedete-li `100` `uint32` připojením přípona `u`, typy `a`, `b`, a jsou návratovou hodnotu odvodit být `uint32`.</span><span class="sxs-lookup"><span data-stu-id="54212-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="54212-120">Také můžete ovlivnit odvození typu pomocí jiných objektů, které implikují typu, jako je například funkce a metody, které pracují se pouze konkrétní typ omezení.</span><span class="sxs-lookup"><span data-stu-id="54212-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="54212-121">Navíc můžete použít explicitní typ poznámky na funkci nebo metodu parametry a proměnné ve výrazech, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="54212-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="54212-122">Pokud dochází ke konfliktům mezi různé omezení výsledkem chyby.</span><span class="sxs-lookup"><span data-stu-id="54212-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="54212-123">Můžete také explicitně návratovou hodnotu funkce tím, že poskytuje anotaci typu po všech parametrů.</span><span class="sxs-lookup"><span data-stu-id="54212-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="54212-124">Častých případech, kde je užitečná, pokud parametr anotaci typu je, když tento parametr typu objektu a chcete použít členem.</span><span class="sxs-lookup"><span data-stu-id="54212-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a><span data-ttu-id="54212-125">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="54212-125">Automatic Generalization</span></span>
<span data-ttu-id="54212-126">Je-li kód funkce není závislá na typ parametru, kompilátor za parametr být obecný.</span><span class="sxs-lookup"><span data-stu-id="54212-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="54212-127">To se označuje jako *Automatická generalizace*, a může být výkonné podpory k psaní kódu obecné bez zvyšuje složitost.</span><span class="sxs-lookup"><span data-stu-id="54212-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="54212-128">Například následující funkce kombinuje dva parametry libovolného typu do řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="54212-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="54212-129">Je potřeba odvodit typ</span><span class="sxs-lookup"><span data-stu-id="54212-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="54212-130">Další informace</span><span class="sxs-lookup"><span data-stu-id="54212-130">Additional Information</span></span>
<span data-ttu-id="54212-131">Odvození typu je podrobně popsaná v další v specifikace jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="54212-131">Type inference is described in more detail in the F# Language Specification.</span></span>


## <a name="see-also"></a><span data-ttu-id="54212-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="54212-132">See Also</span></span>
[<span data-ttu-id="54212-133">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="54212-133">Automatic Generalization</span></span>](generics/automatic-generalization.md)
