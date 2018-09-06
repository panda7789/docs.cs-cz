---
title: 'Postupy: Používání specifických výjimek v bloku Catch'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3da35dae374018f0695f79022e83ad397e98cb88
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874781"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="9bbe8-102">Postup používání specifických výjimek v bloku catch</span><span class="sxs-lookup"><span data-stu-id="9bbe8-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="9bbe8-103">Obecně je programování je dobrým zvykem catch konkrétní typ výjimky, a nemuseli používat základní `catch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9bbe8-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="9bbe8-104">Když dojde k výjimce, jsou předány do zásobníku a každý blok catch dostane příležitost, aby to zvládnul.</span><span class="sxs-lookup"><span data-stu-id="9bbe8-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="9bbe8-105">Je důležité pořadí příkazů catch.</span><span class="sxs-lookup"><span data-stu-id="9bbe8-105">The order of catch statements is important.</span></span> <span data-ttu-id="9bbe8-106">Umístit bloky catch cílené na specifické výjimky než blok catch výjimky nebo kompilátor zahlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="9bbe8-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="9bbe8-107">Určuje blok catch správné odpovídající typ výjimky k názvu na výjimku zadanou v bloku catch.</span><span class="sxs-lookup"><span data-stu-id="9bbe8-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="9bbe8-108">Pokud neexistuje žádný konkrétní blok catch, výjimku zachycuje se prostřednictvím obecný zachytávací blok, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="9bbe8-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="9bbe8-109">Následující příklad kódu používá `try` / `catch` bloku catch <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="9bbe8-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="9bbe8-110">Ukázka vytvoří třídu s názvem `Employee` s jedinou vlastností, úroveň zaměstnance (`Emlevel`).</span><span class="sxs-lookup"><span data-stu-id="9bbe8-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="9bbe8-111">Je metoda `PromoteEmployee`, přebírá objekt a zvýší úroveň zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="9bbe8-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="9bbe8-112"><xref:System.InvalidCastException> Dojde k při <xref:System.DateTime> instance předána `PromoteEmployee` metody.</span><span class="sxs-lookup"><span data-stu-id="9bbe8-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a><span data-ttu-id="9bbe8-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9bbe8-113">See also</span></span>

- [<span data-ttu-id="9bbe8-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="9bbe8-114">Exceptions</span></span>](index.md)
