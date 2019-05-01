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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5183a854ee2b7462ecc27786a5fc0697565194c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970856"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="a408a-102">Postup používání bloku try/catch k zachycování výjimek</span><span class="sxs-lookup"><span data-stu-id="a408a-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="a408a-103">Umístěte všechny příkazy, které mohou vyvolat nebo vyvolat výjimku `try` bloku a používá ke zpracování výjimky nebo výjimky v jednom nebo více příkazů místo `catch` níže uvedených bloků `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="a408a-103">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="a408a-104">Každý `catch` blok obsahuje typ výjimky a může obsahovat další příkazy potřebné ke zpracování tohoto typu výjimky.</span><span class="sxs-lookup"><span data-stu-id="a408a-104">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="a408a-105">V následujícím příkladu <xref:System.IO.StreamReader> otevře soubor s názvem *data.txt* a načte řádek ze souboru.</span><span class="sxs-lookup"><span data-stu-id="a408a-105">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="a408a-106">Protože kód může vyvolat výjimky tři, je umístěný v `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="a408a-106">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="a408a-107">Tři `catch` bloky catch výjimky a mohli je zpracovat zobrazením výsledků do konzoly.</span><span class="sxs-lookup"><span data-stu-id="a408a-107">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="a408a-108">Common Language Runtime (CLR) zachytává výjimky není zpracována `catch` bloky.</span><span class="sxs-lookup"><span data-stu-id="a408a-108">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="a408a-109">Pokud je výjimka zachycena platformou CLR, jednu z následujících výsledků může dojít v závislosti na vaší konfiguraci modulu CLR:</span><span class="sxs-lookup"><span data-stu-id="a408a-109">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="a408a-110">A **ladění** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="a408a-110">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="a408a-111">Program se zastaví provádění a zobrazí se dialogové okno s informací o výjimce.</span><span class="sxs-lookup"><span data-stu-id="a408a-111">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="a408a-112">Chyba vytiskne na [standardní chybový proud výstup](xref:System.Console.Error).</span><span class="sxs-lookup"><span data-stu-id="a408a-112">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="a408a-113">Většinu kódu může vyvolat výjimku a výjimkami, jako je třeba <xref:System.OutOfMemoryException>, mohou být vyvolány pomocí modulu CLR, samotný kdykoli.</span><span class="sxs-lookup"><span data-stu-id="a408a-113">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="a408a-114">Když aplikace není nutné zacházet s těmito výjimkami, mějte na paměti možnost při zápisu knihoven a využívat další uživatelé.</span><span class="sxs-lookup"><span data-stu-id="a408a-114">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="a408a-115">Pro návrhy toho, kdy k nastavení kódu v `try` blokovat, najdete v článku [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="a408a-115">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a408a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a408a-116">See also</span></span>

[<span data-ttu-id="a408a-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="a408a-117">Exceptions</span></span>](index.md)  
[<span data-ttu-id="a408a-118">Zpracování chyb vstupně-výstupní operace v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="a408a-118">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
