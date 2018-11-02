---
title: Zpracování výjimek (F#)
description: Seznamte se se základy zpracování výjimek v F# a odkazy na výrazy a funkce pro zpracování výjimek.
ms.date: 05/16/2016
ms.openlocfilehash: fc89feb0d21bc823cb105e435413f8309cd6174c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "33564323"
---
# <a name="exception-handling"></a><span data-ttu-id="c0182-103">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="c0182-103">Exception Handling</span></span>

<span data-ttu-id="c0182-104">Tato část obsahuje informace o podpoře v zpracování výjimek F# jazyka.</span><span class="sxs-lookup"><span data-stu-id="c0182-104">This section contains information about exception handling support in the F# language.</span></span>


## <a name="exception-handling-basics"></a><span data-ttu-id="c0182-105">Základy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="c0182-105">Exception Handling Basics</span></span>
<span data-ttu-id="c0182-106">Zpracování výjimek je standardní způsob zpracování chyb v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0182-106">Exception handling is the standard way of handling error conditions in the .NET Framework.</span></span> <span data-ttu-id="c0182-107">To znamená, libovolný jazyk .NET musí podporovat tento mechanismus, včetně F#.</span><span class="sxs-lookup"><span data-stu-id="c0182-107">Thus, any .NET language must support this mechanism, including F#.</span></span> <span data-ttu-id="c0182-108">*Výjimka* je objekt, který zapouzdřuje informace o chybě.</span><span class="sxs-lookup"><span data-stu-id="c0182-108">An *exception* is an object that encapsulates information about an error.</span></span> <span data-ttu-id="c0182-109">Když dojde k chybám, výjimky jsou provádění pravidelných a nevyskytla se zastaví.</span><span class="sxs-lookup"><span data-stu-id="c0182-109">When errors occur, exceptions are raised and regular execution stops.</span></span> <span data-ttu-id="c0182-110">Místo toho modul runtime vyhledá odpovídající obslužná rutina výjimky.</span><span class="sxs-lookup"><span data-stu-id="c0182-110">Instead, the runtime searches for an appropriate handler for the exception.</span></span> <span data-ttu-id="c0182-111">Hledání začne v aktuální funkci a zásobníkem prostřednictvím vrstev volající pokračuje, dokud není nalezena odpovídající obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="c0182-111">The search starts in the current function, and proceeds up the stack through the layers of callers until a matching handler is found.</span></span> <span data-ttu-id="c0182-112">Pak je provedena obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="c0182-112">Then the handler is executed.</span></span>

<span data-ttu-id="c0182-113">Kromě toho, jak je zásobník odvinut, modul runtime spustí libovolný kód v `finally` bloky, chcete-li zaručit, že se objekty během odvíjení správně vyčistí.</span><span class="sxs-lookup"><span data-stu-id="c0182-113">In addition, as the stack is unwound, the runtime executes any code in `finally` blocks, to guarantee that objects are cleaned up correctly during the unwinding process.</span></span>


## <a name="related-topics"></a><span data-ttu-id="c0182-114">Související témata</span><span class="sxs-lookup"><span data-stu-id="c0182-114">Related Topics</span></span>

|<span data-ttu-id="c0182-115">Název</span><span class="sxs-lookup"><span data-stu-id="c0182-115">Title</span></span>|<span data-ttu-id="c0182-116">Popis</span><span class="sxs-lookup"><span data-stu-id="c0182-116">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="c0182-117">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="c0182-117">Exception Types</span></span>](exception-types.md)|<span data-ttu-id="c0182-118">Popisuje, jak deklarovat typ výjimky.</span><span class="sxs-lookup"><span data-stu-id="c0182-118">Describes how to declare an exception type.</span></span>|
|[<span data-ttu-id="c0182-119">Výjimky: `try...with` výraz</span><span class="sxs-lookup"><span data-stu-id="c0182-119">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)|<span data-ttu-id="c0182-120">Popisuje konstrukce jazyka, který podporuje zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="c0182-120">Describes the language construct that supports exception handling.</span></span>|
|[<span data-ttu-id="c0182-121">Výjimky: `try...finally` výraz</span><span class="sxs-lookup"><span data-stu-id="c0182-121">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)|<span data-ttu-id="c0182-122">Popisuje konstrukce jazyka, který můžete spustit kód pro vyčištění jako zásobník unwinds, když dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="c0182-122">Describes the language construct that enables you to execute clean-up code as the stack unwinds when an exception is thrown.</span></span>|
|[<span data-ttu-id="c0182-123">Výjimky: `raise` – funkce</span><span class="sxs-lookup"><span data-stu-id="c0182-123">Exceptions: the `raise` Function</span></span>](the-raise-Function.md)|<span data-ttu-id="c0182-124">Popisuje, jak vyvolat objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="c0182-124">Describes how to throw an exception object.</span></span>|
|[<span data-ttu-id="c0182-125">Výjimky: `failwith` – funkce</span><span class="sxs-lookup"><span data-stu-id="c0182-125">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)|<span data-ttu-id="c0182-126">Popisuje, jak generovat Obecné F# výjimky.</span><span class="sxs-lookup"><span data-stu-id="c0182-126">Describes how to generate a general F# exception.</span></span>|
|[<span data-ttu-id="c0182-127">Výjimky: `invalidArg` – funkce</span><span class="sxs-lookup"><span data-stu-id="c0182-127">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)|<span data-ttu-id="c0182-128">Popisuje, jak generovat výjimku neplatný argument.</span><span class="sxs-lookup"><span data-stu-id="c0182-128">Describes how to generate an invalid argument exception.</span></span>|
