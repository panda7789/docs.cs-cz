---
title: Typy výjimek
description: Zjistěte, jak definovat a používat F# typy výjimek.
ms.date: 05/16/2016
ms.openlocfilehash: ed721dd0dc46a486fafeac2fa4c096800995ccb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772720"
---
# <a name="exception-types"></a><span data-ttu-id="4fd2f-103">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="4fd2f-103">Exception Types</span></span>

<span data-ttu-id="4fd2f-104">Existují dvě kategorie výjimek v F#: typy výjimek .NET a F# typy výjimek.</span><span class="sxs-lookup"><span data-stu-id="4fd2f-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="4fd2f-105">Toto téma popisuje, jak definovat a používat F# typy výjimek.</span><span class="sxs-lookup"><span data-stu-id="4fd2f-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="4fd2f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fd2f-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="4fd2f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fd2f-107">Remarks</span></span>

<span data-ttu-id="4fd2f-108">V předchozí syntaxi *typ výjimky* je název nové F# typ výjimky a *typ argumentu* představuje typ argumentu, který může být zadán při vyvolání výjimky tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="4fd2f-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="4fd2f-109">Můžete zadat více argumentů pomocí typu řazené kolekce členů pro *typ argumentu*.</span><span class="sxs-lookup"><span data-stu-id="4fd2f-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="4fd2f-110">Typické definici F# výjimek má následující podobu.</span><span class="sxs-lookup"><span data-stu-id="4fd2f-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="4fd2f-111">Výjimka tohoto typu můžete vygenerovat pomocí `raise` fungovat, následovně.</span><span class="sxs-lookup"><span data-stu-id="4fd2f-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="4fd2f-112">Můžete použít F# typ výjimky přímo do filtrů v `try...with` výrazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4fd2f-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="4fd2f-113">Typ výjimky, který definujete pomocí `exception` – klíčové slovo v F# je nový typ, který dědí z `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="4fd2f-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fd2f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fd2f-114">See also</span></span>

- [<span data-ttu-id="4fd2f-115">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="4fd2f-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="4fd2f-116">Výjimky: `raise` – funkce</span><span class="sxs-lookup"><span data-stu-id="4fd2f-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="4fd2f-117">Hierarchie výjimek</span><span class="sxs-lookup"><span data-stu-id="4fd2f-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)