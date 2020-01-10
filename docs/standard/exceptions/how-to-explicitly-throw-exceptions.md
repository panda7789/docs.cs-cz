---
title: 'Postupy: Explicitní generování výjimek'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
ms.openlocfilehash: 750da20b8c1c40901cc363ac0eff8af888821ce9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708859"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="9d12d-102">Postup explicitního vyvolání výjimek</span><span class="sxs-lookup"><span data-stu-id="9d12d-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="9d12d-103">Výjimku lze explicitně vyvolat pomocí C# [`throw`](../../csharp/language-reference/keywords/throw.md) nebo příkazu Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="9d12d-103">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="9d12d-104">Zachycenou výjimku můžete také vyvolat znovu pomocí příkazu `throw`.</span><span class="sxs-lookup"><span data-stu-id="9d12d-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="9d12d-105">Je vhodné postupovat při kódování pro přidání informací do výjimky, která se znovu vyvolala k poskytnutí dalších informací při ladění.</span><span class="sxs-lookup"><span data-stu-id="9d12d-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="9d12d-106">Následující příklad kódu používá `try`/`catch` blok k zachycení možného <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="9d12d-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="9d12d-107">Následující blok `try` je `catch` blok, který zachytává <xref:System.IO.FileNotFoundException> a zapisuje zprávu do konzoly, pokud datový soubor nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="9d12d-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="9d12d-108">Další příkaz je příkaz `throw`, který vyvolá nový <xref:System.IO.FileNotFoundException> a přidá do výjimky textové informace.</span><span class="sxs-lookup"><span data-stu-id="9d12d-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="9d12d-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d12d-109">See also</span></span>

- [<span data-ttu-id="9d12d-110">Výjimky</span><span class="sxs-lookup"><span data-stu-id="9d12d-110">Exceptions</span></span>](index.md)
