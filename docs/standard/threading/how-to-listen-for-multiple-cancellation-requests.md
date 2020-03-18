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
ms.openlocfilehash: e35472040b6ee1263ebc4c4968fa1822045a2064
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138014"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="6b851-102">Postupy: Naslouchání více požadavkům zrušení</span><span class="sxs-lookup"><span data-stu-id="6b851-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="6b851-103">Tento příklad ukazuje, jak poslouchat dva tokeny zrušení současně, takže můžete zrušit operaci, pokud jeden token požaduje.</span><span class="sxs-lookup"><span data-stu-id="6b851-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b851-104">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="6b851-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="6b851-105">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="6b851-105">This error is benign.</span></span> <span data-ttu-id="6b851-106">Můžete stisknout Klávesu F5 pokračovat z něj a zobrazit chování zpracování výjimek, která je znázorněna v příkladech níže.</span><span class="sxs-lookup"><span data-stu-id="6b851-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="6b851-107">Chcete-li zabránit visual studio z rozdělení na první chybu, stačí zrušit zaškrtnutí políčka "Jen můj kód" zaškrtněte políčko "Jen můj kód" v části **Nástroje, možnosti, ladění, obecné**.</span><span class="sxs-lookup"><span data-stu-id="6b851-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b851-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b851-108">Example</span></span>  
 <span data-ttu-id="6b851-109">V následujícím příkladu <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> metoda se používá k připojení dvou tokenů do jednoho tokenu.</span><span class="sxs-lookup"><span data-stu-id="6b851-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="6b851-110">To umožňuje token, který má být předán metodám, které berou pouze jeden token zrušení jako argument.</span><span class="sxs-lookup"><span data-stu-id="6b851-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="6b851-111">Příklad ukazuje běžný scénář, ve kterém musí metoda sledovat token předaný mimo třídu a token generovaný uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="6b851-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="6b851-112">Když propojený token vyvolá <xref:System.OperationCanceledException>, token, který je předán do výjimky je propojený token, nikoli jeden z tokenů předchůdce.</span><span class="sxs-lookup"><span data-stu-id="6b851-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="6b851-113">Chcete-li zjistit, který z tokenů byl zrušen, zkontrolujte stav tokenů předchůdce přímo.</span><span class="sxs-lookup"><span data-stu-id="6b851-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="6b851-114">V tomto <xref:System.AggregateException> příkladu by nikdy být vyvolána, ale je zachycen zde, <xref:System.OperationCanceledException> protože v reálném scénářích všechny jiné <xref:System.AggregateException>výjimky kromě toho, které jsou vyvolány z delegáta úkolu jsou zabaleny do .</span><span class="sxs-lookup"><span data-stu-id="6b851-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b851-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b851-115">See also</span></span>

- [<span data-ttu-id="6b851-116">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="6b851-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
