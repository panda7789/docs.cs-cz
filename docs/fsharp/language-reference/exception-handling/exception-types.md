---
title: Typy výjimek (F#)
description: 'Zjistěte, jak definovat a používat výjimky typů F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 4462dd00ddf9524d1fd376ee1e73e81fcfd5d945
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564035"
---
# <a name="exception-types"></a><span data-ttu-id="52173-103">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="52173-103">Exception Types</span></span>

<span data-ttu-id="52173-104">Existují dvě kategorie výjimek v jazyce F #: typy .NET výjimky a výjimky typů F #.</span><span class="sxs-lookup"><span data-stu-id="52173-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="52173-105">Toto téma popisuje postup definice a používání výjimka typů F #.</span><span class="sxs-lookup"><span data-stu-id="52173-105">This topic describes how to define and use F# exception types.</span></span>


## <a name="syntax"></a><span data-ttu-id="52173-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52173-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="52173-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52173-107">Remarks</span></span>
<span data-ttu-id="52173-108">V předchozích syntaxi *typ výjimky* je název nové F # výjimka typu, a *typ argumentu* představuje typ argument, který můžete zadat při vyvolat výjimku tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="52173-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="52173-109">Můžete zadat několik argumentů pomocí typu řazené kolekce členů pro *typ argumentu*.</span><span class="sxs-lookup"><span data-stu-id="52173-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="52173-110">Typické definici výjimku F # vypadá přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="52173-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="52173-111">K výjimce typu můžete vygenerovat pomocí `raise` fungovat, následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="52173-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="52173-112">Typ výjimky F # můžete použít přímo do filtrů v `try...with` výrazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="52173-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="52173-113">Typ výjimky, které definujete s `exception` – klíčové slovo v F # je nový typ, který dědí z `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="52173-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>


## <a name="see-also"></a><span data-ttu-id="52173-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="52173-114">See Also</span></span>
[<span data-ttu-id="52173-115">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="52173-115">Exception Handling</span></span>](index.md)

[<span data-ttu-id="52173-116">Výjimky: `raise` – funkce</span><span class="sxs-lookup"><span data-stu-id="52173-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)

[<span data-ttu-id="52173-117">Hierarchie výjimek</span><span class="sxs-lookup"><span data-stu-id="52173-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
