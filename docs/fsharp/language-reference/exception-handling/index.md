---
title: Zpracování výjimek (F#)
description: 'Seznámíte se základy zpracování výjimek v F # a odkazy na výrazy a funkce pro zpracování výjimek.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 37b33f9387956ee462ff4977dd4ba34a82e89ec6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="exception-handling"></a><span data-ttu-id="eea09-103">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="eea09-103">Exception Handling</span></span>

<span data-ttu-id="eea09-104">Tato část obsahuje informace o zpracování podpory v jazyce F # výjimek.</span><span class="sxs-lookup"><span data-stu-id="eea09-104">This section contains information about exception handling support in the F# language.</span></span>


## <a name="exception-handling-basics"></a><span data-ttu-id="eea09-105">Základy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="eea09-105">Exception Handling Basics</span></span>
<span data-ttu-id="eea09-106">Zpracovávání výjimek v jazyce je standardním způsobem zpracovávat chybové stavy v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eea09-106">Exception handling is the standard way of handling error conditions in the .NET Framework.</span></span> <span data-ttu-id="eea09-107">Proto kterémkoli jazyce platformy .NET musí podporovat tento mechanismus, včetně F #.</span><span class="sxs-lookup"><span data-stu-id="eea09-107">Thus, any .NET language must support this mechanism, including F#.</span></span> <span data-ttu-id="eea09-108">*Výjimka* je objekt, který zapouzdří informace o chybě.</span><span class="sxs-lookup"><span data-stu-id="eea09-108">An *exception* is an object that encapsulates information about an error.</span></span> <span data-ttu-id="eea09-109">Pokud dojde k chybám, výjimky jsou provádění pravidelných a nevyskytla se zastaví.</span><span class="sxs-lookup"><span data-stu-id="eea09-109">When errors occur, exceptions are raised and regular execution stops.</span></span> <span data-ttu-id="eea09-110">Místo toho modul runtime vyhledá příslušnou obslužnou rutinu pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="eea09-110">Instead, the runtime searches for an appropriate handler for the exception.</span></span> <span data-ttu-id="eea09-111">Hledání se spustí v aktuální funkce a pokračuje až zásobníku prostřednictvím vrstvy volající, dokud nebude nalezen odpovídající obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="eea09-111">The search starts in the current function, and proceeds up the stack through the layers of callers until a matching handler is found.</span></span> <span data-ttu-id="eea09-112">Pak je spustit obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="eea09-112">Then the handler is executed.</span></span>

<span data-ttu-id="eea09-113">Kromě toho je oddělen zásobníku, modul runtime provede žádný kód v `finally` bloky, chcete-li zaručit, že jsou objekty během procesu unwinding správně vyčištěna.</span><span class="sxs-lookup"><span data-stu-id="eea09-113">In addition, as the stack is unwound, the runtime executes any code in `finally` blocks, to guarantee that objects are cleaned up correctly during the unwinding process.</span></span>


## <a name="related-topics"></a><span data-ttu-id="eea09-114">Související témata</span><span class="sxs-lookup"><span data-stu-id="eea09-114">Related Topics</span></span>

|<span data-ttu-id="eea09-115">Název</span><span class="sxs-lookup"><span data-stu-id="eea09-115">Title</span></span>|<span data-ttu-id="eea09-116">Popis</span><span class="sxs-lookup"><span data-stu-id="eea09-116">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="eea09-117">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="eea09-117">Exception Types</span></span>](exception-types.md)|<span data-ttu-id="eea09-118">Popisuje, jak deklarovat typ výjimky.</span><span class="sxs-lookup"><span data-stu-id="eea09-118">Describes how to declare an exception type.</span></span>|
|[<span data-ttu-id="eea09-119">Výjimky: `try...with` výraz</span><span class="sxs-lookup"><span data-stu-id="eea09-119">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)|<span data-ttu-id="eea09-120">Popisuje konstrukce jazyk, který podporuje zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="eea09-120">Describes the language construct that supports exception handling.</span></span>|
|[<span data-ttu-id="eea09-121">Výjimky: `try...finally` výraz</span><span class="sxs-lookup"><span data-stu-id="eea09-121">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)|<span data-ttu-id="eea09-122">Popisuje konstrukce jazyk, který umožňuje spuštění kódu čištění jako zásobníku unwinds, když je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="eea09-122">Describes the language construct that enables you to execute clean-up code as the stack unwinds when an exception is thrown.</span></span>|
|[<span data-ttu-id="eea09-123">Výjimky: `raise` – funkce</span><span class="sxs-lookup"><span data-stu-id="eea09-123">Exceptions: the `raise` Function</span></span>](the-raise-Function.md)|<span data-ttu-id="eea09-124">Popisuje, jak má být vyvolána výjimka objekt.</span><span class="sxs-lookup"><span data-stu-id="eea09-124">Describes how to throw an exception object.</span></span>|
|[<span data-ttu-id="eea09-125">Výjimky: `failwith` – funkce</span><span class="sxs-lookup"><span data-stu-id="eea09-125">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)|<span data-ttu-id="eea09-126">Popisuje, jak vygenerovat k obecné výjimce F #.</span><span class="sxs-lookup"><span data-stu-id="eea09-126">Describes how to generate a general F# exception.</span></span>|
|[<span data-ttu-id="eea09-127">Výjimky: `invalidArg` – funkce</span><span class="sxs-lookup"><span data-stu-id="eea09-127">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)|<span data-ttu-id="eea09-128">Popisuje, jak generovat výjimku neplatný argument.</span><span class="sxs-lookup"><span data-stu-id="eea09-128">Describes how to generate an invalid argument exception.</span></span>|
