---
title: 'Postupy: Explicitní generování výjimek'
description: Zjistěte, jak v rozhraní .NET vyvolat výjimku explicitně pomocí příkazu throw jazyka C# nebo příkazu Visual Basic throw.
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
ms.openlocfilehash: 2dd939f9edd58ba91ea74df5d6930087849f0560
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662781"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="7af36-103">Postup explicitního vyvolání výjimek</span><span class="sxs-lookup"><span data-stu-id="7af36-103">How to explicitly throw exceptions</span></span>

<span data-ttu-id="7af36-104">Výjimku lze explicitně vyvolat pomocí jazyka C# [`throw`](../../csharp/language-reference/keywords/throw.md) nebo [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) příkazu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7af36-104">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="7af36-105">Zachycenou výjimku můžete také vyvolat znovu pomocí `throw` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7af36-105">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="7af36-106">Je vhodné postupovat při kódování pro přidání informací do výjimky, která se znovu vyvolala k poskytnutí dalších informací při ladění.</span><span class="sxs-lookup"><span data-stu-id="7af36-106">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="7af36-107">Následující příklad kódu používá `try` / `catch` blok k zachycení možného <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="7af36-107">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="7af36-108">Po `try` bloku je `catch` blok, který zachytává <xref:System.IO.FileNotFoundException> a zapisuje zprávu do konzoly, pokud datový soubor nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="7af36-108">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="7af36-109">Další příkaz je `throw` příkaz, který vyvolá novou <xref:System.IO.FileNotFoundException> a přidá do výjimky textové informace.</span><span class="sxs-lookup"><span data-stu-id="7af36-109">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="7af36-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7af36-110">See also</span></span>

- [<span data-ttu-id="7af36-111">Výjimky</span><span class="sxs-lookup"><span data-stu-id="7af36-111">Exceptions</span></span>](index.md)
