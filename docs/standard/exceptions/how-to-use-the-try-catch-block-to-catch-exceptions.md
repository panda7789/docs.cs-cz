---
title: 'Postupy: zachycení výjimky pomocí bloku Try-Catch'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b169353752f6e6483a056cdc9dd8c3227b9ebeb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571446"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="db7ce-102">Jak zachytit výjimky pomocí bloku try/catch</span><span class="sxs-lookup"><span data-stu-id="db7ce-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="db7ce-103">Umístit na části kódu, který může vyvolat výjimky v `try` bloku a umístěte kód, který zpracovává výjimky v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="db7ce-103">Place the sections of code that might throw exceptions in a `try` block and place code that handles exceptions in a `catch` block.</span></span> <span data-ttu-id="db7ce-104">`catch` Blok je řada příkazů počínaje klíčové slovo `catch`, za nímž následují typ výjimky a akce, které mají být provedeny.</span><span class="sxs-lookup"><span data-stu-id="db7ce-104">The `catch` block is a series of statements beginning with the keyword `catch`, followed by an exception type and an action to be taken.</span></span>

<span data-ttu-id="db7ce-105">Následující příklad kódu používá `try` / `catch` blok k zachycení možné výjimky.</span><span class="sxs-lookup"><span data-stu-id="db7ce-105">The following code example uses a `try`/`catch` block to catch a possible exception.</span></span> <span data-ttu-id="db7ce-106">`Main` Metoda obsahuje `try` blokovat s <xref:System.IO.StreamReader> příkaz, který otevře datový soubor s názvem `data.txt` a zapisuje řetězec ze souboru.</span><span class="sxs-lookup"><span data-stu-id="db7ce-106">The `Main` method contains a `try` block with a <xref:System.IO.StreamReader> statement that opens a data file called `data.txt` and writes a string from the file.</span></span> <span data-ttu-id="db7ce-107">Následující `try` blok je `catch` blok, který zachytí jakoukoli výjimku, která je výsledkem `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="db7ce-107">Following the `try` block is a `catch` block that catches any exception that results from the `try` block.</span></span>

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="db7ce-108">Modul common language runtime zachytí výjimky, které nejsou zachytila bloku catch.</span><span class="sxs-lookup"><span data-stu-id="db7ce-108">The common language runtime catches exceptions that are not caught by a catch block.</span></span> <span data-ttu-id="db7ce-109">V závislosti na konfiguraci modulu runtime zobrazí se dialogové okno ladění, nebo program zastaví, provádění a zobrazí se dialogové okno s informací o výjimce nebo chybu se vytiskne na STDERR.</span><span class="sxs-lookup"><span data-stu-id="db7ce-109">Depending on how the runtime is configured, a debug dialog box appears, or the program stops executing and a dialog box with exception information appears, or an error is printed out to STDERR.</span></span>

> [!NOTE] 
> <span data-ttu-id="db7ce-110">Téměř každý řádek kódu může způsobit výjimku, zejména výjimky, které jsou vyvolány common language runtime samostatně, jako například <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="db7ce-110">Almost any line of code can cause an exception, particularly exceptions that are thrown by the common language runtime itself, such as <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="db7ce-111">Většina aplikací nemusí zabývat těmito výjimkami, ale byste měli vědět tuto možnost při zápisu knihoven pro použití jinými uživateli.</span><span class="sxs-lookup"><span data-stu-id="db7ce-111">Most applications don't have to deal with these exceptions, but you should be aware of this possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="db7ce-112">Návrhy, když chcete nastavit kód do bloku Try, najdete v části [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="db7ce-112">For suggestions on when to set code in a Try block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db7ce-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="db7ce-113">See Also</span></span>  
[<span data-ttu-id="db7ce-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="db7ce-114">Exceptions</span></span>](index.md)
