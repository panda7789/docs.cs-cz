---
title: "Typy výjimek (F#)"
description: "Zjistěte, jak definovat a používat výjimky typů F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e850205a-b8da-459e-8f6d-cb3510f8f173
ms.openlocfilehash: a0864218841396c0ebdf26c7585e0e5bb778f83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="exception-types"></a><span data-ttu-id="edf78-104">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="edf78-104">Exception Types</span></span>

<span data-ttu-id="edf78-105">Existují dvě kategorie výjimek v jazyce F #: typy .NET výjimky a výjimky typů F #.</span><span class="sxs-lookup"><span data-stu-id="edf78-105">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="edf78-106">Toto téma popisuje postup definice a používání výjimka typů F #.</span><span class="sxs-lookup"><span data-stu-id="edf78-106">This topic describes how to define and use F# exception types.</span></span>


## <a name="syntax"></a><span data-ttu-id="edf78-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edf78-107">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="edf78-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="edf78-108">Remarks</span></span>
<span data-ttu-id="edf78-109">V předchozích syntaxi *typ výjimky* je název nové F # výjimka typu, a *typ argumentu* představuje typ argument, který můžete zadat při vyvolat výjimku tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="edf78-109">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="edf78-110">Můžete zadat několik argumentů pomocí typu řazené kolekce členů pro *typ argumentu*.</span><span class="sxs-lookup"><span data-stu-id="edf78-110">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="edf78-111">Typické definici výjimku F # vypadá přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="edf78-111">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="edf78-112">K výjimce typu můžete vygenerovat pomocí `raise` fungovat, následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="edf78-112">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="edf78-113">Typ výjimky F # můžete použít přímo do filtrů v `try...with` výrazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="edf78-113">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="edf78-114">Typ výjimky, které definujete s `exception` – klíčové slovo v F # je nový typ, který dědí z `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="edf78-114">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>


## <a name="see-also"></a><span data-ttu-id="edf78-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="edf78-115">See Also</span></span>
[<span data-ttu-id="edf78-116">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="edf78-116">Exception Handling</span></span>](index.md)

[<span data-ttu-id="edf78-117">Výjimky: `raise` – funkce</span><span class="sxs-lookup"><span data-stu-id="edf78-117">Exceptions: the `raise` Function</span></span>](the-raise-function.md)

[<span data-ttu-id="edf78-118">Hierarchie výjimek</span><span class="sxs-lookup"><span data-stu-id="edf78-118">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
