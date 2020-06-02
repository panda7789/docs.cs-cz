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
ms.openlocfilehash: 3f92d1d9e8fec91475886e8bd7bffbc97bb632a0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279392"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="f655c-102">Postupy: Naslouchání více požadavkům zrušení</span><span class="sxs-lookup"><span data-stu-id="f655c-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="f655c-103">Tento příklad ukazuje, jak naslouchat dvěma tokeny zrušení současně, abyste mohli zrušit operaci, pokud ji buď vyžádá.</span><span class="sxs-lookup"><span data-stu-id="f655c-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f655c-104">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="f655c-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="f655c-105">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="f655c-105">This error is benign.</span></span> <span data-ttu-id="f655c-106">Stiskem klávesy F5 můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v níže uvedených příkladech.</span><span class="sxs-lookup"><span data-stu-id="f655c-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="f655c-107">Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.</span><span class="sxs-lookup"><span data-stu-id="f655c-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f655c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f655c-108">Example</span></span>  
 <span data-ttu-id="f655c-109">V následujícím příkladu se <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> Metoda používá pro spojení dvou tokenů do jednoho tokenu.</span><span class="sxs-lookup"><span data-stu-id="f655c-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="f655c-110">To umožňuje předat token do metod, které jako argument přebírají pouze jeden token zrušení.</span><span class="sxs-lookup"><span data-stu-id="f655c-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="f655c-111">Příklad ukazuje běžný scénář, ve kterém metoda musí sledovat token předaný z vnějšku třídy a token vygenerovaný uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="f655c-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="f655c-112">Když propojený token vyvolá výjimku <xref:System.OperationCanceledException> , token, který je předán do výjimky, je propojený token, nikoli buď tokeny předchůdce.</span><span class="sxs-lookup"><span data-stu-id="f655c-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="f655c-113">Chcete-li zjistit, které z tokenů byly zrušeny, zkontrolujte stav tokenů předchůdce přímo.</span><span class="sxs-lookup"><span data-stu-id="f655c-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="f655c-114">V tomto příkladu <xref:System.AggregateException> by neměl být nikdy vyvolána, ale je zde zachycena z toho důvodu, že v reálných scénářích jakékoli jiné výjimky kromě těch <xref:System.OperationCanceledException> , které jsou vyvolány z delegáta úkolu, jsou zabaleny do <xref:System.AggregateException> .</span><span class="sxs-lookup"><span data-stu-id="f655c-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f655c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f655c-115">See also</span></span>

- [<span data-ttu-id="f655c-116">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="f655c-116">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
