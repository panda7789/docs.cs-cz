---
title: 'Postupy: Naslouchání více požadavkům zrušení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17874b8b9733ea18d4877e2c79810fcd6247db0b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680228"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="5ed34-102">Postupy: Naslouchání více požadavkům zrušení</span><span class="sxs-lookup"><span data-stu-id="5ed34-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="5ed34-103">Tento příklad ukazuje, jak tak, aby naslouchala na dvou tokeny zrušení současně tak, aby operace můžete zrušit, pokud buď token požadavku.</span><span class="sxs-lookup"><span data-stu-id="5ed34-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ed34-104">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="5ed34-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="5ed34-105">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="5ed34-105">This error is benign.</span></span> <span data-ttu-id="5ed34-106">Můžete stisknutím klávesy F5 pokračovat z něj a najdete v chování zpracování výjimek, což je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="5ed34-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="5ed34-107">Pokud chcete zabránit přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí políčka "Jen můj kód" v části **nástroje, možnosti, ladění, Obecné**.</span><span class="sxs-lookup"><span data-stu-id="5ed34-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ed34-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ed34-108">Example</span></span>  
 <span data-ttu-id="5ed34-109">V následujícím příkladu <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> metoda se používá pro připojení dvou tokeny do jednoho tokenu.</span><span class="sxs-lookup"><span data-stu-id="5ed34-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="5ed34-110">To umožňuje token, který má předané do metod, které přijímají token jako argument pouze jeden zrušení.</span><span class="sxs-lookup"><span data-stu-id="5ed34-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="5ed34-111">Tento příklad ukazuje běžný scénář, ve kterém metoda zachovávají i token předat z mimo třídu a token generuje uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="5ed34-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="5ed34-112">Pokud vyvolá propojené token <xref:System.OperationCanceledException>, token, který je předán výjimka je propojené token, není buď tokenů předchůdce.</span><span class="sxs-lookup"><span data-stu-id="5ed34-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="5ed34-113">Pokud chcete zjistit, které tokenů byla zrušena, zkontrolujte stav předchůdce tokenů přímo.</span><span class="sxs-lookup"><span data-stu-id="5ed34-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="5ed34-114">V tomto příkladu <xref:System.AggregateException> by nikdy být vyvolána, ale to je zachycena zde protože ve skutečných scénářích všechny výjimky kromě <xref:System.OperationCanceledException> , které jsou vyvolány z delegátu úlohy jsou zabaleny v <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="5ed34-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed34-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ed34-115">See also</span></span>

- [<span data-ttu-id="5ed34-116">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="5ed34-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
