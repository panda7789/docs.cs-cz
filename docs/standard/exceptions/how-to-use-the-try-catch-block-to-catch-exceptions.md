---
title: 'Postupy: zachycení výjimek pomocí bloku try-catch'
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708463"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="d9ae9-102">Jak zachytit výjimky pomocí bloku try/catch</span><span class="sxs-lookup"><span data-stu-id="d9ae9-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="d9ae9-103">Umístěte jakékoli příkazy kódu, které mohou vyvolat nebo vyvolat výjimku v bloku `try` a umístit příkazy používané pro zpracování výjimky nebo výjimek v jednom nebo více `catch` blocích pod blokem `try`.</span><span class="sxs-lookup"><span data-stu-id="d9ae9-103">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="d9ae9-104">Každý blok `catch` zahrnuje typ výjimky a může obsahovat další příkazy potřebné ke zpracování tohoto typu výjimky.</span><span class="sxs-lookup"><span data-stu-id="d9ae9-104">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="d9ae9-105">V následujícím příkladu <xref:System.IO.StreamReader> otevře soubor s názvem *data. txt* a načte řádek ze souboru.</span><span class="sxs-lookup"><span data-stu-id="d9ae9-105">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="d9ae9-106">Vzhledem k tomu, že kód může vyvolat některou ze tří výjimek, je umístěn do `try`ho bloku.</span><span class="sxs-lookup"><span data-stu-id="d9ae9-106">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="d9ae9-107">Tři `catch` bloky zachytit výjimky a zpracují je zobrazením výsledků do konzoly.</span><span class="sxs-lookup"><span data-stu-id="d9ae9-107">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

<span data-ttu-id="d9ae9-108">Modul CLR (Common Language Runtime) zachytává výjimky, které nejsou zpracovány `catch` bloky.</span><span class="sxs-lookup"><span data-stu-id="d9ae9-108">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="d9ae9-109">Pokud je výjimka zachycena modulem CLR, může dojít k jednomu z následujících výsledků v závislosti na konfiguraci CLR:</span><span class="sxs-lookup"><span data-stu-id="d9ae9-109">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="d9ae9-110">Zobrazí se dialogové okno **ladění** .</span><span class="sxs-lookup"><span data-stu-id="d9ae9-110">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="d9ae9-111">Program zastaví provádění a zobrazí se dialogové okno s informacemi o výjimce.</span><span class="sxs-lookup"><span data-stu-id="d9ae9-111">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="d9ae9-112">Chyba se tiskne do [standardního výstupního datového proudu chyb](xref:System.Console.Error).</span><span class="sxs-lookup"><span data-stu-id="d9ae9-112">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="d9ae9-113">Většina kódu může vyvolat výjimku a některé výjimky, jako je například <xref:System.OutOfMemoryException>, mohou být vyvolány samotným modulem CLR kdykoli.</span><span class="sxs-lookup"><span data-stu-id="d9ae9-113">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="d9ae9-114">I když se aplikace nevyžadují k tomu, aby se s těmito výjimkami musely zabývat, pamatujte na to, že při psaní knihoven, které budou používat ostatní</span><span class="sxs-lookup"><span data-stu-id="d9ae9-114">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="d9ae9-115">Návrhy na to, kdy nastavit kód v bloku `try`, najdete v tématu [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="d9ae9-115">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9ae9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9ae9-116">See also</span></span>

- [<span data-ttu-id="d9ae9-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="d9ae9-117">Exceptions</span></span>](index.md)
- [<span data-ttu-id="d9ae9-118">Zpracování vstupně-výstupních chyb v .NET</span><span class="sxs-lookup"><span data-stu-id="d9ae9-118">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
