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
ms.openlocfilehash: 213ab53c68a37ac0ba5f337a1d6fc32bfe6f8989
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970908"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="c7707-102">Postup použití bloku finally.</span><span class="sxs-lookup"><span data-stu-id="c7707-102">How to use finally blocks</span></span>

<span data-ttu-id="c7707-103">Když dojde k výjimce, zastaví provádění a ovládací prvek dostane k obslužné rutině příslušné výjimky.</span><span class="sxs-lookup"><span data-stu-id="c7707-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="c7707-104">To často znamená, že se přeskočí řádky kódu, který očekáváte, že má být proveden.</span><span class="sxs-lookup"><span data-stu-id="c7707-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="c7707-105">Některé vyčištění prostředků, jako je například zavření souboru, je nutné provést i v případě, že dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="c7707-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="c7707-106">K tomuto účelu můžete použít `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="c7707-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="c7707-107">A `finally` vždy provede blok, bez ohledu na to, zda je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c7707-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="c7707-108">Následující příklad kódu používá `try` / `catch` bloku catch <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="c7707-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="c7707-109">`Main` Metoda vytvoří dvě pole a pokusí se zkopírujte jeden na druhý.</span><span class="sxs-lookup"><span data-stu-id="c7707-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="c7707-110">Vytvoří akci <xref:System.ArgumentOutOfRangeException> a bude chyba zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="c7707-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="c7707-111">`finally` Blok se spustí bez ohledu na to výsledek akce kopírování.</span><span class="sxs-lookup"><span data-stu-id="c7707-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="c7707-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7707-112">See also</span></span>

- [<span data-ttu-id="c7707-113">Výjimky</span><span class="sxs-lookup"><span data-stu-id="c7707-113">Exceptions</span></span>](index.md)
