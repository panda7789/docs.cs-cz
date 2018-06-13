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
ms.openlocfilehash: 93303ba84538a85350fd09b78f9963558668b91b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582106"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="b16ee-102">Postupy: Povolení režimu sledování vláken ve struktuře SpinLock</span><span class="sxs-lookup"><span data-stu-id="b16ee-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="b16ee-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> je uzamčen nízké úrovně vzájemné vyloučení, který můžete použít pro scénáře, které mají velmi krátké čekací doby.</span><span class="sxs-lookup"><span data-stu-id="b16ee-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="b16ee-104"><xref:System.Threading.SpinLock> není vícenásobně.</span><span class="sxs-lookup"><span data-stu-id="b16ee-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="b16ee-105">Po vlákno zadá zámek, se musí zámek správně ukončit, než můžete znovu zadat.</span><span class="sxs-lookup"><span data-stu-id="b16ee-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="b16ee-106">Obvykle pokusy o znovu zadat zámek způsobí zablokování a blokování může být velmi obtížné ladění.</span><span class="sxs-lookup"><span data-stu-id="b16ee-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="b16ee-107">Jako pomůcku při vývoji <xref:System.Threading.SpinLock?displayProperty=nameWithType> podporuje režimu sledování vláken, které způsobí výjimku vyvolána, pokud se pokusí znovu zadat zámku, která již obsahuje vlákna.</span><span class="sxs-lookup"><span data-stu-id="b16ee-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="b16ee-108">To umožňuje více snadno najít bod, kdy nebyl správně opustil zámek.</span><span class="sxs-lookup"><span data-stu-id="b16ee-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="b16ee-109">Můžete zapnout na režimu sledování vláken pomocí <xref:System.Threading.SpinLock> konstruktor, který přebírá logickou hodnotu vstupní parametr a předávání argument `true`.</span><span class="sxs-lookup"><span data-stu-id="b16ee-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="b16ee-110">Po dokončení vývoj a testování fáze, vypněte režimu sledování vláken pro dosažení vyššího výkonu.</span><span class="sxs-lookup"><span data-stu-id="b16ee-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b16ee-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="b16ee-111">Example</span></span>  
 <span data-ttu-id="b16ee-112">Následující příklad ukazuje režimu sledování vláken.</span><span class="sxs-lookup"><span data-stu-id="b16ee-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="b16ee-113">Řádky, které správně ukončit zámek jsou vloženy do komentáře k simulaci kódování chyba, která způsobí, že jeden z následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="b16ee-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
-   <span data-ttu-id="b16ee-114">Pokud je vyvolána výjimka <xref:System.Threading.SpinLock> byla vytvořena pomocí argument `true` (`True` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b16ee-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
-   <span data-ttu-id="b16ee-115">Zablokování, pokud <xref:System.Threading.SpinLock> byla vytvořena pomocí argument `false` (`False` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b16ee-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="b16ee-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b16ee-116">See Also</span></span>  
 [<span data-ttu-id="b16ee-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="b16ee-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
