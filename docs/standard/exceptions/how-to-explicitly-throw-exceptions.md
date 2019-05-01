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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1a8658999f08d295e76afc9df6ec8acd146abe2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970895"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="62a06-102">Jak explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="62a06-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="62a06-103">Můžete explicitně vyvolat výjimku pomocí `throw` příkazu.</span><span class="sxs-lookup"><span data-stu-id="62a06-103">You can explicitly throw an exception using the `throw` statement.</span></span> <span data-ttu-id="62a06-104">Můžete také vyvolá Zachycenou výjimku znovu pomocí `throw` příkazu.</span><span class="sxs-lookup"><span data-stu-id="62a06-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="62a06-105">Je dobrým zvykem přidejte informace o výjimce, která je znovu vyvolána k poskytnutí dalších informací při ladění.</span><span class="sxs-lookup"><span data-stu-id="62a06-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="62a06-106">Následující příklad kódu používá `try` / `catch` bloku catch možný výskyt <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="62a06-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="62a06-107">Následující `try` blok je `catch` blok, který zachytává <xref:System.IO.FileNotFoundException> a zapíše zprávu do konzoly, pokud datový soubor nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="62a06-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="62a06-108">Další příkaz je `throw` příkaz, který vyvolá novou <xref:System.IO.FileNotFoundException> a přidá informace o textu k výjimce.</span><span class="sxs-lookup"><span data-stu-id="62a06-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="62a06-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62a06-109">See also</span></span>

- [<span data-ttu-id="62a06-110">Výjimky</span><span class="sxs-lookup"><span data-stu-id="62a06-110">Exceptions</span></span>](index.md)
