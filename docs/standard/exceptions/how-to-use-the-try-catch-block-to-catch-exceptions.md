---
title: 'Postupy: Používání bloku Try/Catch k zachycování výjimek'
description: Použijte blok try k zahrnutí příkazů, které mohou vyvolat nebo vyvolat výjimku. Umístěte příkazy pro zpracování výjimek v jednom nebo více blocích catch.
ms.date: 02/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
ms.openlocfilehash: 60ed213ea777fe35873fd1e67555b7506e3ca587
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768908"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="3947f-104">Jak zachytit výjimky pomocí bloku try/catch</span><span class="sxs-lookup"><span data-stu-id="3947f-104">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="3947f-105">Umístěte jakékoli příkazy kódu, které mohou vyvolat nebo vyvolat výjimku v `try` bloku a umístit příkazy používané pro zpracování výjimky nebo výjimek v jednom nebo více `catch` blocích pod `try` blokem.</span><span class="sxs-lookup"><span data-stu-id="3947f-105">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="3947f-106">Každý `catch` blok zahrnuje typ výjimky a může obsahovat další příkazy potřebné ke zpracování tohoto typu výjimky.</span><span class="sxs-lookup"><span data-stu-id="3947f-106">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="3947f-107">V následujícím příkladu <xref:System.IO.StreamReader> otevře soubor s názvem *data.txt* a načte řádek ze souboru.</span><span class="sxs-lookup"><span data-stu-id="3947f-107">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="3947f-108">Vzhledem k tomu, že kód může vyvolat některou ze tří výjimek, je umístěn v `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="3947f-108">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="3947f-109">Tři `catch` bloky zachytí výjimky a zpracovávají je zobrazením výsledků do konzoly.</span><span class="sxs-lookup"><span data-stu-id="3947f-109">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

<span data-ttu-id="3947f-110">Modul CLR (Common Language Runtime) zachytává výjimky, které nejsou zpracovávány `catch` bloky.</span><span class="sxs-lookup"><span data-stu-id="3947f-110">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="3947f-111">Pokud je výjimka zachycena modulem CLR, může dojít k jednomu z následujících výsledků v závislosti na konfiguraci CLR:</span><span class="sxs-lookup"><span data-stu-id="3947f-111">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="3947f-112">Zobrazí se dialogové okno **ladění** .</span><span class="sxs-lookup"><span data-stu-id="3947f-112">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="3947f-113">Program zastaví provádění a zobrazí se dialogové okno s informacemi o výjimce.</span><span class="sxs-lookup"><span data-stu-id="3947f-113">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="3947f-114">Chyba se tiskne do [standardního výstupního datového proudu chyb](xref:System.Console.Error).</span><span class="sxs-lookup"><span data-stu-id="3947f-114">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="3947f-115">Většina kódu může vyvolat výjimku a některé výjimky, například <xref:System.OutOfMemoryException> , mohou být vyvolány samotným modulem CLR kdykoli.</span><span class="sxs-lookup"><span data-stu-id="3947f-115">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="3947f-116">I když se aplikace nevyžadují k tomu, aby se s těmito výjimkami musely zabývat, pamatujte na to, že při psaní knihoven, které budou používat ostatní</span><span class="sxs-lookup"><span data-stu-id="3947f-116">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="3947f-117">Návrhy na to, kdy nastavit kód v `try` bloku, najdete v tématu [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="3947f-117">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3947f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3947f-118">See also</span></span>

- [<span data-ttu-id="3947f-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="3947f-119">Exceptions</span></span>](index.md)
- [<span data-ttu-id="3947f-120">Zpracování vstupně-výstupních chyb v .NET</span><span class="sxs-lookup"><span data-stu-id="3947f-120">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
