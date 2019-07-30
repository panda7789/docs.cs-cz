---
title: Typy výjimek
description: Naučte se definovat a používat F# typy výjimek.
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630313"
---
# <a name="exception-types"></a><span data-ttu-id="d43af-103">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="d43af-103">Exception Types</span></span>

<span data-ttu-id="d43af-104">Existují dvě kategorie výjimek v F#: typy výjimek rozhraní .NET a F# typy výjimek.</span><span class="sxs-lookup"><span data-stu-id="d43af-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="d43af-105">Toto téma popisuje, jak definovat a používat F# typy výjimek.</span><span class="sxs-lookup"><span data-stu-id="d43af-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="d43af-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d43af-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="d43af-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d43af-107">Remarks</span></span>

<span data-ttu-id="d43af-108">V předchozí syntaxi je *Typ výjimky* název nového F# typu výjimky a *typ argumentu* představuje typ argumentu, který lze zadat při vyvolání výjimky tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="d43af-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="d43af-109">Můžete zadat více argumentů pomocí typu řazené kolekce členů pro *typ argumentu*.</span><span class="sxs-lookup"><span data-stu-id="d43af-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="d43af-110">Typická definice pro F# výjimku se podobá následujícímu.</span><span class="sxs-lookup"><span data-stu-id="d43af-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="d43af-111">Výjimku tohoto typu můžete vygenerovat pomocí `raise` funkce následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="d43af-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="d43af-112">Typ F# výjimky můžete použít přímo ve filtrech ve `try...with` výrazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d43af-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="d43af-113">Typ výjimky, který definujete pomocí `exception` klíčového slova v, F# je nový typ, který `System.Exception`dědí z.</span><span class="sxs-lookup"><span data-stu-id="d43af-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d43af-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d43af-114">See also</span></span>

- [<span data-ttu-id="d43af-115">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="d43af-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="d43af-116">Výjimky: `raise` funkce</span><span class="sxs-lookup"><span data-stu-id="d43af-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="d43af-117">Hierarchie výjimek</span><span class="sxs-lookup"><span data-stu-id="d43af-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
