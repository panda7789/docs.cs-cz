---
title: 'Postupy: používání bloku Try-Catch k zachycování výjimek'
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
ms.openlocfilehash: 852df5cb3eeea2ee5fa44ddce2f97e9c4f8d8b5a
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46699310"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="ae483-102">Postup používání bloku try/catch k zachycování výjimek</span><span class="sxs-lookup"><span data-stu-id="ae483-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="ae483-103">Umístit na části kódu, který může vyvolat výjimky v `try` bloku a místo kód, který zpracovává výjimky v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="ae483-103">Place the sections of code that might throw exceptions in a `try` block and place code that handles exceptions in a `catch` block.</span></span> <span data-ttu-id="ae483-104">`catch` Blok je řada příkazů pomocí klíčového slova začínající `catch`následovaný typ výjimky a akce, jež mají být provedeny.</span><span class="sxs-lookup"><span data-stu-id="ae483-104">The `catch` block is a series of statements beginning with the keyword `catch`, followed by an exception type and an action to be taken.</span></span>

<span data-ttu-id="ae483-105">Následující příklad kódu používá `try` / `catch` bloku catch možnou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="ae483-105">The following code example uses a `try`/`catch` block to catch a possible exception.</span></span> <span data-ttu-id="ae483-106">`Main` Obsahuje metodu `try` blokovat s <xref:System.IO.StreamReader> volá příkaz, který otevře soubor dat `data.txt` a zapíše řetězec ze souboru.</span><span class="sxs-lookup"><span data-stu-id="ae483-106">The `Main` method contains a `try` block with a <xref:System.IO.StreamReader> statement that opens a data file called `data.txt` and writes a string from the file.</span></span> <span data-ttu-id="ae483-107">Následující `try` blok je `catch` blok, který zachytí jakoukoli výjimku, která je výsledkem `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="ae483-107">Following the `try` block is a `catch` block that catches any exception that results from the `try` block.</span></span>

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="ae483-108">Modul common language runtime zachytí výjimky, které nejsou zachyceny v bloku catch.</span><span class="sxs-lookup"><span data-stu-id="ae483-108">The common language runtime catches exceptions that are not caught by a catch block.</span></span> <span data-ttu-id="ae483-109">V závislosti na konfiguraci modulu runtime se zobrazí dialogové okno ladění, program se zastaví provádění a zobrazí se dialogové okno s informací o výjimce nebo chybu je tisknout do STDERR.</span><span class="sxs-lookup"><span data-stu-id="ae483-109">Depending on how the runtime is configured, a debug dialog box appears, or the program stops executing and a dialog box with exception information appears, or an error is printed out to STDERR.</span></span>

> [!NOTE] 
> <span data-ttu-id="ae483-110">Téměř libovolném řádku kódu může způsobit výjimku, zejména výjimky vyvolané modulem common language runtime, jako například <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="ae483-110">Almost any line of code can cause an exception, particularly exceptions that are thrown by the common language runtime itself, such as <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="ae483-111">Většina aplikací nemusíte řešit tyto výjimky, ale byste měli vědět tuto možnost při zápisu knihoven a využívat další uživatelé.</span><span class="sxs-lookup"><span data-stu-id="ae483-111">Most applications don't have to deal with these exceptions, but you should be aware of this possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="ae483-112">Návrhy toho, kdy k nastavení kódu v bloku Try, najdete v části [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="ae483-112">For suggestions on when to set code in a Try block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae483-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae483-113">See also</span></span>

- [<span data-ttu-id="ae483-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="ae483-114">Exceptions</span></span>](index.md)
