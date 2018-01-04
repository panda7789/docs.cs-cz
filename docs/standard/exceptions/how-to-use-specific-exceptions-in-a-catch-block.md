---
title: "Postupy: Používání specifických výjimek v bloku Catch"
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
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ebc59035140ff0464cd959129fdf48a4e9a269f5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="2d447-102">Postup používání specifických výjimek v bloku catch</span><span class="sxs-lookup"><span data-stu-id="2d447-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="2d447-103">Obecně platí, je dobrým zvykem zachytit specifický typ výjimky, místo použití základní programování `catch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="2d447-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="2d447-104">Když dojde k výjimce, je předán do zásobníku a každý blok catch je zadána možnost se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="2d447-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="2d447-105">Je důležité pořadí příkazů catch.</span><span class="sxs-lookup"><span data-stu-id="2d447-105">The order of catch statements is important.</span></span> <span data-ttu-id="2d447-106">Umístit bloky catch cílená na konkrétní výjimky před obecné výjimce bloku catch nebo kompilátor může vydat k chybě.</span><span class="sxs-lookup"><span data-stu-id="2d447-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="2d447-107">Správný blok catch je určen podle odpovídající typ výjimky k názvu zadaná v bloku catch výjimky.</span><span class="sxs-lookup"><span data-stu-id="2d447-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="2d447-108">Pokud není žádný konkrétní blok catch, je výjimka zachycena pomocí bloku catch Obecné, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="2d447-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="2d447-109">Následující příklad kódu používá `try` / `catch` bloku k zachycení <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="2d447-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="2d447-110">Ukázka vytvoří třídu s názvem `Employee` s jedinou vlastností, úroveň zaměstnance (`Emlevel`).</span><span class="sxs-lookup"><span data-stu-id="2d447-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="2d447-111">A metoda `PromoteEmployee`, přebírá objekt a zvýší úroveň zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="2d447-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="2d447-112"><xref:System.InvalidCastException> Dojde při <xref:System.DateTime> instance předána `PromoteEmployee` metoda.</span><span class="sxs-lookup"><span data-stu-id="2d447-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a><span data-ttu-id="2d447-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d447-113">See Also</span></span>  
[<span data-ttu-id="2d447-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="2d447-114">Exceptions</span></span>](index.md)
