---
title: 'Postupy: Povolení režimu sledování vláken ve struktuře SpinLock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 111ab87ca419217f425eb5d4bc9b52f5f30f0237
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644846"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="5b02f-102">Postupy: Povolení režimu sledování vláken ve struktuře SpinLock</span><span class="sxs-lookup"><span data-stu-id="5b02f-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="5b02f-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> je nízké úrovně vzájemné vyloučení zámek, který můžete použít pro scénáře, které mají velmi krátké čekací dobu.</span><span class="sxs-lookup"><span data-stu-id="5b02f-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="5b02f-104"><xref:System.Threading.SpinLock> není vícenásobně.</span><span class="sxs-lookup"><span data-stu-id="5b02f-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="5b02f-105">Poté, co vlákno zadá zámek, ho ukončíte zámek správně předtím, než můžete znovu zadat.</span><span class="sxs-lookup"><span data-stu-id="5b02f-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="5b02f-106">Obvykle jakékoli pokusy o potvrzení zámek by způsobila zablokování a zablokování může být velmi obtížné ladit.</span><span class="sxs-lookup"><span data-stu-id="5b02f-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="5b02f-107">Jako vodítko k vývoji <xref:System.Threading.SpinLock?displayProperty=nameWithType> podporuje režimu sledování vláken, která způsobí výjimku, která je vyvolána, když vlákno se pokusí znovu zadejte zámek, který již obsahuje.</span><span class="sxs-lookup"><span data-stu-id="5b02f-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="5b02f-108">To umožňuje více snadno najít bod, ve kterém zámek nebyl ukončen správně.</span><span class="sxs-lookup"><span data-stu-id="5b02f-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="5b02f-109">Můžete zapnout režimu sledování vláken pomocí <xref:System.Threading.SpinLock> konstruktor, který přebírá logickou hodnotu vstupní parametr a předávání argument `true`.</span><span class="sxs-lookup"><span data-stu-id="5b02f-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="5b02f-110">Po dokončení vývojové a testovací fázi se vypněte režimu sledování vláken pro zajištění lepšího výkonu.</span><span class="sxs-lookup"><span data-stu-id="5b02f-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b02f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b02f-111">Example</span></span>  
 <span data-ttu-id="5b02f-112">Následující příklad ukazuje režimu sledování vláken.</span><span class="sxs-lookup"><span data-stu-id="5b02f-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="5b02f-113">Řádky, které správně ukončení uzamčení jsou označené jako komentář pro simulaci chyby kódu, který způsobí, že jeden z následujících výsledků:</span><span class="sxs-lookup"><span data-stu-id="5b02f-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
- <span data-ttu-id="5b02f-114">Pokud je vyvolána výjimka <xref:System.Threading.SpinLock> bylo vytvořeno s použitím argument `true` (`True` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5b02f-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
- <span data-ttu-id="5b02f-115">Vzájemné zablokování, pokud <xref:System.Threading.SpinLock> bylo vytvořeno s použitím argument `false` (`False` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5b02f-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="5b02f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b02f-116">See also</span></span>

- [<span data-ttu-id="5b02f-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="5b02f-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
