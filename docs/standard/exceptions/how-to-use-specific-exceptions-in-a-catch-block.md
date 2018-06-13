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
ms.openlocfilehash: 424db46c879974a9859637f9a2a5dfcd4494a3c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571795"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="5c389-102">Postup používání specifických výjimek v bloku catch</span><span class="sxs-lookup"><span data-stu-id="5c389-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="5c389-103">Obecně platí, je dobrým zvykem zachytit specifický typ výjimky, místo použití základní programování `catch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5c389-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="5c389-104">Když dojde k výjimce, je předán do zásobníku a každý blok catch je zadána možnost se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="5c389-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="5c389-105">Je důležité pořadí příkazů catch.</span><span class="sxs-lookup"><span data-stu-id="5c389-105">The order of catch statements is important.</span></span> <span data-ttu-id="5c389-106">Umístit bloky catch cílená na konkrétní výjimky před obecné výjimce bloku catch nebo kompilátor může vydat k chybě.</span><span class="sxs-lookup"><span data-stu-id="5c389-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="5c389-107">Správný blok catch je určen podle odpovídající typ výjimky k názvu zadaná v bloku catch výjimky.</span><span class="sxs-lookup"><span data-stu-id="5c389-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="5c389-108">Pokud není žádný konkrétní blok catch, je výjimka zachycena pomocí bloku catch Obecné, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="5c389-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="5c389-109">Následující příklad kódu používá `try` / `catch` bloku k zachycení <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="5c389-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="5c389-110">Ukázka vytvoří třídu s názvem `Employee` s jedinou vlastností, úroveň zaměstnance (`Emlevel`).</span><span class="sxs-lookup"><span data-stu-id="5c389-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="5c389-111">A metoda `PromoteEmployee`, přebírá objekt a zvýší úroveň zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="5c389-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="5c389-112"><xref:System.InvalidCastException> Dojde při <xref:System.DateTime> instance předána `PromoteEmployee` metoda.</span><span class="sxs-lookup"><span data-stu-id="5c389-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a><span data-ttu-id="5c389-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c389-113">See Also</span></span>  
[<span data-ttu-id="5c389-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="5c389-114">Exceptions</span></span>](index.md)
