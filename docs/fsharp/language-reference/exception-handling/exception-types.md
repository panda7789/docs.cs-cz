---
title: Typy výjimek
description: Zjistěte, jak definovat a používat F# typy výjimek.
ms.date: 05/16/2016
ms.openlocfilehash: b7203dc042c7207bca95cfd0372790bfe52e0226
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645570"
---
# <a name="exception-types"></a><span data-ttu-id="bc37b-103">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="bc37b-103">Exception Types</span></span>

<span data-ttu-id="bc37b-104">Existují dvě kategorie výjimek v F#: typy výjimek .NET a F# typy výjimek.</span><span class="sxs-lookup"><span data-stu-id="bc37b-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="bc37b-105">Toto téma popisuje, jak definovat a používat F# typy výjimek.</span><span class="sxs-lookup"><span data-stu-id="bc37b-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="bc37b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc37b-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="bc37b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc37b-107">Remarks</span></span>

<span data-ttu-id="bc37b-108">V předchozí syntaxi *typ výjimky* je název nové F# typ výjimky a *typ argumentu* představuje typ argumentu, který může být zadán při vyvolání výjimky tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="bc37b-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="bc37b-109">Můžete zadat více argumentů pomocí typu řazené kolekce členů pro *typ argumentu*.</span><span class="sxs-lookup"><span data-stu-id="bc37b-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="bc37b-110">Typické definici F# výjimek má následující podobu.</span><span class="sxs-lookup"><span data-stu-id="bc37b-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="bc37b-111">Výjimka tohoto typu můžete vygenerovat pomocí `raise` fungovat, následovně.</span><span class="sxs-lookup"><span data-stu-id="bc37b-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="bc37b-112">Můžete použít F# typ výjimky přímo do filtrů v `try...with` výrazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bc37b-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="bc37b-113">Typ výjimky, který definujete pomocí `exception` – klíčové slovo v F# je nový typ, který dědí z `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="bc37b-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc37b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc37b-114">See also</span></span>

- [<span data-ttu-id="bc37b-115">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="bc37b-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="bc37b-116">Výjimky: `raise` – funkce</span><span class="sxs-lookup"><span data-stu-id="bc37b-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="bc37b-117">Hierarchie výjimek</span><span class="sxs-lookup"><span data-stu-id="bc37b-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
