---
title: Typy výjimek (F#)
description: 'Zjistěte, jak definovat a používat výjimky typů F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 6aaa5cd1b94f829b98d5aed5dcf6e30472a8b751
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="exception-types"></a><span data-ttu-id="e83b5-103">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="e83b5-103">Exception Types</span></span>

<span data-ttu-id="e83b5-104">Existují dvě kategorie výjimek v jazyce F #: typy .NET výjimky a výjimky typů F #.</span><span class="sxs-lookup"><span data-stu-id="e83b5-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="e83b5-105">Toto téma popisuje postup definice a používání výjimka typů F #.</span><span class="sxs-lookup"><span data-stu-id="e83b5-105">This topic describes how to define and use F# exception types.</span></span>


## <a name="syntax"></a><span data-ttu-id="e83b5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e83b5-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="e83b5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e83b5-107">Remarks</span></span>
<span data-ttu-id="e83b5-108">V předchozích syntaxi *typ výjimky* je název nové F # výjimka typu, a *typ argumentu* představuje typ argument, který můžete zadat při vyvolat výjimku tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="e83b5-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="e83b5-109">Můžete zadat několik argumentů pomocí typu řazené kolekce členů pro *typ argumentu*.</span><span class="sxs-lookup"><span data-stu-id="e83b5-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="e83b5-110">Typické definici výjimku F # vypadá přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="e83b5-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="e83b5-111">K výjimce typu můžete vygenerovat pomocí `raise` fungovat, následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e83b5-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="e83b5-112">Typ výjimky F # můžete použít přímo do filtrů v `try...with` výrazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e83b5-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="e83b5-113">Typ výjimky, které definujete s `exception` – klíčové slovo v F # je nový typ, který dědí z `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="e83b5-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>


## <a name="see-also"></a><span data-ttu-id="e83b5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e83b5-114">See Also</span></span>
[<span data-ttu-id="e83b5-115">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="e83b5-115">Exception Handling</span></span>](index.md)

[<span data-ttu-id="e83b5-116">Výjimky: `raise` – funkce</span><span class="sxs-lookup"><span data-stu-id="e83b5-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)

[<span data-ttu-id="e83b5-117">Hierarchie výjimek</span><span class="sxs-lookup"><span data-stu-id="e83b5-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
