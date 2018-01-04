---
title: "Postupy: Naslouchání více požadavkům zrušení"
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
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 397de114a3d8c3cbcfbc8ab55e4dbaf45ca9b652
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="df154-102">Postupy: Naslouchání více požadavkům zrušení</span><span class="sxs-lookup"><span data-stu-id="df154-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="df154-103">Tento příklad ukazuje, jak pro naslouchání na dva zrušení tokenů současně tak, aby operace můžete zrušit, pokud se požaduje buď token.</span><span class="sxs-lookup"><span data-stu-id="df154-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df154-104">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="df154-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="df154-105">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="df154-105">This error is benign.</span></span> <span data-ttu-id="df154-106">Můžete stisknutím klávesy F5 lze pokračovat a jejich chování zpracování výjimek, která je znázorněna v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="df154-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="df154-107">Abyste zabránili zastavení při první chybě Visual Studio, stačí zrušit zaškrtnutí políčka "Pouze můj kód" v části **nástroje, možnosti, ladění, Obecné**.</span><span class="sxs-lookup"><span data-stu-id="df154-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df154-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="df154-108">Example</span></span>  
 <span data-ttu-id="df154-109">V následujícím příkladu <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> metoda se používá pro připojení dvě tokeny do jednoho tokenu.</span><span class="sxs-lookup"><span data-stu-id="df154-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="df154-110">To umožňuje token, který má být předán metod, které přijímají pouze jeden zrušení tokenu jako argument.</span><span class="sxs-lookup"><span data-stu-id="df154-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="df154-111">Příklad ukazuje, běžný scénář, ve kterém musí odpovídat metodu obou token předané z mimo třídu a token vygenerovaný v třídě.</span><span class="sxs-lookup"><span data-stu-id="df154-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="df154-112">Když vyvolá propojené token <xref:System.OperationCanceledException>, token, který je předán výjimka je propojené token, není buď předchůdce tokenů.</span><span class="sxs-lookup"><span data-stu-id="df154-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="df154-113">Pokud chcete zjistit, které tokenů byla zrušena, zkontrolujte stav tokenů předchůdce přímo.</span><span class="sxs-lookup"><span data-stu-id="df154-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="df154-114">V tomto příkladu <xref:System.AggregateException> by měl být nikdy vyvolána, ale je zachycena jako zde protože ve scénářích reálného světa jakékoli výjimky kromě <xref:System.OperationCanceledException> , jsou vyvolány z delegáta úlohy jsou uzavřen do <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="df154-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df154-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="df154-115">See Also</span></span>  
 [<span data-ttu-id="df154-116">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="df154-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
