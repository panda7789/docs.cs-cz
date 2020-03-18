---
title: 'Postupy: Používání bloku Try/Catch k zachycování výjimek'
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
ms.openlocfilehash: 5a9218d394b76e897f4263708a10f1bc895ad4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708463"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="f9155-102">Jak použít blok try/catch k zachycení výjimek</span><span class="sxs-lookup"><span data-stu-id="f9155-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="f9155-103">Umístěte všechny příkazy kódu, které mohou `try` vyvolat nebo vyvolat výjimku v bloku a umístit `catch` příkazy `try` používané ke zpracování výjimky nebo výjimky v jednom nebo více bloků pod blok.</span><span class="sxs-lookup"><span data-stu-id="f9155-103">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="f9155-104">Každý `catch` blok obsahuje typ výjimky a může obsahovat další příkazy potřebné ke zpracování tohoto typu výjimky.</span><span class="sxs-lookup"><span data-stu-id="f9155-104">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="f9155-105">V následujícím příkladu <xref:System.IO.StreamReader> otevře soubor s názvem *data.txt* a načte řádek ze souboru.</span><span class="sxs-lookup"><span data-stu-id="f9155-105">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="f9155-106">Vzhledem k tomu, že kód může vyvolat některou ze tří výjimek, je umístěn v `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="f9155-106">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="f9155-107">Tři `catch` bloky zachytit výjimky a zpracovat je zobrazením výsledky do konzoly.</span><span class="sxs-lookup"><span data-stu-id="f9155-107">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

<span data-ttu-id="f9155-108">Common Language Runtime (CLR) zachytí `catch` výjimky, které nejsou zpracovány bloky.</span><span class="sxs-lookup"><span data-stu-id="f9155-108">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="f9155-109">Pokud je výjimka zachycena CLR, může dojít k jednomu z následujících výsledků v závislosti na konfiguraci CLR:</span><span class="sxs-lookup"><span data-stu-id="f9155-109">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="f9155-110">Zobrazí se dialogové okno **Ladění.**</span><span class="sxs-lookup"><span data-stu-id="f9155-110">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="f9155-111">Program zastaví provádění a zobrazí se dialogové okno s informacemi o výjimce.</span><span class="sxs-lookup"><span data-stu-id="f9155-111">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="f9155-112">Chyba se vytiskne do [výstupního datového proudu standardní chyby](xref:System.Console.Error).</span><span class="sxs-lookup"><span data-stu-id="f9155-112">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="f9155-113">Většina kódu může vyvolat výjimku a <xref:System.OutOfMemoryException>některé výjimky, jako je , může být vyvolána CLR sám kdykoli.</span><span class="sxs-lookup"><span data-stu-id="f9155-113">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="f9155-114">Zatímco aplikace nejsou nutné k řešení těchto výjimek, být vědomi možnosti při psaní knihoven, které mají být použity jinými uživateli.</span><span class="sxs-lookup"><span data-stu-id="f9155-114">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="f9155-115">Návrhy, kdy nastavit kód `try` v bloku, najdete v [tématu Doporučené postupy pro výjimky](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="f9155-115">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9155-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9155-116">See also</span></span>

- [<span data-ttu-id="f9155-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="f9155-117">Exceptions</span></span>](index.md)
- [<span data-ttu-id="f9155-118">Zpracování vstupně-v.I chyb v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="f9155-118">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
