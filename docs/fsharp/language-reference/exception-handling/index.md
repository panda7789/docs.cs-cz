---
title: Zpracování výjimek (F#)
description: 'Seznámíte se základy zpracování výjimek v F # a odkazy na výrazy a funkce pro zpracování výjimek.'
keywords: 'Visual f #, f #, funkční programování'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ad475c4a-d94e-47d9-b27b-3ff000b65f8e
ms.openlocfilehash: b61af66e0a70fdf9b86df37418c0284957d1f99e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="exception-handling"></a><span data-ttu-id="71ee9-104">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="71ee9-104">Exception Handling</span></span>

<span data-ttu-id="71ee9-105">Tato část obsahuje informace o zpracování podpory v jazyce F # výjimek.</span><span class="sxs-lookup"><span data-stu-id="71ee9-105">This section contains information about exception handling support in the F# language.</span></span>


## <a name="exception-handling-basics"></a><span data-ttu-id="71ee9-106">Základy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="71ee9-106">Exception Handling Basics</span></span>
<span data-ttu-id="71ee9-107">Zpracovávání výjimek v jazyce je standardním způsobem zpracovávat chybové stavy v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="71ee9-107">Exception handling is the standard way of handling error conditions in the .NET Framework.</span></span> <span data-ttu-id="71ee9-108">Proto kterémkoli jazyce platformy .NET musí podporovat tento mechanismus, včetně F #.</span><span class="sxs-lookup"><span data-stu-id="71ee9-108">Thus, any .NET language must support this mechanism, including F#.</span></span> <span data-ttu-id="71ee9-109">*Výjimka* je objekt, který zapouzdří informace o chybě.</span><span class="sxs-lookup"><span data-stu-id="71ee9-109">An *exception* is an object that encapsulates information about an error.</span></span> <span data-ttu-id="71ee9-110">Pokud dojde k chybám, výjimky jsou provádění pravidelných a nevyskytla se zastaví.</span><span class="sxs-lookup"><span data-stu-id="71ee9-110">When errors occur, exceptions are raised and regular execution stops.</span></span> <span data-ttu-id="71ee9-111">Místo toho modul runtime vyhledá příslušnou obslužnou rutinu pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="71ee9-111">Instead, the runtime searches for an appropriate handler for the exception.</span></span> <span data-ttu-id="71ee9-112">Hledání se spustí v aktuální funkce a pokračuje až zásobníku prostřednictvím vrstvy volající, dokud nebude nalezen odpovídající obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="71ee9-112">The search starts in the current function, and proceeds up the stack through the layers of callers until a matching handler is found.</span></span> <span data-ttu-id="71ee9-113">Pak je spustit obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="71ee9-113">Then the handler is executed.</span></span>

<span data-ttu-id="71ee9-114">Kromě toho je oddělen zásobníku, modul runtime provede žádný kód v `finally` bloky, chcete-li zaručit, že jsou objekty během procesu unwinding správně vyčištěna.</span><span class="sxs-lookup"><span data-stu-id="71ee9-114">In addition, as the stack is unwound, the runtime executes any code in `finally` blocks, to guarantee that objects are cleaned up correctly during the unwinding process.</span></span>


## <a name="related-topics"></a><span data-ttu-id="71ee9-115">Související témata</span><span class="sxs-lookup"><span data-stu-id="71ee9-115">Related Topics</span></span>

|<span data-ttu-id="71ee9-116">Název</span><span class="sxs-lookup"><span data-stu-id="71ee9-116">Title</span></span>|<span data-ttu-id="71ee9-117">Popis</span><span class="sxs-lookup"><span data-stu-id="71ee9-117">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="71ee9-118">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="71ee9-118">Exception Types</span></span>](exception-types.md)|<span data-ttu-id="71ee9-119">Popisuje, jak deklarovat typ výjimky.</span><span class="sxs-lookup"><span data-stu-id="71ee9-119">Describes how to declare an exception type.</span></span>|
|[<span data-ttu-id="71ee9-120">Výjimky: `try...with` výraz</span><span class="sxs-lookup"><span data-stu-id="71ee9-120">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)|<span data-ttu-id="71ee9-121">Popisuje konstrukce jazyk, který podporuje zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="71ee9-121">Describes the language construct that supports exception handling.</span></span>|
|[<span data-ttu-id="71ee9-122">Výjimky: `try...finally` výraz</span><span class="sxs-lookup"><span data-stu-id="71ee9-122">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)|<span data-ttu-id="71ee9-123">Popisuje konstrukce jazyk, který umožňuje spuštění kódu čištění jako zásobníku unwinds, když je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="71ee9-123">Describes the language construct that enables you to execute clean-up code as the stack unwinds when an exception is thrown.</span></span>|
|[<span data-ttu-id="71ee9-124">Výjimky: `raise` – funkce</span><span class="sxs-lookup"><span data-stu-id="71ee9-124">Exceptions: the `raise` Function</span></span>](the-raise-Function.md)|<span data-ttu-id="71ee9-125">Popisuje, jak má být vyvolána výjimka objekt.</span><span class="sxs-lookup"><span data-stu-id="71ee9-125">Describes how to throw an exception object.</span></span>|
|[<span data-ttu-id="71ee9-126">Výjimky: `failwith` – funkce</span><span class="sxs-lookup"><span data-stu-id="71ee9-126">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)|<span data-ttu-id="71ee9-127">Popisuje, jak vygenerovat k obecné výjimce F #.</span><span class="sxs-lookup"><span data-stu-id="71ee9-127">Describes how to generate a general F# exception.</span></span>|
|[<span data-ttu-id="71ee9-128">Výjimky: `invalidArg` – funkce</span><span class="sxs-lookup"><span data-stu-id="71ee9-128">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)|<span data-ttu-id="71ee9-129">Popisuje, jak generovat výjimku neplatný argument.</span><span class="sxs-lookup"><span data-stu-id="71ee9-129">Describes how to generate an invalid argument exception.</span></span>|
