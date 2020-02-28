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
ms.openlocfilehash: 48b450e579263876725f96e0adfc4c16aac1d869
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160154"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="b6097-102">Používání specifických výjimek v bloku catch</span><span class="sxs-lookup"><span data-stu-id="b6097-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="b6097-103">Obecně je dobrým programovacím postupem zachytit konkrétní typ výjimky namísto použití základního příkazu `catch`.</span><span class="sxs-lookup"><span data-stu-id="b6097-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="b6097-104">Pokud dojde k výjimce, je předán zásobníku a každý blok catch je dána příležitostí k jejímu zpracování.</span><span class="sxs-lookup"><span data-stu-id="b6097-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="b6097-105">Pořadí příkazů catch je důležité.</span><span class="sxs-lookup"><span data-stu-id="b6097-105">The order of catch statements is important.</span></span> <span data-ttu-id="b6097-106">Umístěte bloky catch cílené na konkrétní výjimky před obecným blokem catch výjimky nebo kompilátor může vystavit chybu.</span><span class="sxs-lookup"><span data-stu-id="b6097-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="b6097-107">Správný blok catch je určen porovnáním typu výjimky s názvem výjimky zadané v bloku catch.</span><span class="sxs-lookup"><span data-stu-id="b6097-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="b6097-108">Pokud není k dispozici žádný konkrétní blok catch, je výjimka zachycena obecným blokem catch, pokud nějaká existuje.</span><span class="sxs-lookup"><span data-stu-id="b6097-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="b6097-109">Následující příklad kódu používá `try`/`catch` blok k zachycení <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="b6097-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="b6097-110">Ukázka vytvoří třídu s názvem `Employee` s jedinou vlastností, úrovní zaměstnance (`Emlevel`).</span><span class="sxs-lookup"><span data-stu-id="b6097-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="b6097-111">Metoda, `PromoteEmployee`, přebírá objekt a zvyšuje úroveň zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="b6097-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="b6097-112">K <xref:System.InvalidCastException> dojde, když je instance <xref:System.DateTime> předána metodě `PromoteEmployee`.</span><span class="sxs-lookup"><span data-stu-id="b6097-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="b6097-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6097-113">See also</span></span>

- [<span data-ttu-id="b6097-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="b6097-114">Exceptions</span></span>](index.md)
