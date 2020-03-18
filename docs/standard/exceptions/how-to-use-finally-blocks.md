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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708829"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="fcf1b-102">Jak používat finally bloky</span><span class="sxs-lookup"><span data-stu-id="fcf1b-102">How to use finally blocks</span></span>

<span data-ttu-id="fcf1b-103">Dojde-li k výjimce, zastavení spuštění a ovládací prvek je dán a příslušné obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="fcf1b-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="fcf1b-104">To často znamená, že řádky kódu, které očekáváte, že budou provedeny jsou vynechány.</span><span class="sxs-lookup"><span data-stu-id="fcf1b-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="fcf1b-105">Některé vyčištění prostředků, jako je například zavření souboru, je třeba provést i v případě, že je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="fcf1b-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="fcf1b-106">Chcete-li to provést, `finally` můžete použít blok.</span><span class="sxs-lookup"><span data-stu-id="fcf1b-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="fcf1b-107">Blok `finally` se vždy spustí, bez ohledu na to, zda je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="fcf1b-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="fcf1b-108">Následující příklad kódu `try` / `catch` používá blok <xref:System.ArgumentOutOfRangeException>k zachycení .</span><span class="sxs-lookup"><span data-stu-id="fcf1b-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="fcf1b-109">Metoda `Main` vytvoří dvě pole a pokusí se zkopírovat jeden do druhého.</span><span class="sxs-lookup"><span data-stu-id="fcf1b-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="fcf1b-110">Akce generuje <xref:System.ArgumentOutOfRangeException> a chyba je zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="fcf1b-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="fcf1b-111">Blok `finally` se provede bez ohledu na výsledek akce kopírování.</span><span class="sxs-lookup"><span data-stu-id="fcf1b-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="fcf1b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="fcf1b-112">See also</span></span>

- [<span data-ttu-id="fcf1b-113">Výjimky</span><span class="sxs-lookup"><span data-stu-id="fcf1b-113">Exceptions</span></span>](index.md)
