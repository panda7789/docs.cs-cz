---
title: "Postupy: Používání bloků Finally"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 325be4836d661369326fbe3ea1f8b252bf251f3c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="0dfbf-102">Postup používání bloků finally</span><span class="sxs-lookup"><span data-stu-id="0dfbf-102">How to use finally blocks</span></span>

<span data-ttu-id="0dfbf-103">Když dojde k výjimce, provádění zastaví a řízení dostane do obslužné rutiny příslušné výjimky.</span><span class="sxs-lookup"><span data-stu-id="0dfbf-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="0dfbf-104">Často to znamená, že se vynechá řádků kódu, které chcete provést.</span><span class="sxs-lookup"><span data-stu-id="0dfbf-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="0dfbf-105">Některé vyčištění prostředků, jako je například zavření souboru, je potřeba udělat i v případě, že je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="0dfbf-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="0dfbf-106">Chcete-li to provést, můžete použít `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="0dfbf-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="0dfbf-107">A `finally` vždy provede bloku, bez ohledu na to, jestli je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="0dfbf-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="0dfbf-108">Následující příklad kódu používá `try` / `catch` bloku k zachycení <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="0dfbf-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="0dfbf-109">`Main` Metoda vytvoří dvě pole a pokusí se zkopírovat jeden na druhý.</span><span class="sxs-lookup"><span data-stu-id="0dfbf-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="0dfbf-110">Vytvoří akci <xref:System.ArgumentOutOfRangeException> a bude chyba zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0dfbf-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="0dfbf-111">`finally` Bloku spustí bez ohledu na to výsledek akce kopírování.</span><span class="sxs-lookup"><span data-stu-id="0dfbf-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="0dfbf-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="0dfbf-112">See Also</span></span>  
[<span data-ttu-id="0dfbf-113">Výjimky</span><span class="sxs-lookup"><span data-stu-id="0dfbf-113">Exceptions</span></span>](index.md)   
