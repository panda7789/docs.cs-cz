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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dff1083256e24a35b7238ee5e8af6cb5743bc0ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571518"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="8c79f-102">Postup používání bloků finally</span><span class="sxs-lookup"><span data-stu-id="8c79f-102">How to use finally blocks</span></span>

<span data-ttu-id="8c79f-103">Když dojde k výjimce, provádění zastaví a řízení dostane do obslužné rutiny příslušné výjimky.</span><span class="sxs-lookup"><span data-stu-id="8c79f-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="8c79f-104">Často to znamená, že se vynechá řádků kódu, které chcete provést.</span><span class="sxs-lookup"><span data-stu-id="8c79f-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="8c79f-105">Některé vyčištění prostředků, jako je například zavření souboru, je potřeba udělat i v případě, že je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8c79f-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="8c79f-106">Chcete-li to provést, můžete použít `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="8c79f-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="8c79f-107">A `finally` vždy provede bloku, bez ohledu na to, jestli je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8c79f-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="8c79f-108">Následující příklad kódu používá `try` / `catch` bloku k zachycení <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="8c79f-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="8c79f-109">`Main` Metoda vytvoří dvě pole a pokusí se zkopírovat jeden na druhý.</span><span class="sxs-lookup"><span data-stu-id="8c79f-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="8c79f-110">Vytvoří akci <xref:System.ArgumentOutOfRangeException> a bude chyba zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="8c79f-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="8c79f-111">`finally` Bloku spustí bez ohledu na to výsledek akce kopírování.</span><span class="sxs-lookup"><span data-stu-id="8c79f-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="8c79f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c79f-112">See Also</span></span>  
[<span data-ttu-id="8c79f-113">Výjimky</span><span class="sxs-lookup"><span data-stu-id="8c79f-113">Exceptions</span></span>](index.md)   
