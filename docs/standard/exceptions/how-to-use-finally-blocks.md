---
title: 'Postupy: Používání bloků Finally'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
ms.openlocfilehash: 44fbb53437c4c8f19a424227a167e2e268b77057
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708829"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="1bd54-102">Jak používat bloky finally</span><span class="sxs-lookup"><span data-stu-id="1bd54-102">How to use finally blocks</span></span>

<span data-ttu-id="1bd54-103">Pokud dojde k výjimce, spuštění se zastaví a ovládací prvek se přestává příslušné obslužné rutině výjimky.</span><span class="sxs-lookup"><span data-stu-id="1bd54-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="1bd54-104">To často znamená, že řádky kódu, které očekáváte, jsou vynechány.</span><span class="sxs-lookup"><span data-stu-id="1bd54-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="1bd54-105">Některé vyčištění prostředků, jako je například zavření souboru, je nutné provést i v případě, že je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1bd54-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="1bd54-106">K tomu můžete použít blok `finally`.</span><span class="sxs-lookup"><span data-stu-id="1bd54-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="1bd54-107">`finally` blok se vždy spustí bez ohledu na to, zda je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1bd54-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="1bd54-108">Následující příklad kódu používá `try`/`catch` blok k zachycení <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="1bd54-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="1bd54-109">Metoda `Main` vytvoří dvě pole a pokusí se je zkopírovat do druhé.</span><span class="sxs-lookup"><span data-stu-id="1bd54-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="1bd54-110">Akce vygeneruje <xref:System.ArgumentOutOfRangeException> a chyba se zapíše do konzoly.</span><span class="sxs-lookup"><span data-stu-id="1bd54-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="1bd54-111">`finally` blok se provede bez ohledu na výsledek akce kopírování.</span><span class="sxs-lookup"><span data-stu-id="1bd54-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="1bd54-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1bd54-112">See also</span></span>

- [<span data-ttu-id="1bd54-113">Výjimky</span><span class="sxs-lookup"><span data-stu-id="1bd54-113">Exceptions</span></span>](index.md)
