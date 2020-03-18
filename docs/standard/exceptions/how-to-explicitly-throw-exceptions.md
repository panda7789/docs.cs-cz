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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708859"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="08568-102">Jak explicitně vyvolat výjimky</span><span class="sxs-lookup"><span data-stu-id="08568-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="08568-103">Můžete explicitně vyvolat výjimku [`throw`](../../csharp/language-reference/keywords/throw.md) pomocí C# [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) nebo Visual Basic prohlášení.</span><span class="sxs-lookup"><span data-stu-id="08568-103">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="08568-104">Můžete také vyvolat zachycené výjimky znovu pomocí příkazu. `throw`</span><span class="sxs-lookup"><span data-stu-id="08568-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="08568-105">Je vhodné kódování praxe přidat informace o výjimce, která je znovu vyvolána poskytnout další informace při ladění.</span><span class="sxs-lookup"><span data-stu-id="08568-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="08568-106">Následující příklad kódu `try` / `catch` používá blok zachytit <xref:System.IO.FileNotFoundException>možné .</span><span class="sxs-lookup"><span data-stu-id="08568-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="08568-107">Následující `try` blok je `catch` blok, <xref:System.IO.FileNotFoundException> který zachytí a zapíše zprávu do konzoly, pokud datový soubor nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="08568-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="08568-108">Dalším příkazem `throw` je příkaz, který <xref:System.IO.FileNotFoundException> vyvolá nový a přidá textové informace k výjimce.</span><span class="sxs-lookup"><span data-stu-id="08568-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="08568-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="08568-109">See also</span></span>

- [<span data-ttu-id="08568-110">Výjimky</span><span class="sxs-lookup"><span data-stu-id="08568-110">Exceptions</span></span>](index.md)
